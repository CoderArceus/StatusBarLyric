# StatusBarLyric

![StatusBarLyric banner](ic_home_background.webp)

StatusBarLyric is an Xposed module that displays timed lyrics in the Android status bar. It supports configurable lyric and icon styling, anchor selection, and additional SystemUI behavior.

This repository is a community-maintained fork of [Block-Network/StatusBarLyric](https://github.com/Block-Network/StatusBarLyric). The upstream project is archived. Original notices and the GNU General Public License v3.0 are retained; see [LICENSE](LICENSE).

## Compatibility

- Requires Android 11 (API 30) or later and an Xposed-compatible framework. The module is scoped to `com.android.systemui`; LSPosed is recommended.
- This fork updates the SuperLyric integration to the Binder-based SuperLyric API 3.7.
- An Android 16+ AOSP status-bar clock fallback is included for ROMs where an old saved anchor no longer matches.
- The current compatibility baseline was built and tested with SuperLyric 4.1 on a POCO F6 (`peridot`) running Android 17 (API 37, Penguin/CLO ROM). Other devices and ROMs are not yet verified; SystemUI layouts vary between ROMs.

## Installation

1. Install the StatusBarLyric APK and activate it in your Xposed manager, applying the module to **System UI** (`com.android.systemui`).
2. Reboot if your Xposed framework requires it, then open StatusBarLyric and enable the master switch.
3. On first setup, open **Hook Page**, enable **Test Mode**, and restart SystemUI. Select a suitable clock/anchor from the detected hook points.
4. Turn Test Mode off and restart SystemUI again.
5. If you use SuperLyric as the lyric provider, install and configure SuperLyric separately, then enable the music app you want it to monitor. Play a track with available timed lyrics.

If lyrics do not appear, confirm that the module is active for SystemUI, that an anchor is selected, and that the lyric provider is sending data. Restart the music app and SystemUI after changing module or provider settings that request a restart.

## Build from source

### Requirements

- JDK 21
- Android SDK with Android SDK Platform 36 and the matching Android build tools
- Network access for Gradle to resolve dependencies on the first build

Set `ANDROID_HOME` or `ANDROID_SDK_ROOT` to your SDK directory, or provide `sdk.dir` in `local.properties`. Then run:

```sh
./gradlew assembleDebug
```

The debug APK is written under `app/build/outputs/apk/debug/`. Its filename includes the app version, build type, and build timestamp.

## Project links

- [Upstream project](https://github.com/Block-Network/StatusBarLyric)
- [SuperLyric](https://github.com/HChenX/SuperLyric)
- [SuperLyric API](https://github.com/HChenX/SuperLyricApi)
- [Original usage guide](https://blog.xiaowine.cc/posts/8e64/)
- [Contributing guide](doc/CONTRIBUTING.md)
- [Contributor history](https://github.com/Block-Network/StatusBarLyric/graphs/contributors)
- [EULA](doc/EULA.md)
- [GNU General Public License v3.0](LICENSE)
