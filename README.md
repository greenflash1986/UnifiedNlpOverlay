<!--
SPDX-FileCopyrightText: 2021, Greenflash1986 aka Samuel
SPDX-License-Identifier: Apache-2.0
-->

# UnifiedNlpOverlay

A package for using [UnifiedNlp](https://github.com/microg/UnifiedNlp) together with GAPPS. This overlay
forces org.microg.nlp-package as LocationProvider. If it's installed you can not use the GAPPS
LocationProvider anymore. And you still have to place UnifiedNlp on system partition to get it to work.

## Current state

Tested with Android 9 - Pie.

Currently there are no signed packages or something like that. Feel free to contact me, if you need them.


## Instructions
1. download UnifiedOverlay.apk and org.microg.nlp.xml
1. get write access to system-partition: _adb root && adb remount_
1. place UnifiedNlpOverlay.apk from [Releases](https://github.com/greenflash1986/UnifiedNlpOverlay/releases) into /system/vendor/overlay
    * adb push UnifiedNlpOverlay.apk /vendor/overlay/UnifiedNlpOverlay.apk
1. place org.microg.nlp.xml into /etc/permissions
    * _adb push org.microg.nlp.xml /etc/permissions_ (if this does not work try to push to _/system/etc/..._)
1. download and install UnifiedNlp.apk from [F-Droid](https://f-droid.org/de/packages/org.microg.nlp/)
    * _adb push <APK-Name> /system/priv-app/UnifiedNlp/UnifiedNlp.apk_
	
## Background

UnifiedNlp offers three different versions with different package names (Legacy-version, _com.google.android.gms_, _org.microg.nlp_).
On ROMs without Gapps it's possible to use the version with _com.google.android.gms_ because  there will be no conflicts.
On ROMs WITH Gapps you have to use _org.microg.nlp_ to avoid these conflicts.

Android has a internal list of "allowed location providers packages". Originally this list contains 
_com.google.android.gms_ and _com.android.location.fused_. Android collects the signatures of this packages
IN THE SYSTEM partition at startup and uses these signatures as "allowed" signatures. With this overlay you some kind of 
disable the "list of allowed location providers" and tell Android to only use _org.microg.nlp_.

PS: Because of the "system-partition"-thing you have to use either a ROM with the provided patch from UnifiedNlp 
or install UnifiedNlp in the system-partition.

This overlay enables the use of UnifiedNlp as 

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
