# Ration Reg app updates

Latest version: **2.3.8 — native in-app updater**.

## Install this version once

- [Android APK](https://raw.githubusercontent.com/thehive2119/Ration-Reg/main/releases/RationReg-2.3.8.apk)
- [Windows installer](https://raw.githubusercontent.com/thehive2119/Ration-Reg/main/releases/RationReg-Setup-2.3.8.exe)

Save pending entries first, then install over the existing app. Keep its app data and existing shop connection. Android versions 2.3.6/2.3.7 need this APK installed manually once because their WebView blocks the previous update check. Do not uninstall the app to update it.

## Updates from version 2.3.8 onward

Open **Settings → About Ration Reg → Check for updates**. When an update is available:

1. Choose **Download update**. Ration Reg downloads it internally and shows progress.
2. The app verifies the SHA-256 hash. Android additionally verifies its own package name, newer version and signing certificate.
3. Choose **Install update**. Android opens its system package installer. If asked, allow installation from Ration Reg and return to continue. Windows opens its local installer and closes Ration Reg after saving its local settings.
4. Approve the operating system installation. Windows' installer offers to reopen the app when finished.

The updater does not open a browser. System installation/permission screens remain required. Stock data stays in each shop's existing workbooks. Apps do not notify while closed.

## Publish the next version

1. Build a higher version with the original Android signing key.
2. Upload both versioned files into `releases/`, for example `RationReg-2.3.9.apk` and `RationReg-Setup-2.3.9.exe`. Keep older versions.
3. Download the uploaded files and verify their SHA-256 hashes against the local builds.
4. Update `releases/latest.json` **last**, setting `version`, `android`, `windows`, and both **required** `sha256` values. The URLs must use this repository's exact raw GitHub paths and versioned filenames.
5. Check from a device before rolling out to everyone. GitHub raw-file caching may take about five minutes to refresh.

The website still uses its existing Apps Script deployment process. This public repository contains installers, the update manifest and instructions. It contains no stock data, connection codes, spreadsheet IDs, signing keys or Apps Script server source.

Native HTTPS download and hash verification were tested on Windows and in a Java transport test. Physical Android installation, Android unknown-source permission screens and actual Windows installer upgrade were not exercised on a device.
