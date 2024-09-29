When plugging the ST-Link V2 device to your Windows computer, it will not be immediately recognized. (If you check Device Manager, there will be a yellow 'warning' symbol next to the device)

To get your computer to recognize the ST-Link, you must manually install the device drivers from this link: https://www.st.com/en/development-tools/stsw-link009.html
You can also get to this link by Google'ing "stlink v2 drivers", it should be the first result.

After installing the drivers, you need to port forward WSL so that it can access the USB device.
