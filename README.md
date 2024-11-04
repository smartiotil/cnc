For Educational Purposes Only
Bypass AV AMSI.dll

Add-Type -TypeDefinition ([IO.File]::ReadAllText("$pwd\Source.cs")) -OutputAssembly "Source.dll"
[Reflection.Assembly]::Load([IO.File]::ReadAllBytes("$pwd\\Source.dll"))
[BP.AMS]::Disable()

Note: If your antivirus software blocks the Source.dll file, simply add a comment (e.g., //) in Source.cs to bypass antivirus signature detection.

Detecting PowerShell Processes with Sysmon and Wazuh
To monitor PowerShell processes using Sysmon:
Sysmon64.exe -accepteula -i sysconfig.xml

Detect PowerShell Empire Using Snort
Analyze a pcap file with Snort to detect PowerShell Empire activity:

snort -c /usr/local/etc/snort/snort.lua -r http_powershell_empire.pcap -Acmg -k none -q

This command processes packets with Snort.

Snort Rule for Detecting PowerShell Empire C&C Malware
Here’s a sample Snort rule to detect PowerShell Empire C&C connections:
snort

alert http (
    msg:"PowerShellEmpire detected";
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

Snort 3 HTTP Buffers
Snort 3 provides several HTTP inspection buffers, including:
http_inspect::http_client_body
http_inspect::http_cookie
http_inspect::http_header
http_inspect::http_method
http_inspect::http_param
http_inspect::http_raw_body
http_inspect::http_raw_cookie
http_inspect::http_raw_header
http_inspect::http_raw_request
http_inspect::http_stat_code
http_inspect::http_uri
http_inspect::js_data
http_inspect::vba_data


snort -c /usr/local/etc/snort/snort.lua -r ttp_powershell_empire.pcap -Acmg


For further reading, visit https://Livehack101.com.
