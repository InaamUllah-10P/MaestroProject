# Installing Maestro
* Installing the CLI
Dependencies:
* Xcode (recommended version is 14 or higher)
Please make sure that Command Line Tools are installed (Xcode -> Preferences -> Locations -> Command Line Tools)
* Run the following command to install Maestro on Mac OS, Linux or Windows (WSL):
* curl -Ls "https://get.maestro.mobile.dev" | bash
Upgrading the CLI
* Simply run the installation script again:
*curl -Ls "https://get.maestro.mobile.dev" | bash


# Connecting to Your Device
* iOS
Before running Flows on iOS Simulator, install Facebook IDB tool
• brew tap facebook/fb
• brew install facebook/fb/idb-companion
Note: At the moment, Maestro does not support real iOS devices

* Android
• maestro test will automatically detect and use any local emulator or USB-connected physical device.
* Build and Install your App
Currently maestro supports emulator and device builds for Android (.apk) and iOS Simulator (.app).

* Android
• Android app binary requirements:
• APK (AAB not supported)
• Compatible with x86_64 architecture
• Requires Android API level 26 or newer
• Release and Debug builds both supported
• Building with Gradle
• Build your app using one of the commands below. Then find the appropriate APK file in the build/outputs/apk/ output directory.
# Release build
./gradlew assembleRelease
​
# Debug build
./gradlew assembleDebug


# iOS
* Building with Xcode
Maestro currently supports iOS Simulator builds (.app), AppStore distribution device builds (.ipa) are not currently supported. The easiest way to get an app installed on the simulator is by building and running it from Xcode (make sure that simulator target is selected):

* Default build location
If you want to install the .app manually, the file can be found under the Products folder at Xcode Menu: Product -> Show Build Folder in Finder -> Then go to path Products/Debug-iphonesimulator
The .app file can then be installed on the simulator by simple dragging and dropping the file.

* Writing Your First Flow
Write a test in a YAML file

# Signup.yaml
​
appId: com.launchgood.Launchgood.development
---
- launchApp:
    appId: "com.launchgood.Launchgood.development"
    clearState: true
- tapOn: Ok
- tapOn:
    id: profile-unselected
- tapOn: Sign Up
- tapOn: First Name
- inputText: inaam
- tapOn: Last Name
- inputText: LG
- tapOn: Email
- inputRandomEmail
- tapOn: Password
- inputText: 123456
- tapOn:
    text: "Sign Up"     # (optional) Finds text or accessibility text that matches regexp.
    index: 1
* Make sure an iOS simulator is running (instructions) and app is correctly installed on a selected device (instructions).
* Run it!
* maestro test Signup.yaml




Run a Flow
# Download the MaestroProject

Install the Launchgood/Wikipedia app and then run the associated Flow using the maestro test command.
* Android
Connect the Android device with the system
install Wikipedia.apk on the Android device
• cd ./MaestroProject/wikipedia-android-advanced
• run the command on the terminal: maestro test run-test.yml
Note: launch the app 

* iOS
Run the simulator from the xcode
Install the Launchgood.app on the simulator
• cd ./MaestroProject/Launchgood
• run the command on the terminal: maestro test Signup.yaml

