# UnifiedNlpOverlay

A package for using [UnifiedNlp](https://github.com/microg/UnifiedNlp) together with GAPPS. This overlay
forces org.microg.nlp-package as LocationProvider. If it's installed you can not use the GAPPS
LocationProvider anymore. And you still have to place UnifiedNlp on system partition to get it to work.

## Instructions
1. download UnifiedOverlay.apk and org.microg.nlp.xml
1. get write access to system-partition: _adb root && adb remount_
1. place UnifiedNlpOverlay.apk into /system/vendor/overlay
    * adb push UnifiedNlpOverlay.apk /vendor/overlay/UnifiedNlpOverlay.apk
1. place org.microg.nlp.xml into /etc/permissions
    * _adb push org.microg.nlp.xml /etc/permissions_ (if this does not work try to push to _/system/etc/..._)
1. download and install UnifiedNlp.apk from [F-Droid](https://f-droid.org/de/packages/org.microg.nlp/)
    * _adb push <APK-Name> /system/priv-app/UnifiedNlp/UnifiedNlp.apk_
