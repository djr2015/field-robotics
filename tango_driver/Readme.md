**Establishing WiFi and USB communication between the Tango and the PC**

For the ROS node initialized on the Tango to communicate with the ROS master node based on the PC, full bi-directional connectivity must be ensured between the two devices. Here we explain how to enable bi-directional connectivity by Wifi and USB.

**USB**

1. Turn on the Tango and connect the Tango to the PC via USB.
2. On the Tango, navigate to **Settings** > **More** > **Tethering and portable hotspot** and turn **USB tethering** on.
3. On a Linux command prompt, type `adb devices`. If

    ```
    ????????????	no permissions
    ```
    
    appears, enter the following commands:
    
    ```
    sudo adb kill-server
    sudo adb start-server
    ```
    
    The device should now be recognized by Ubuntu.

4. On a Linux command prompt, type `ip link`. Check that a device name (which we will refer to from now on as `[device name]`: it might be `usb0`) corresponding to the Tango is present among the listed devices.
5. Type `dhcpcd [device name]`. This should connect the Tango to the PC's network. It will be assigned a new IP address which will appear on the terminal after a second or two. When running the app, enter this IP address in the `RobotURI` field that displays when the app starts.

As the micro USB port on the Tango is slightly unstable, the Tango may disconnect from the PC's network from time to time. If this happens, type `dhcpcd -k [device name]` to kill the connection and then `dhcpcd [device name]` to reset it.

**WiFi**

1. Connect the PC and the Tango to the same WiFi network.
2. On a Linux command prompt, type `ifconfig`. Under `wlan` you should see a field named `inet addr` which indicates the PC's internal IP address. When running the app, enter this IP address in the `RobotURI` field that displays when the app starts.

