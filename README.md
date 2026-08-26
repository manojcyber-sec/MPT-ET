# MPT-ET
Mobile Pentestration Testing and Ethical Hacking

# Experiment 1 — Browser-Based Android & ADB Essentials

**Course:** 7CS1292 / Mobile Penetration Testing and Ethical Hacking  
**Mode:** Browser (WebADB) + Physical Android Device (Wireless Debugging)  
**Tool:** WebADB (https://app.webadb.com/)  
**Browser:** Google Chrome  

## Aim

To introduce Android Debug Bridge (ADB) concepts through a browser-based workflow, and practice device enumeration, shell access, package management (pm), activity management (am), and basic Android file-system navigation — without installing Android Studio or local ADB.

## Tools & Setup

| Item | Details |
|---|---|
| Interface | WebADB (app.webadb.com) |
| Connection method | Wireless Debugging (ADB over Wi-Fi) |
| Connected device ID | RE6090L1 |
| Browser | Chrome |

USB was not available, so the device was connected using Wireless Debugging: Developer Options → Wireless Debugging → paired via pairing code over the same Wi-Fi network, then connected through the ADB over WiFi option in WebADB.

## Steps Performed

1. Opened WebADB at app.webadb.com in Chrome.
2. Enabled Developer Options and Wireless Debugging on the Android device.
3. Paired and connected the device to WebADB over Wi-Fi.
4. Opened Interactive Shell and confirmed device connection (RE6090L1).
5. Ran basic navigation and identity commands.
6. Navigated the device file system under /sdcard.

## Commands Executed & Output


# Experiment 2 — Android Studio Installation and SDK Configuration

**Course:** 7CS1292 / Mobile Penetration Testing and Ethical Hacking  
**Platform:** Windows  
**Tool:** Android Studio  

## Aim

To install Android Studio and verify the Android SDK and required SDK tools for Android application development.

## Tools & Setup

| Item | Details |
|---|---|
| Platform | Windows |
| IDE | Android Studio |
| Android SDK | Installed |
| SDK Platform | Android 17 (API 37) |
| Android Emulator | Installed |

## Steps Performed

1. Installed Android Studio with the required Android SDK and emulator components.
2. Opened **Android SDK Manager** and verified the installed SDK platform.
3. Verified the required SDK tools including **Build-Tools, Platform-Tools, Emulator, Command-line Tools, and Emulator Hypervisor Driver**.
4. Confirmed that the required SDK components were successfully installed and available.

## Output

Android Studio SDK Manager displayed the installed Android platform and required SDK tools successfully.

### Evidence

- SDK Platforms screenshot
- SDK Tools screenshot
- Screen recording of the practical

## Result

Android Studio was successfully installed and the Android SDK and required SDK tools were configured and verified successfully.

# Experiment 3 – Android Architecture, Boot Process & Partition Layout

## Aim

To examine the Android system architecture, boot-related information, mounted filesystems, and partition layout of an Android emulator using ADB shell commands.

## Objectives

- Verify ADB connectivity with the Android emulator.
- Identify the Android version, SDK level, CPU architecture, and Linux kernel.
- Inspect important Android system directories.
- Examine boot-related properties.
- Analyze mounted filesystems and mount points.
- Inspect Android block-device and partition information.
- Identify named partitions such as `super`, `vbmeta`, and `metadata`.
- Check whether dynamic partitions are enabled.

## Environment

- Android Studio Emulator
- Virtual Device: Pixel 8
- Android Version: 15
- API Level: 35
- CPU ABI: x86_64
- ADB: Android Debug Bridge
- Host OS: Windows

## Commands Used

```bash
adb devices
adb shell

getprop ro.build.version.release
getprop ro.build.version.sdk
getprop ro.product.cpu.abi
uname -a

getprop ro.boot.slot_suffix
getprop ro.boot.verifiedbootstate
cat /proc/cmdline

df -h
cat /proc/mounts
cat /proc/partitions

ls -l /dev/block/by-name

ls /system
ls /vendor
ls /product

getprop ro.boot.dynamic_partitions
getprop ro.boot.super_partition
