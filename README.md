# all_screpy_tools_linux
Unlock the full potential of your smartphone by seamlessly integrating it with your Linux machine using the AllScrepy Tools for Linux Phone Connectivity Suite. This powerful toolkit enables you to harness your phone's camera, microphone, screen, and more, directly on your PC.


# Install scrcpy

To install the latest version of the open-source tool SCRCPY, use the following command:

```bash
sudo apt install scrcpy
```

For more information and the latest updates, you can visit the [SCRCPY GitHub repository](https://github.com/Genymobile/scrcpy).


# Installing Dependencies On the PC

1. Install Android tools (adb) on your PC:

    ```bash
    sudo apt install android-tools-adb
    ```

2. Verify connected devices:

    ```bash
    adb devices
    ```

Make sure your Android device is connected to your PC before running the above command.


# How to Run scrcpy Wirelessly

1. Connect the device to the same Wi-Fi as your computer.
2. Get your device IP address (in Settings → About phone → Status).
3. Enable adb over TCP/IP on your device: `adb tcpip 5555`.
4. Connect to your device: `adb connect DEVICE_IP:5555` (replace `DEVICE_IP` with your device's IP address).
5. Unplug your device.
6. Run `scrcpy -m 1024 --max-fps=25` as usual.



To switch back to USB mode: `adb usb`.
