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



# Use scrcpy with Dummy Video Device

1. Install dependencies:

    ```bash
    sudo apt install ffmpeg libsdl2-2.0-0 adb wget gcc git pkg-config meson ninja-build libsdl2-dev libavcodec-dev libavdevice-dev libavformat-dev libavutil-dev v4l2loopback-dkms v4l2loopback-utils
    ```

2. Create a Dummy Video Device:

    ```bash
    sudo modprobe v4l2loopback
    ```

3. Check for the created device:

    ```bash
    v4l2-ctl --list-devices
    ```

4. Execute scrcpy with the Dummy Video Device:

    ```bash
    scrcpy -m 1080 --max-fps=60 --lock-video-orientation=1 --v4l2-sink=/dev/video0 --turn-screen-off --stay-awake --power-off-on-close --crop=1080:1437:0:290
    ```

   - `-m 1080`: Set the height of the mirrored screen.
   - `--max-fps=60`: Set the maximum frames per second.
   - `--lock-video-orientation=1`: Lock the video orientation.
   - `--v4l2-sink=/dev/video0`: Set the Dummy Video Device.
   - `--turn-screen-off`: Turn off the device screen.
   - `--stay-awake`: Keep the device awake.
   - `--power-off-on-close`: Power off the device on scrcpy closure.
   - `--crop=1080:1437:0:290`: Crop the mirrored screen.

