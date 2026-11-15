# PLAYFORM

PLAYFORM turns an Android phone into a Bluetooth controller for games on a Windows PC.

## First-time setup

### On the Windows PC

1. For gamepad mode, install the separate [ViGEmBus driver](https://github.com/nefarius/ViGEmBus/releases). PLAYFORM does not install drivers automatically. ViGEmBus is retired and no longer receives updates, so review its [end-of-life notice](https://docs.nefarius.at/projects/ViGEm/End-of-Life/) before installing.
2. Open `PLAYFORM-Gamepad.exe` and click **Start receiver**. Keep it running while you play. If its installer asks you to restart Windows, restart before continuing.

### On the Android phone

1. Transfer `PLAYFORM.apk` to the phone and open it to install. If Android asks, allow your file manager or browser to install unknown apps.
2. Open PLAYFORM and allow **Nearby devices** when prompted. Android 8–11 also need Location permission and the phone’s Location setting enabled for BLE scanning; PLAYFORM does not use your location.
3. Tap **Connect over Bluetooth**, grant **Nearby devices** permission, then choose your laptop from the scan list. If its scan entry says **check connection**, select it anyway; the app will verify the PLAYFORM service before marking it connected. Bluetooth Low Energy does not require pairing first.

The APK is signed for direct installation. Install it over the previous PLAYFORM app to keep saved HUD settings; uninstalling or clearing app storage deletes those settings.

If connection fails, make sure the PC receiver says it is ready. On Android 12+, check **Settings → Apps → PLAYFORM → Permissions → Nearby devices**. Android groups Bluetooth scan and connection access under this permission name. On Android 8–11, allow Location and turn on the phone’s Location setting. The app checks the receiver's service after connecting and retries once if Android reports a transient GATT error.

## Playing and checking input

- Keep **Xbox 360 gamepad (recommended)** selected in the PC app for games. ViGEmBus is required for this mode.
- Choose **Keyboard fallback** in the PC app for programs that only accept keyboard input.
- To check whether Windows sees the virtual controller, press **Windows+R**, enter `joy.cpl`, and look for the Xbox 360 controller while PLAYFORM is connected.
- Some games, especially games with anti-cheat, may block virtual controllers.

Closing the PC app window minimizes it to the notification area; use the tray menu's **Exit** command to stop it. The checkbox in the app controls automatic startup at Windows sign-in. Receiver messages are saved to `%LOCALAPPDATA%\PLAYFORM\receiver.log`.

## Custom HUD

The Android app saves HUD position, size, stick-cap size, hidden controls, opacity, and button mapping on the phone. Settings persist between app launches and are saved separately for each orientation. They are removed if you uninstall PLAYFORM or clear its app storage.

## Optional browser version

`Playform.html` is the standalone website alternative. Open it in Chrome on Android and tap **Connect over Bluetooth**. Browser Bluetooth availability depends on the browser and how the file is opened. The page requests landscape mode; if the browser cannot lock it, rotate the phone manually. Website HUD settings are stored separately in that browser and do not transfer to the APK.

## Do I need the .NET 8 SDK?

No. `PLAYFORM-Gamepad.exe` is self-contained, and the Android APK does not use .NET. The .NET SDK is only needed to edit and rebuild the Windows receiver from its C# source. Android app development uses the Android project in `android-app`, Android Studio/SDK, and Java—not the .NET SDK.
