# Ration Reg app updates

This public repository holds the Android and Windows installers. Installed apps read [releases/latest.json](releases/latest.json) when they open. They also have **Settings → About Ration Reg → Check for updates**.

## Install the updater once

Download [RationReg-2.3.5.apk](releases/RationReg-2.3.5.apk) on each Android phone and [RationReg-Setup-2.3.5.exe](releases/RationReg-Setup-2.3.5.exe) on each Windows PC. Install over the existing app so its shop connection and local pending entries remain in place. Android requires approval to install the downloaded APK; Windows asks the user to run its installer. The website is updated separately through its existing Apps Script deployment.

## Publish the next version

1. Build the new APK and Windows installer from the local Ration Reg project. Increment the shared UI and native app version numbers, and keep the existing Android signing certificate.
2. In this repository, open `releases/` and upload the two new files with their versioned names, for example `RationReg-2.3.6.apk` and `RationReg-Setup-2.3.6.exe`. Keep old files so users who started an update can finish it.
3. Download each uploaded file once and compare its SHA-256 hash with the local build.
4. Edit `releases/latest.json` **last**. Set `version` to the new version and point `android` and `windows` at the exact raw GitHub URLs for the uploaded files. Update the optional SHA-256 entries. Commit the manifest change. GitHub's raw file cache may take about five minutes to refresh.
5. Open an installed app, use **Check for updates**, and verify the notification and correct download. When a new version is available the app prompts on launch; choosing **Later** dismisses that version's automatic prompt on that device.

An installed app opens the download in the system browser. The user then approves installation. The app does not install files without OS approval, and it does not notify while closed.

The repository contains no spreadsheets, stock data, connection keys, Apps Script server code, or Android signing secrets.
