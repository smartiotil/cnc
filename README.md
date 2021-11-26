# Defernder for 365

Project Scope	2
Windows Defender ATP Architecture	3
Windows Defender ATP Architecture (Disconnected Devices)	5
Project Phases	6
Phase 1 – Planning	6
Phase 2 – Deployment & Validation	6
Phase 3 – Windows Defender (AV+EDR) Customization	6
Phase 4 – Pilot	6
Phase 5 – Cloud app security integration	6
Licensing requirements	8
Client devices requirements	8
Onboarding Disconnected Device	9
Management server:	9
Download sources	9
Disconnected Devices	9
Proxy URLs and Port (Disconnected Devices)	10
Proxy URLs and Port (Online Devices)	10
Verify client connectivity to Windows Defender ATP service URLs	11
Onboarding using Configmgr	11
Company policy regarding commercial terms of deals made in Israel	14
General conditions for SOW	14





Project Scope 
The company need to deploy the windows defender ATP to ensure maximum protection for windows 10, MACOS and Linux servers, the goal of the project is protecting the business from advanced threats and zero day
In the process we will also integrate WDATP with MCAS, to extends Cloud Discovery capabilities beyond your corporate network, and enables machine-based investigation. Microsoft Defender ATP is a security platform for intelligent protection, detection, investigation, and response. Microsoft Defender ATP protects endpoints from cyber threats, detects advanced attacks and data breaches, automates security incidents, and improves security posture 

U-BTech integration team will setup the environment for Windows MAC and Linux deployments, and setup all the needed features and rules
the onboarding process of each Platform (Linux MAC and windows, windows servers) up to 5 devices only, will be leaded by U-BTech side.
Currently in the organization there is no system that can do the following actions: 
1.	Detects fast-changing malware variations using behavior monitoring and cloud-powered protection.
2.	Provides the most decisive malware defense and helps to ensure that only trusted apps can start on your devices.
3.	Checking integrity of the devices firmware, OS, and system defenses
4.	Automatic isolation hunter rule on contained machine
5.	Knowledge transfer with the team that will be responsible on Defender ATP







Windows Defender ATP Architecture
Windows Defender ATP consists of three main components: Windows Defender ATP endpoint sensors, the Windows Defender ATP cloud services backend, and the Windows Defender ATP console in the Windows Defender Security Center.
 



Windows Defender ATP Architecture (Disconnected Devices)

 





Project Phases 
The project is divided into several stages of planning and mapping, integration, testing and training system. 


Phase 1 – Planning
In the first phase, we plan and map the current environment and discuss about Windows defender ATP combability: 
•	Map users and client side 
•	Edit High Level Documents (design)  

Phase 2 – Deployment & Validation 
•	Prepare prerequisites (Firewall access and other system, credentials etc.) 
•	Prepare requirements for endpoint onboarding (Services like telemetry)
•	Deploy & Configure endpoint onboarding 
•	Remove existing Anti-virus (Optional).

Phase 3 – Windows Defender (AV+EDR) Customization 
•	Alerts
•	Files – Block\Allow lists
•	Excludes Process
•	Excludes URL

Phase 4 – Pilot
The fourth stage will focus on checking the configuration, deploy client and check the Windows defender ATP environment. 
•	Create profile for onboarding option for SCCM\Intune
•	Enable attack surface reduction rules (ASR- help prevent actions that malware often abuses to compromise devices and networks), with Intune (optional)
•	Check onboarding
•	Deployment for relative supported platform groups

Phase 5 – Cloud app security integration 
•	Connect WDATP to MCAS
•	Preview product integration benefits 

Notes
Attack surface reduction rules (ASR rules) help prevent actions that malware often abuses to compromise devices and networks. You can set ASR rules for devices running any of the following editions and versions of Windows:
Windows 10 Pro, version 1709 or later
Windows 10 Enterprise, version 1709 or later
Windows Server, version 1803 (Semi-Annual Channel) or later
Windows Server 2019
Each ASR rule contains one of three settings:
Not configured: Disable the ASR rule
Block: Enable the ASR rule
Audit: Evaluate how the ASR rule would impact your organization if enabled

























Requirements

Licensing requirements
Windows Defender Advanced Threat Protection requires one of the following Microsoft Volume Licensing offers:
•	Windows 10 Enterprise E5
•	Windows 10 Education E5
•	Microsoft 365 E5 (M365 E5) which includes Windows 10 Enterprise E5.
Client devices requirements
•	Windows 7 SP1 Enterprise
•	Windows 7 SP1 Pro
•	Windows 10 Enterprise, version 1607 or later (Fully Automated Deployment with Intune)
•	macOS
•	Telemetry and diagnostics service set on auto and running
Supported Linux server distributions and versions:
•	Red Hat Enterprise Linux 7.2 or higher
•	CentOS 7.2 or higher
•	Ubuntu 16.04 LTS or higher LTS
•	Debian 9 or higher
•	SUSE Linux Enterprise Server 12 or higher
•	Oracle Linux 7.2 or higher


For full list of supported OS, click the following link:
https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements#browser-requirements

Onboarding Disconnected Device
Management server:
Computers designated to run the Log Analytics gateway(OMS Gateway) must have the following configuration:
•	Windows 10, Windows 8.1, or Windows 7
•	Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, or Windows Server 2008
•	Microsoft .NET Framework 4.5
•	At least a 4-core processor and 8 GB of memory
•	A Log Analytics agent for Windows that is configured to report to the same workspace as the agents that communicate through the gateway

Download sources
•	OMS Gateway (Management servers Only)
https://go.microsoft.com/fwlink/?linkid=837444

•	Microsoft Monitoring Agent 64 bit(Management server, Windows 7, servers 2008-2016)
https://go.microsoft.com/fwlink/?LinkId=828603

Disconnected Devices
Windows Server 2016 and earlier or Windows 8.1 and earlier
*Windows 10 and server 2019 not supported by oms gateway
Proxy URLs and Port (Disconnected Devices)
Note
If a proxy or firewall is blocking all traffic by default and allowing only specific domains through or HTTPS scanning (SSL inspection) is enabled, make sure that the following URLs are white-listed to permit communication with Windows Defender ATP service in port 80 and 
443
Note
If a proxy or firewall is blocking anonymous traffic, as Windows Defender ATP sensor is connecting   from system context, make sure anonymous traffic is permitted in the above listed URLs

Source	Destination	Port/URLs	Info
Disconnected devices	Management server	8080	oms gateway 
Management sever	Azure Log analytics 	*.agentsvc.azureautomation.net
*.blob.core.windows.net
*.ods.opinsights.azure.com
*.oms.opinsights.azure.com	
Microsoft Monitoring Agent	Azure Log analytics	*.agentsvc.azureautomation.net
*.blob.core.windows.net
*.ods.opinsights.azure.com
*.oms.opinsights.azure.com	Used for management server & server 2008 – 2016, windows 7
			

Notes
connectivity issue can be check by running the TestCloudConnectivity tool. The tool is installed by default with the agent in the folder %SystemRoot%\Program Files\Microsoft Monitoring Agent\Agent
Proxy URLs and Port (Online Devices)
 
•	For full network requirements click the following link:
https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-antivirus/configure-network-connections-windows-defender-antivirus#allow-connections-to-the-windows-defender-antivirus-cloud-service

Verify client connectivity to Windows Defender ATP service URLs
Download the connectivity verification tool to the PC where Windows Defender ATP sensor is running on.
https://winatpmanagement.windows.com/client/management/static/WDATPConnectivityAnalyzer.zip
If at least one of the connectivity options returns a (200) status, then the Windows Defender ATP client can communicate with the tested URL properly using this connectivity method. 

Onboarding using Configmgr
ConfigMgr Configuration (Version 1610)
•	Enable Windows Defender ATP feature in ConfigMgr
•	Download package from the Windows Defender ATP portal
•	Extract the contents of the .zip file to a shared, read-only location
•	Create Collection for devices running version 1607
select SMS_R_SYSTEM.ResourceID,SMS_R_SYSTEM.ResourceType,SMS_R_SYSTEM.Name,SMS_R_SYSTEM.SMSUniqueIdentifier,SMS_R_SYSTEM.ResourceDomainORWorkgroup,SMS_R_SYSTEM.Client from SMS_R_System inner join SMS_G_System_OPERATING_SYSTEM on SMS_G_System_OPERATING_SYSTEM.ResourceID = SMS_R_System.ResourceId where SMS_G_System_OPERATING_SYSTEM.BuildNumber >= "14393" and SMS_G_System_OPERATING_SYSTEM.Caption like "Microsoft Windows 10%"

 
Microsoft Defender ATP for non-Windows platforms
Microsoft Defender ATP for Mac
Microsoft Defender ATP for Mac offers AV and EDR capabilities for the three latest released versions of macOS. Customers can deploy and manage the solution through Microsoft Endpoint Manager and Jamf. Just like with Microsoft Office applications on macOS, Microsoft Auto Update is used to manage Microsoft Defender ATP for Mac updates. For information about the key features and benefits, read our announcements.
For more details on how to get started, visit the Microsoft Defender ATP for Mac documentation.
Microsoft Defender ATP for Linux
Microsoft Defender ATP for Linux offers preventative (AV) capabilities for Linux servers. This includes a full command line experience to configure and manage the agent, initiate scans, and manage threats. We support recent versions of the six most common Linux Server distributions: RHEL 7.2+, CentOS Linux 7.2+, Ubuntu 16 LTS, or higher LTS, SLES 12+, Debian 9+, and Oracle Linux 7.2. Microsoft Defender ATP for Linux can be deployed and configured using Puppet, Ansible, or using your existing Linux configuration management tool. For information about the key features and benefits, read our announcements.
For more details on how to get started, visit the Microsoft Defender ATP for Linux documentation.

Microsoft Defender ATP for Android
Microsoft Defender ATP for Android is our mobile threat defense solution for devices running Android 6.0 and higher. Both Android Enterprise (Work Profile) and Device Administrator modes are supported. On Android, we offer web protection, which includes anti-phishing, blocking of unsafe connections, and setting of custom indicators. The solution scans for malware and potentially unwanted applications (PUA) and offers additional breach prevention capabilities through integration with Microsoft Endpoint Manager and Conditional Access. For information about the key features and benefits, read our announcements.
For more details on how to get started, visit the Microsoft Defender ATP for Android documentation.




 
Notes and comments 
•	The project will make with an emphasis on knowledge transfer to the customer need to know the environment 
•	Establishment of the rule of servers including prerequisites for the system will be made by the customer 
•	Requirements will be made by the customer 
•	support after the completion of the project will be based on a service agreement 
•	POC will include windows OS, if Linux and macOS is required, additional time is needed
•	AV Removal in the POC is the costumer responsibility, U-BTech can assist the costumer based on hours bank 
•	Linux servers agents deployment is out of scope (costumers responsibility)
•	MCAS POC will run in deferent process 
•	Customer responsibility deploying WDATP to all devices after 5 devices (part of SOW)
•	Windows servers deployment of defender ATP is costumer responsibility
•	VDI Deployment of WDATP is costumer responsibility













Company policy regarding commercial terms of deals made in Israel 
 	Project cost: 
 	Total project costs: 15,000 USD
 	200 MCAS Licenses for 1 month included in project cost.
 	Every additional hour for escort or specialist services out of scope under this activity only -300 NIS
(billing according to actual utilization).
 	Payment terms: 
 	current + 30 days
 	VAT will be added to each invoice by law.
 	50% after kick-off meeting.
 	50% after POC summary meeting.
 	If a Microsoft funding is received during the mentioned period, the amount will be adjusted from customer invoice.
General conditions for SOW
The project's price is based on a Fix Price and on the experience of U-BTech (Part 1).
The project's price for professional services- Out of scope will base on an Hours Bank accoridng to conditions below (Part 2).
Customer will associate U-BTech as the Partner of Record in all the cloud systems purchased.

















Part #1- SOW for SCCM (Installation & Configuration):
Project will charge after Kickoff meeting.
•	This quote is based on the included information given to us by the customer. Any additional work needed not in the project plan will be performed at additional costs.
•	Any change or cancellation made by the client, must be notified at least two bussines days in advance. In case a notification was not made/was made too late, the client is obligated to pay for the planned consultation hours accroting to hourly rate of 350 NIS and conditions below:
	The minimum amount of billable consultation hours for a field call is 4 hours.
	The minimum amount of billable consultation hours for a phone call is 30 min.
	A half hour drive to and from the client will be calculated as of a cosultation hour.
•	The client is obligated to avoid any form of lobbying and\or attempts to hire any of  U-BTech employees, in whom he got in touch with during the project, directly or indirectly.  
•	The resposibilty for a legal licesing relies on the client. 
•	Our offer stands for 30 days.
Part #2- Hours bank for professional Services:
Every hour will be charged at a rate of 300 NIS per hour.
Pro services will charge according to actual utilization (monthly invoice).
•	Any change or cancellation made by the client, must be notified at least two bussines days in advance. In case a notification was not made/was made too late, the client is obligated to pay for the planned consultation hours accroting to hourly rate of 300 NIS and conditions below.
•	Hourly rate will calculate according to the conditions below:
	The minimum amount of billable consultation hours for a field call is 4 hours.
	The minimum amount of billable consultation hours for a phone call is 30 min.
	A half hour drive to and from the client will be calculated as of a cosultation hour.
	During week days, any activity/consultantation between 18:00 and 23:59 will be valued as 150% of the standard rate per hour. 
	Sunday to Thursday, any activity/consultantation between 00:00 and 08:00 will be valued as 200% of the standard rate per hour.
	On Fridays, any activity/consultantation between 08:00 and 17:00 will be valued as 150% of the standard rate per hour.
	On Fridays, any activity/consultantation between 17:00 and 08:00 will be valued as 200% of the standard rate per hour.
•	The resposibilty for a legal licesing relies on the client. 
•	Our offer stands for 30 days.




