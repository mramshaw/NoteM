# Mobile Note-taker

![Graphic](images/playstore.png)

A mobile note-taking app

## Goals

A note-taking app that can be used on mobile:

* Either iOS or Android
* Does not depend upon cloud storage
* Possibly web (optionally)

Possible uses:

1. Keep track of anything that might be put on a sticky
2. An encrypted password store

#### Storage

Should be capable of:

1. Local storage
2. <del>Sync'ing with the cloud (optionally)</del>

Ideally should NOT be dependent upon a device's Cloud account.

[Item 2, Cloud Sync'ing, was dropped. The app only uses local storage.]

#### Validation

* Either a Note title OR a Note body must be present

#### Actions

* Note can be added
* Note can be flagged
* Note can be starred
* Note can be edited (double-tap)
* Note can be deleted (swipe)

Notes can be filtered by `star` or `flag`.

#### Architecture

* Application constants should be centralized in one place
* Persistent storage should be mediated by a DAO (facilitates easy swapping)
* Application should be [reactive](http://en.wikipedia.org/wiki/Reactive_programming), or - at least - stream-based
* Include a database maintenance option

#### Instrumentation

The requirements are still to be determined; [Events](Events.md) defined, [Logging details](Logging.md) investigated.

#### Tests

Follow [Test Plan](TestPlan.md).

Unit tests as follows:

- [x] Tests for singleton DAO

## Reference

Some useful links follow.

#### Android App Bundle

[These replace the previous __APK__ (Android Package Kit) files.
 It is possible to install APK files but the Google Play Store
 requires __AAB__ (Android App Bundle) files. Only APKs from
 trusted providers should be installed - Google offers a number
 of APK protections, which include scanning the APK for exploits.]

Details: http://developer.android.com/platform/technology/app-bundle

AABs tend to reduce some of the bloat of APKs (see [Fat APKs](#fat-apks)
below for details of APK bloat), plus Google Play Store will handle
the delivery of builds appropriate for the processor type of the target
device.  So generally a good idea (much research suggests reducing the
download size of an app leads to more downloads).

#### App Signing by Google Play

How to sign an Android app: http://support.google.com/googleplay/android-developer/answer/7384423

#### Apple App Store

App Store Review Overview: http://developer.apple.com/app-store/review/

App Store Review Guidelines: http://developer.apple.com/app-store/review/guidelines/

App Store Submissions: http://developer.apple.com/app-store/submissions/

Analytics: http://developer.apple.com/app-store-connect/analytics/

#### Apple Developer Program

Home page: http://developer.apple.com/programs/

Gives access to [TestFlight](#testflight) as well as [App Store Connect](http://appstoreconnect.apple.com/).

#### Fabric.io

Fabric roadmap: http://get.fabric.io/roadmap

#### Fat APKs

Initial 'fat' release:

    app-release.apk             19.7 MB (19,664,349 bytes)

Targetted release:

    app-arm64-v8a-release.apk    7.7 MB (8,058,472 bytes)
    app-armeabi-v7a-release.apk  7.4 MB (7,743,759 bytes)
    app-x86_64-release.apk       7.9 MB (8,223,996 bytes)

These APKs correspond to the following processors:

    ARM     app-armeabi-v7a-release.apk
    ARM64   app-arm64-v8a-release.apk
    x86_64  app-x86_64-release.apk

[It turns out that it is not easy to determine the processor of an Android phone.]

#### Google Play Store

Overview: http://developer.android.com/distribute/best-practices/launch

#### IPA files

Apple apps are generally distributed as __IPA__ files (the situation with Apple APPs and
IPAs seems to be analagous to Android APKs and Android App Bundle files - both IPAs and
Android App Bundle files are normally ___Signed___).

Wikipedia is pretty informative on the subject of APPs: http://en.wikipedia.org/wiki/Bundle_(macOS)

Wikipedia is pretty informative on the subject of IPAs: http://en.wikipedia.org/wiki/.ipa

IPA files (actually ___archive___ files) are normally signed by a registered Apple
Developer.

#### Sentry.io

Sentry documentation: http://docs.sentry.io/

#### Sideloading

> Sideloading has several advantages when compared with other ways of delivering content to mobile devices

For more on Sideloading: http://en.wikipedia.org/wiki/Sideloading

#### TestFlight

Beta Testing Made Simple with TestFlight: http://developer.apple.com/testflight/

[Probably a good idea for iOS releases as Apple requirements are stringent.]

#### Unsigned IPA files

How to open an unsigned IPA: http://support.apple.com/en-us/guide/mac-help/mh40616/mac

While it is possible to install unsigned IPAs, they may only be valid for seven days.

Also, it may be necessary to ___register___ the target device first.

## To Do (General)

- [x] Add links for various deployment options
- [x] Add notes on Android build architectures
- [x] Add a [Test Plan](TestPlan.md)
- [ ] Investigate web drivers for testing
- [x] Investigate the details necessary to effectively debug/analyze the app
- [ ] Instrument app events to a level of granularity sufficient for debugging & analytics
- [ ] Build and release for web
- [ ] Deploy to GitHub Pages
- [ ] Investigate Google Tag Manager
- [ ] [Optional] Integrate with Fabric.io (deprecated; Crashlytics recommended) or Sentry.io
- [ ] Set up a CI/CD pipeline
- [x] Internationalize everything
- [x] Translations (English)
- [x] Translations (French)
- [ ] Translations (Spanish)

#### To Do (Google Play Store / Android)

- [ ] Build and test for Android
- [ ] Investigate Google Play Store ads
- [ ] Investigate APKs versus App Bundles (also code-signing)
- [ ] Publish to the Google Play Store

#### To Do (Apple App Store/ iOS)

- [ ] Build and test for iOS
- [ ] Investigate Apple APPs versus Apple IPAs (also code-signing)
- [ ] [Optional] Publish to TestFlight
- [ ] Publish to the App Store
