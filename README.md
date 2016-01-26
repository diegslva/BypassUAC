# BypassUAC
Defeating Windows User Account Control by abusing built-in Windows AutoElevate backdoor.

# System Requirements
1.x86-32/x64 Windows 7/8/8.1/10 (client, some methods however works on server version too).

2.Admin account with UAC set on default settings required.

# Usage
Run executable from command line: BypassUAC_x86 [Key] [Param] or BypassUAC_x64 [Key] [Param]. See "Run examples" below for more info.

First param is number of method to use, second is optional command (executable file name including full path) to run. Second param can be empty - in this case program will execute elevated cmd.exe from system32 folder.

Keys (watch debug ouput with dbgview or similar for more info):

1 - Leo Davidson sysprep method, this will work only on Windows 7 and Windows 8, used in multiple malware;

2 - Tweaked Leo Davidson sysprep method, this will work only on Windows 8.1.9600;

3 - Leo Davidson method tweaked by WinNT/Pitou developers, works from Windows 7 up to 10th2 10532;

4 - Application Compatibility Shim RedirectEXE method, from WinNT/Gootkit. Works from Windows 7 up to 8.1.9600;

5 - ISecurityEditor WinNT/Simda method, used to turn off UAC, works from Windows 7 up to Windows 10th1 100136;

6 - Wusa method used by Win32/Carberp, tweaked to work with Windows 8/8.1 also;

7 - Wusa method, tweaked to work from Windows 7 up to 10th1 10136;

8 - Slightly modified Leo Davidson method used by Win32/Tilon, works only on Windows 7;

9 - Hybrid method, combination of WinNT/Simda and Win32/Carberp + AVrf, works from Windows 7 up to 10th1 10136;

10 - Hybrid method, abusing appinfo.dll way of whitelisting autoelevated applications and KnownDlls cache changes, works from Windows 7 up to 10th2 10532;

11 - WinNT/Gootkit second method based on the memory patching from MS "Fix it" patch shim (and as side effect - arbitrary dll injection), works from Windows 7 up to 8.1.9600;

12 - Windows 10 sysprep method, abusing different dll dependency added in Windows 10 (works up to 10th2 10558);

13 - Hybrid method, abusing appinfo.dll way of whitelisting MMC console commands and EventViewer missing dependency, works from Windows 7 up to 10rs1 11082;

14 - WinNT/Sirefef method, abusing appinfo.dll way of whitelisting OOBE.exe, works from Windows 7 up to 10th2 10558;

15 - Win32/Addrop method, also used in Metasploit uacbypass module, works from Windows 7 up to 10rs1 11082;

16 - Hybrid method working together with Microsoft GWX backdoor, work from Windows 7 up to 10rs1 11082.


Note:

Several methods require process injection, so they won't work from wow64, use x64 edition of this tool;

Method (4) unavailable in 64 bit edition because of Shim restriction;

Method (6) unavailable in wow64 environment starting from Windows 8. Also target application unavailable in Windows 10;

Method (11) implemented in x86-32 version;

Method (13) implemented only in x64 version.


Run examples:

BypassUAC_x86.ex 1 cmd.exe

BypassUAC_x64.ex 3 cmd.exe

