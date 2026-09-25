# MPT-ET

Mobile Penetration Testing and Ethical Hacking

# Experiment 1 — Browser-Based Android & ADB Essentials

**Course:** 7CS1292 / Mobile Penetration Testing and Ethical Hacking  
**Mode:** Browser (WebADB) + Physical Android Device (Wireless Debugging)  
**Tool:** WebADB  
**Browser:** Google Chrome  

## Aim

To introduce Android Debug Bridge (ADB) concepts through a browser-based workflow and practice device enumeration, shell access, package management, activity management, and basic Android file-system navigation without installing Android Studio or local ADB.

## Tools & Setup

| Item | Details |
|---|---|
| Interface | WebADB |
| Connection method | Wireless Debugging |
| Connected device ID | RE6090L1 |
| Browser | Google Chrome |

## Steps Performed

1. Opened WebADB in Google Chrome.
2. Enabled Developer Options and Wireless Debugging on the Android device.
3. Paired and connected the device to WebADB over Wi-Fi.
4. Opened the Interactive Shell and confirmed the device connection.
5. Executed basic ADB shell commands.
6. Practiced Android file-system navigation.
7. Used package management commands to inspect installed applications.
8. Used activity management commands to open an Android system activity.

## Commands Executed

```bash
adb devices
adb shell

pwd
whoami
ls
cd /sdcard
ls -l
cd Download
ls
cd /

pm list packages
pm path com.android.settings

am start -a android.settings.SETTINGS
```

## Output

The Android device was successfully connected through WebADB. Basic shell navigation, package inspection, APK path identification, and activity launching were performed successfully.

### Evidence

- WebADB connection screenshot
- ADB shell screenshot
- Screen recording of the practical

## Result

ADB operations were successfully performed through WebADB using a wireless Android device. Device enumeration, shell access, package management, activity management, and basic file-system navigation were successfully demonstrated.


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
2. Opened Android SDK Manager.
3. Verified the installed Android SDK platform.
4. Verified Android SDK Build-Tools.
5. Verified Android SDK Platform-Tools.
6. Verified Android Emulator.
7. Verified Android SDK Command-line Tools.
8. Verified the Emulator Hypervisor Driver and required virtualization support.

## Output

Android Studio SDK Manager displayed the installed Android platform and required SDK tools successfully.

### Evidence

- SDK Platforms screenshot
- SDK Tools screenshot
- Screen recording of the practical

## Result

Android Studio was successfully installed and the Android SDK and required SDK tools were configured and verified successfully.


# Experiment 3 — Android Architecture, Boot Process & Partition Layout

**Course:** 7CS1292 / Mobile Penetration Testing and Ethical Hacking  
**Platform:** Windows  
**Software:** Android Studio and Android Emulator  
**Command-line Tool:** Android SDK Platform-Tools (ADB)  
**Virtual Device:** Pixel 8  

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
```

## Key Results

- ADB successfully connected to the Pixel 8 emulator.
- Android Version: 15.
- API Level: 35.
- CPU ABI: x86_64.
- Linux kernel information was obtained.
- `/system`, `/vendor`, and `/product` directories were inspected.
- Mounted filesystems were examined using `df -h` and `/proc/mounts`.
- `super`, `vbmeta`, and `metadata` block devices were identified.
- Dynamic partitions were reported as enabled.
- Some `/proc` information returned `Permission denied`, which was recorded without bypassing permissions.

### Evidence

- ADB and architecture screenshot
- Partition information screenshot
- Screen recording of the practical

## Result

The Android emulator architecture, boot-related information, mounted filesystems, and partition layout were successfully examined using read-only ADB commands.


# Experiment 4 — APK Dissection Using Apktool and Android Emulator

**Course:** 7CS1292 / Mobile Penetration Testing and Ethical Hacking  
**Platform:** Windows  
**Tools:** Android Studio, Android Emulator, ADB, Apktool, Android SDK Build-Tools  
**Training Application:** InsecureBankv2  
**Emulator:** Pixel 5  

## Aim

To learn the basic workflow of APK analysis using Apktool and an Android Emulator by obtaining an authorized training APK, decoding and inspecting its contents, performing a harmless UI modification, rebuilding and signing the APK, and testing the modified application in the emulator.

## Environment

- Android Studio
- Android Emulator — Pixel 5
- Android SDK Platform-Tools
- ADB
- Apktool
- Android SDK Build-Tools
- InsecureBankv2 training application
- Windows

## Steps Performed

1. Started the Android Emulator and verified the device using ADB.
2. Identified the installed InsecureBankv2 training application.
3. Located the APK path using the Android Package Manager.
4. Created the working directory `C:\APKLab`.
5. Pulled the authorized APK from the emulator to the Windows system.
6. Decoded the APK using Apktool.
7. Inspected the decoded `AndroidManifest.xml` and application structure.
8. Inspected SMALI files in the decoded project.
9. Performed a harmless UI modification without changing security functionality.
10. Rebuilt the modified APK using Apktool.
11. Signed the rebuilt APK using a lab signing key.
12. Verified the APK signature using `apksigner`.
13. Installed and tested the modified APK in the Android Emulator.
14. Verified the modified application and UI output.

## Commands Used

```bash
adb devices
adb shell pm list packages | findstr /i "insecure"
adb shell pm path com.android.insecurebankv2

adb pull "/data/app/<actual-apk-path>/base.apk" "C:\APKLab\insecurebankv2.apk"

apktool --version
apktool d insecurebankv2.apk -o insecurebankv2_decoded
apktool b insecurebankv2_decoded -o insecurebankv2_modified.apk

keytool -genkeypair -v -keystore lab-key.jks -alias labkey -keyalg RSA -keysize 2048 -validity 10000

apksigner sign --ks lab-key.jks insecurebankv2_modified.apk
apksigner verify --verbose insecurebankv2_modified.apk

adb install insecurebankv2_modified.apk
```

## Output

- The Android Emulator was successfully detected through ADB.
- The InsecureBankv2 package was identified successfully.
- The authorized APK was extracted from the emulator.
- APK contents were decoded and inspected.
- AndroidManifest.xml and SMALI files were examined.
- A harmless UI modification was performed.
- The modified APK was rebuilt and signed.
- The modified application was installed and tested on the emulator.

### Evidence

- ADB and APK extraction screenshot
- APK analysis screenshot
- Rebuild/signing screenshot
- Modified application emulator screenshot
- Screen recording of the practical

## Result

The authorized InsecureBankv2 training APK was successfully analyzed using Apktool, modified with a harmless UI change, rebuilt, signed, installed, and tested in the Android Emulator.


# Experiment 5 — Android Application Creation and UI Event Testing

**Course:** 7CS1292 / Mobile Penetration Testing and Ethical Hacking  
**Platform:** Windows  
**IDE:** Android Studio  
**Project:** AndroidSecurityLab  
**Emulator:** Pixel 5 API 30  
**Language:** Kotlin  
**UI Framework:** Jetpack Compose  

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
4. Added the text `Android Security Lab`.
5. Added a `SHOW MESSAGE` button.
6. Implemented the button click event.
7. Configured the application to display a harmless confirmation message when the button was pressed.
8. Built the application successfully.
9. Ran the application on the Pixel 5 Android Emulator.
10. Pressed the `SHOW MESSAGE` button and verified the output.

## Output

The Android application launched successfully in the emulator.

The screen displayed:

- `Android Security Lab`
- `SHOW MESSAGE` button

The button responded to the click event and displayed the configured harmless confirmation message.

### Evidence

- Android Studio project screenshot
- Emulator output screenshot
- Screen recording of the practical

## Result

A basic Android application was successfully created, built, executed, and tested on the Android Emulator. The `SHOW MESSAGE` button responded correctly and produced the expected output.
