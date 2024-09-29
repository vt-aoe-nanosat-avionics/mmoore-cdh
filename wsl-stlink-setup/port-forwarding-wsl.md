Once your computer recognizes the ST-Link as a usb device, now you need to give WSL access to use the device.

To do this, follow the instructions on this page: https://learn.microsoft.com/en-us/windows/wsl/connect-usb 

It is worth noting, if you close WSL you will need to re-attach the shared ST-Link to the new WSL window.
Each time you open WSL, run Powershell as an admin and type "usbipd attach --wsl --busid <busid>", where <busid> is the ID of the ST-Link.
You find the bus ID by running "usbipd list" in Powershell.
