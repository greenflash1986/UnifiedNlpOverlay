<!--
SPDX-FileCopyrightText: 2021, Greenflash1986 aka Samuel
SPDX-License-Identifier: Apache-2.0
-->

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

## Licence

    Copyright 2021 Greenflash1986 aka Samuel

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
