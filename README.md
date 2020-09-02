# Mobile Note-taker

![Graphic](images/playstore.png)

A mobile note-taking app

## Contents

The contents are as follows:

* [Goals](#goals)
    * [Storage](#storage)
    * [Validation](#validation)
    * [Actions](#actions)
    * [Architecture](#architecture)
    * [Performance](#performance)
    * [Instrumentation](#instrumentation)
    * [Tests](#tests)
* [Reference](#reference)
    * [Analytics Providers](#analytics-providers)
    * [Android App Bundle](#android-app-bundle)
    * [App Signing by Google Play](#app-signing-by-google-play)
    * [Apple App Store](#apple-app-store)
    * [Apple Certificates](#apple-certificates)
    * [Apple Developer Program](#apple-developer-program)
    * [Crashlytics](#crashlytics)
    * [Fabric.io](#fabricio)
    * [fastlane](#fastlane)
    * [Fat APKs](#fat-apks)
    * [Firebase App Distribution](#firebase-app-distribution)
    * [Firebase Remote Config](#firebase-remote-config)
    * [Google Play Store](#google-play-store)
    * [IPA files](#ipa-files)
    * [Sentry.io](#sentryio)
    * [Sideloading](#sideloading)
    * [TestFlight](#testflight)
    * [UDIDs](#udids)
    * [Unsigned IPA files](#unsigned-ipa-files)
* [To Do](#to-do)
    * [To Do (Application)](#to-do-application)
    * [To Do (General)](#to-do-general)
    * [To Do (Google Play Store / Android)](#to-do-google-play-store--android)
    * [To Do (Apple App Store/ iOS)](#to-do-apple-app-store-ios)

## Goals

A note-taking app that can be used on mobile:

* Either iOS or Android
* Does not depend upon cloud storage (can work offline)
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
* Analytics should be mediated by a single component (to facilitate easy swapping of [Analytics Providers](#analytics-providers))
* Application should be [reactive](http://en.wikipedia.org/wiki/Reactive_programming), or - at least - stream-based
* Include a database maintenance option
* Significant [events](Events.md) logged

#### Performance

* Should have native levels of performance for each platform (Android or iOS)
* Telemetry should not significantly impact performance (particularly in offline mode)

#### Instrumentation

Application [Events](Events.md) have been defined, [Logging details](Logging.md) have been investigated.

#### Tests

Follow [Test Plan](TestPlan.md) in English, French and (eventually) Spanish.

Unit tests as follows:

- [x] Tests for singleton DAO

## Reference

Some useful links follow.

[The links are in alphabetical order.]

#### Analytics Providers

As with Crash Reporting providers, there are many options.

Here is a list of [Analytics Providers](Analytics.md).

#### Android App Bundle

[These replace the previous __APK__ (Android Package Kit) files.
 It is possible to install APK files but the Google Play Store
 requires __AAB__ (Android App Bundle) files. Only APKs from
 trusted providers should be installed - Google offers a number
 of APK protections, which include scanning the APK for exploits.]

Overview: http://developer.android.com/platform/technology/app-bundle

AABs tend to reduce some of the bloat of APKs (see [Fat APKs](#fat-apks)
below for details of APK bloat), plus Google Play Store will handle
the delivery of builds appropriate for the processor type of the target
device.  So generally a good idea (much research suggests reducing the
download size of an app leads to more downloads).

About Android App Bundles: http://developer.android.com/guide/app-bundle

Test your Android App Bundle: http://developer.android.com/guide/app-bundle/test

#### App Signing by Google Play

How to sign an Android app: http://support.google.com/googleplay/android-developer/answer/7384423

#### Apple App Store

Developer program is generally referred to as __App Store Connect__.

[formerly __iTunes Connect__, which still appears in older documentation.]

App Store Review Overview: http://developer.apple.com/app-store/review/

App Store Review Guidelines: http://developer.apple.com/app-store/review/guidelines/

App Store Submissions: http://developer.apple.com/app-store/submissions/

Analytics: http://developer.apple.com/app-store-connect/analytics/

#### Apple Certificates

Generally, apart from [Unsigned IPA files](#unsigned-ipa-files), iOS apps
should be signed by Apple. This requires certificates.

Apple certificates seem to fall into two categories: __developer certificates__
and __provisioning certificates__.

Developer certificates are meant for local testing only.

Provisioning certificates can apparently be divided into __App Store__ (for
distribution to [TestFlight](#testflight) or the [Apple App Store](#apple-app-store))
certificates and __Ad Hoc__ (general distribution, probably for testing purposes,
to anyone other than [TestFlight](#testflight) or the [Apple App Store](#apple-app-store))
certificates.

For __Ad Hoc__ testing it appears the device must be registered; for __App Store__
(i.e. [TestFlight](#testflight)) testing this does not seem to be the case.

To register the testing device, the [UDID](#udids) of the target device is required.

#### Apple Developer Program

Home page: http://developer.apple.com/programs/

Gives access to [TestFlight](#testflight) as well as [App Store Connect](http://appstoreconnect.apple.com/).

#### Crashlytics

[Acquired by Google; now called Firebase Crashlytics.]

http://firebase.google.com/docs/crashlytics/

#### Fabric.io

Fabric roadmap: http://get.fabric.io/roadmap

[Acquired by Google; now integrated into Firebase. Links to all of the replacing Firebase products.]

#### fastlane

> Automate your development and release process

From: http://fastlane.tools/

Seems to be another integration platform, along the lines of [Fabric.io](#fabricio)
(now owned by Google and integrated into Firebase) or [buddybuild](http://www.buddybuild.com/)
(owned by Apple). Unlike buddybuild, it covers both Android builds and iOS builds.

Can be used with [Firebase App Distribution](#firebase-app-distribution) (which also covers
both Android and iOS).

#### Fat APKs

Initial 'fat' release:

    app-release.apk             23   MB (23,086,334 bytes)

Targetted releases:

    app-arm64-v8a-release.apk    8.6 MB  (8,943,212 bytes)
    app-armeabi-v7a-release.apk  8.2 MB  (8,582,949 bytes)
    app-x86_64-release.apk       8.8 MB  (9,154,421 bytes)

[These are in roughly chronological order: the newest phones are
 probably ARM64 (v8a) processors; tablets and older phones are
 probably ARM (v7a) processors; and the oldest phones x86_64
 processors (and there is an even older option - which is not
 a target build for this app).]

These APKs correspond to the following processors:

    ARM     app-armeabi-v7a-release.apk
    ARM64   app-arm64-v8a-release.apk
    x86_64  app-x86_64-release.apk

[It is non-trivial to determine the processor of an Android device.
 Trial-and-error works; this app is tested & working on ARM processor
 (both tablets and phones) devices and ARM64 processor devices.]

And the corresponding App Bundle:

    app-release.aab             23   MB (23,207,957 bytes)

[The App Bundle should include builds for ARM, ARM64 and x86_64 - so this
 App Bundle should be about the same size as the Fat APK - which it is.]

#### Firebase App Distribution

> built as the next evolution of Fabric's Crashlytics Beta

Covers both Android builds and iOS builds.

As of the time of writing (May, 2020) only supports APKs and
[IPA files](#ipa-files) (which must be signed). [Android App Bundles](#android-app-bundle)
are not supported.

Offers three integrations (from simplest to most complex):

* Firebase console
* Firebase CLI
* [fastlane](#fastlane)

[For Android builds, there is also __Gradle__.]

___Nota Bene___ (mainly a warning):

> Firebase App Distribution is a __beta release__. This means that
> the functionality might change in backward-incompatible ways. A
> beta release is not subject to any SLA or deprecation policy and
> may receive limited or no support.

From: http://firebase.google.com/docs/app-distribution

[Seems to be a viable alternative to [TestFlight](#testflight).]

Optional integration with [Crashlytics](#crashlytics).

#### Firebase Remote Config

[Similiar to Environment variables, effectively server-side parameters.
 As with Environment variables, need to define sensible fallback defaults.]

Enables [A/B Testing](http://firebase.google.com/docs/ab-testing),
seasonal theming, as well as many other possibilities.

Overview: http://firebase.google.com/products/remote-config/

> Firebase Remote Config is a cloud service that lets you  
> change the behavior and appearance of your app without  
> requiring users to download an app update. When using  
> Remote Config, you create in-app default values that  
> control the behavior and appearance of your app. Then,  
> you can later use the Firebase console or the Remote  
> Config backend APIs to override in-app default values for  
> all app users or for segments of your user base.

From: http://firebase.google.com/docs/remote-config/

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

> TestFlight makes it easy to invite users to test your apps and collect valuable
> feedback before releasing your apps on the App Store. You can invite up to
> 10,000 testers using just their email address or by sharing a public link.

[Probably a good idea for iOS releases as Apple requirements are stringent.
 It sounds a lot like [Fabric.io](#fabricio).]

TestFlight on the App Store: http://apps.apple.com/us/app/testflight/id899247664

#### UDIDs

Apple (iOS) devices have a UDID (Unique Device Identifier).

[This is apparently a 40-character hexadecimal string.]

For testing, it may be necessary to register these device IDs in advance.

[As with determining an Android device's processor type, determining an iOS
 device's UDID appears to be non-trivial.]

To determine the device's UDID: http://whatsmyudid.com/

#### Unsigned IPA files

How to open an unsigned IPA: http://support.apple.com/en-us/guide/mac-help/mh40616/mac

While it is possible to install unsigned IPAs, they may only be valid for seven days.

It may be necessary to ___register___ the [UDID](#udids) of the target device first.

## To Do

The following sections cover Application improvements (Android & iOS), General
improvements not specifically related to the application, Google Play Store / Android
improvements (i.e. Android only) and Apple App Store / iOS improvements (i.e. iOS only).

#### To Do (Application)

Please refer to the [Roadmap](Roadmap.md).

#### To Do (General)

- [x] Add links for various deployment options
- [x] Add notes on Android build architectures
- [x] Add a [Test Plan](TestPlan.md)
- [ ] Investigate web drivers for testing
- [x] Investigate the details necessary to effectively debug/analyze the app
- [x] Instrument app events to a level of granularity sufficient for debugging & analytics
- [ ] Verify granularity of instrumentation for Metrics/Analytics/Debugging/Logging purposes
- [ ] Build and release for web
- [ ] Deploy to GitHub Pages
- [ ] Investigate Google Tag Manager
- [ ] Investigate SEO for apps
- [x] [Optional] Integrate with [Crashlytics](#crashlytics) or [Sentry.io](#sentryio)
- [x] Internationalize everything
- [x] Translations (English)
- [x] Translations (French)
- [ ] Translations (Spanish)
- [ ] Have someone review French Translation
- [ ] Have someone review Spanish Translation
- [x] Investigate [Analytics Providers](#analytics-providers)
- [x] Investigate [Firebase Remote Config](#firebase-remote-config)

#### To Do (Google Play Store / Android)

- [x] Build and test for Android
- [ ] Investigate Google Play Store ads
- [x] Investigate APKs versus App Bundles
- [x] Investigate Android code-signing
- [ ] Set up a CI/CD pipeline
- [x] [Optional] Test with Firebase Test Lab
- [x] [Optional] Publish to [Firebase App Distribution](#firebase-app-distribution)
- [x] [Optional] Gather feedback from Beta-testers
- [ ] Publish to the Google Play Store
- [ ] [Optional] Benchmark performance (offline performance also)
- [ ] Upgrade to the latest tools (Java, Android Debug Bridge, Android Studio, Visual Studio Code)

#### To Do (Apple App Store / iOS)

- [ ] Build and test for iOS
- [x] Investigate Apple APPs versus Apple IPAs
- [ ] Investigate Apple App code-signing
- [ ] Set up a CI/CD pipeline
- [ ] [Optional] Test with Firebase Test Lab
- [ ] [Optional] Publish to [Firebase App Distribution](#firebase-app-distribution) or [TestFlight](#testflight)
- [ ] [Optional] Gather feedback from Beta-testers
- [ ] Publish to the App Store
- [ ] [Optional] Benchmark performance (offline performance also)
