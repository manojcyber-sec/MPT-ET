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
