# Smartcard Sniffer #

### REPOSITORY MOVED TO GITHUB ###
### https://github.com/ea/smartcard-sniffer ###

I wrote this as I was using APDUView ( http://www.fernandes.org/apduview/index.html )
utility quite a lot, but it's sometimes complicated to set up.
This tool uses AppInit\_Dlls functionality to achieve the same with more ease.

It hooks winscard!SCardTransmit and logs both sent and received data to a log file.
Log file is located in the same directory as the SmartcardSniffer dll, and has
a name of the application that is talking to the smart card.

To install the dll, just add it's path to:
  * for 32 bit DLL on 32 bit systems
> `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Windows\AppInit_DLLs]`
  * for 64 bit DLL on 64 bit system
> `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Windows\AppInit_DLLs]`
  * for 32 bit DLL on 64 bit system (for hooking 32 bit applications on 64 bit systems)
> `[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\Windows\AppInit_DLLs]`

> Multiple entries are separated by space and/or ",".
> Make sure you path to the DLL doesn't have any spaces in it.

> Note that on Windows Vista and later , you'd also need to set RequireSignedAppInit\_DLLs key to 0
> to be able to load unsigned DLLs and make sure LoadAppInit\_DLLs is set to 1.

> To uninstall it, simply remove the DLL entry from AppInit\_DLLs list.

> In the log file >>> specifies the data to be sent, and <<< received data.

> It's using MHook lib (http://codefromthe70s.org/mhook.aspx ) to do it's hooking business.

**- ea**