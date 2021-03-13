<!--
SPDX-FileCopyrightText: 2021, Greenflash1986 aka Samuel
SPDX-License-Identifier: Apache-2.0
-->

# UnifiedNlpOverlay

A package for using [UnifiedNlp](https://github.com/microg/UnifiedNlp) together with GAPPS if your operating system.
This branch is only to show that it's possible to use an onetime-installation of an overlay and after that switch between
Unified and GAPPS the easiest way possible. After installing this package in vendor partition it's
possible to switch betweeen these two just by simply (de-)installing Unified.
The only contradiction for "the simplest way possible" is that you have to compile Unified and this
package yourself. Therefore it's only to show that it's possible and not as "production". But feel free to use it.
(Tested with LineageOS 16 (=Android 9))

## Instructions

(built with gradle 6.5.1)
1. build this package (_gradle assembleDebug_)
1. _adb push src/assets/etc_permissions/org.microg.nlp /etc/permissions_ (if this does not work try to push to _/system/etc..._)
1. _adb push build/outputs/apk/debug/UnifiedNlpOverlay-debug.apk /vendor/overlay/UnifiedNlpOverlay.apk_
   1. (installs this package in the vendor partition)
   1. (the apk has to be in the root of _/vendor/overlay_, subfolder will not work)
1. build _UnifiedNlp_ fork from https://github.com/erfanoabdi/UnifiedNlp (is also buildable with Gradle 6.5.1)
   1. you could also use the original repo at https://github.com/microg/UnifiedNlp but it's harder to get a working build from scratch.
   1. The key part for this whole thing is the signature which has to be the same for the build of this package and the version of _UnifiedNlp_
   1. (You can build AND install with gradle: _gradle app:installUnifiedNlpDebug_)
1. install the created apk of _Unified_.

## Background
Google has a list of "allowed location provider packages" in the sources of Android. Android collects
the signatures of these packages (the packages have to be on the "system"-partition) during startup and
thus has a list of "allowed location provider package signatures".
If you build this package yourself and install it in _/vendor/overlay_ you extend the list of "allowed
location provider packages" (_src/main/res/values/config.xml) as well as the list of "allowed location
 provider package signatures" (because you signed this package with your keys during build).

Now Android has the signature for the package _org.microg.nlp_ as "allowed location provider signature"
and we can install updates of the package _org.microg.nlp_ in the userspace and they are used from Android as
"location provider packages" as long as they have the same signature.

It would be possible to prevent the "build it yourself" misery but this would require someone to build
this package with the same keys as _UnifiedNlp_ was build. And this does not prevent the necessity to be
able to write in the vendor partition at least once.
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
