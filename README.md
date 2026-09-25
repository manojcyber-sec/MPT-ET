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

# Experiment 4 — APK Dissection Using Apktool and Android Emulator

**Course:** 7CS1292 / Mobile Penetration Testing and Ethical Hacking  
**Platform:** Windows  
**Tools:** Android Studio, Android Emulator, ADB, Apktool, Android SDK Build-Tools  
**Training Application:** InsecureBankv2

## Aim

To learn the basic workflow of APK analysis using Apktool and an Android Emulator by obtaining an authorized training APK, decoding and inspecting its contents, performing a harmless UI modification, rebuilding and signing the APK, and testing the modified application in the emulator.

## Environment

- Android Studio
- Android Emulator — Pixel 5
- Android SDK Platform-Tools
- ADB
- Apktool
- InsecureBankv2 training application
- Windows

## Steps Performed

1. Started the Android Emulator and verified the device using ADB.
2. Identified the installed InsecureBankv2 training application.
3. Located the APK path using the Android Package Manager.
4. Pulled the authorized APK from the emulator to the Windows system.
5. Decoded the APK using Apktool.
6. Inspected the decoded AndroidManifest.xml and application structure.
7. Inspected SMALI files in the decoded project.
8. Modified a harmless UI text value without changing security functionality.
9. Rebuilt the modified APK using Apktool.
10. Signed the rebuilt APK using a lab signing key.
11. Verified the APK signature using apksigner.
12. Installed and tested the modified APK in the Android Emulator.
13. Verified that the harmless UI modification was reflected in the application.

## Commands Used

```bash
adb devices
adb shell pm list packages | findstr /i "insecure"
adb shell pm path com.android.insecurebankv2
adb pull <APK_PATH> C:\APKLab\insecurebankv2.apk

apktool --version
apktool d insecurebankv2.apk -o insecurebankv2_decoded
apktool b insecurebankv2_decoded -o insecurebankv2_modified.apk

keytool -genkeypair -v -keystore lab-key.jks -alias labkey -keyalg RSA -keysize 2048 -validity 10000
apksigner sign --ks lab-key.jks insecurebankv2_modified.apk
apksigner verify --verbose insecurebankv2_modified.apk

adb install insecurebankv2_modified.apk

# Experiment 5 — Android Application Creation and UI Event Testing

**Course:** 7CS1292 / Mobile Penetration Testing and Ethical Hacking  
**Platform:** Windows  
**IDE:** Android Studio  
**Emulator:** Pixel 5 API 30  
**Language:** Kotlin / Jetpack Compose

## Aim

To create a basic Android application with a TextView and Button, implement a button click event, display a harmless message, and test the application successfully on an Android Emulator.

## Tools & Setup

| Item | Details |
|---|---|
| Platform | Windows |
| IDE | Android Studio |
| Project | AndroidSecurityLab |
| Language | Kotlin |
| UI Framework | Jetpack Compose |
| Emulator | Pixel 5 API 30 |

## Steps Performed

1. Created a new Android Studio project using the Empty Activity template.
2. Created the project named `AndroidSecurityLab`.
3. Designed the application screen using Jetpack Compose.
4. Added the TextView text `Android Security Lab`.
5. Added a `SHOW MESSAGE` button.
6. Implemented the button click event using an OnClickListener.
7. Configured the application to display a harmless confirmation message when the button was pressed.
8. Built the application successfully.
9. Ran the application on the Pixel 5 Android Emulator.
10. Pressed the `SHOW MESSAGE` button and verified the output.

## Output

The Android application launched successfully in the emulator. The screen displayed:

- `Android Security Lab`
- `SHOW MESSAGE` button

The button responded to the click event and displayed the configured harmless confirmation message.

### Evidence

- Android Studio project screenshot
- Emulator output screenshot
- Screen recording of the practical

## Result

A basic Android application was successfully created, built, executed, and tested on the Android Emulator. The `SHOW MESSAGE` button responded correctly and produced the expected output.
