**Establishing WiFi and USB communication between the Tango and the PC**

**USB**

1. Turn on the Tango and connect the Tango to the PC via USB.
2. On the Tango, navigate to **Settings** > **More** > **Tethering and portable hotspot** and turn **USB tethering** on.
3. On a Linux command prompt, type `adb devices`. If (code corresponding to unrecognized device) appears, enter the following commands:
    sudo adb kill-server
    sudo adb start-server
The device should now be recognized by Ubuntu.
4. On a Linux command prompt, type `ip link`. Check that a device name (possibly `usb0`) corresponding to the Tango is present among the listed devices.
5. Type `dhcpcd [device name]`. This should connect the Tango to the PC's network. It will be assigned a new IP address which will appear on the terminal after a second or two. When running the app, enter this IP address in the `RobotURI` field that displays when the app starts.

**WiFi**

1. Connect the PC and the Tango to the same WiFi network.
2. On a Linux command prompt, type `ifconfig` (finish explaining how to extract the PC's internal IP address). When running the app, enter this IP address in the `RobotURI` field that displays when the app starts.

