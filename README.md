# UnifiedNlpOverlay

Test for overwriting config_locationProviderPackageNames during boot of Android 9 and to get UnifiedNlp to work beside Gapps.

## Build

* aapt2.exe compile -v -o resources.zip --dir src\res
* aapt2 link -v --no-resource-removal --manifest src/AndroidManifest.xml -I C:\Users\GreenFlash1986\AppData\Local\apktool\framework\1.apk -o framework-res-overlay.apk.u resources.zip
* apksigner sign --ks \Users\GreenFlash1986\.android\debug.keystore --min-sdk-version=26 --out framework-res-overlay.apk framework-res-overlay.apk.u
* adb root && adb remount && adb push framework-res-overlay.apk /vendor/overlay/FrameworkResOverlay/FrameworkResOverlay.apk && adb reboot (the folder FrameworkResOverlay has to exist already)
