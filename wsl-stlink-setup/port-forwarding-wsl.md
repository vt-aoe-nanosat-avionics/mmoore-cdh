Once your computer recognizes the ST-Link as a usb device, now you need to give WSL access to use the device.

The instructions are from this page if you have any issues: https://learn.microsoft.com/en-us/windows/wsl/connect-usb 

To attach your ST-Link or any other usb device to WSL, you must first determine what USB Bus the device is using.
First, you must open Powershell in administrator mode (this is important for the second step).
In powershell, inputting the following command will list all attached USB devices and their bus-id:

```bash
usbipd list
```

The bus-id will be two numbers joined by a hyphen. For this example, 1-3 will be used as the bus-id.
Now we can switch the state of the USB bus to a "shared" state, this will allow us to attach the bus to WSL.
To share the bus, we use the bind command as follows:

```bash
usbipd bind --busid 1-3
```

This will change the state from "not shared" to "shared" in powershell, you can double-check this by inputting 'usbipd list' again.
Now all that is left is to give WSL access to the bus, which is done by attaching the USB bus to WSL via the following command:

```bash
usbipd attach --wsl --busid 1-3
```
It is worth noting that if you detach the USB device from your computer, you will need to re-attach the shared ST-Link to the new WSL window.
Each time you open WSL, run Powershell as an admin and retype the attach command as previously shown (you only need to bind the bus once, after it is bound it can be attached at any time).
