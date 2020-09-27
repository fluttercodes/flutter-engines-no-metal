# Flutter engines (metal disabled)

These flutter engines have been compiled with metal disabled in iOS. This allows you to use SkSL cache files for iOS builds to reduce first-run jank.

How to use SkSL caching: https://github.com/flutter/flutter/wiki/Reduce-shader-compilation-jank-using-SkSL-warm-up

## How to use

* Download the engine which matches your flutter version *exactly* - you must match your engine to your flutter sdk. The version strings in the repo here match the version string of the flutter sdk.
* Unzip the engine zips and move the `Flutter.framework` folder inside the zip into the respective folder at `$FLUTTER_HOME/bin/cache/artifacts/engine/[ios-profile/ios-release]` where `FLUTTER_HOME` represents where your flutter SDK lives on your disk. You should overwrite the existing `Flutter.framework` folder with the one contained in the zip file.
* Do a `flutter clean` and rebuild your project and it will now build iOS with metal disabled.

## Restoring the default engine

If you ever want to go back to the normal one, simply delete the engine artifacts and re-download them:
```
rm -rf $FLUTTER_HOME/bin/cache/artifacts/engine/*
flutter upgrade
flutter doctor
flutter precache
```
