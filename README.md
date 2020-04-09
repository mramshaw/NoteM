# Mobile Note-taker

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
* Note can be edited
* Note can be deleted (swipe)

Notes can be filtered by `star` or `flag`.

#### Architecture

* Application constants should be centralized in one place
* Persistent storage should be mediated by a DAO (facilitates easy swapping)
* Application should be [reactive](http://en.wikipedia.org/wiki/Reactive_programming), or - at least - stream-based
* Include a database maintenance option

#### Tests

Follow [Test Plan](TestPlan.md).

Unit tests as follows:

- [x] Tests for singleton DAO

## Reference

Some useful links follow.

#### App Store

App Store Review Guidelines: http://developer.apple.com/app-store/review/

App Store Submissions: http://developer.apple.com/app-store/submissions/

#### Fabric.io

Fabric roadmap: http://get.fabric.io/roadmap

#### Fat APKs

Initial 'fat' release:

    `app-release.apk`            19.7 MB (19,664,349 bytes)

Targetted release:

    `app-arm64-v8a-release.apk`   7.7 MB (8,058,472 bytes)
    `app-armeabi-v7a-release.apk` 7.4 MB (7,743,759 bytes)
    `app-x86_64-release.apk`      7.9 MB (8,223,996 bytes)

These APKs correspond to the following processors:

    ARM    `app-armeabi-v7a-release.apk`
    ARM64  `app-arm64-v8a-release.apk`
    x86_64 `app-x86_64-release.apk`

[It turns out that it is not easy to determine the processor of an Android phone.]

#### Google Play Store

Overview: http://developer.android.com/distribute/best-practices/launch

#### Sentry.io

Sentry documenatation: http://docs.sentry.io/

#### TestFlight

Beta Testing Made Simple with TestFlight: http://developer.apple.com/testflight/

## To Do

- [x] Add links for various deployment options
- [x] Add notes on Android build architectures
- [x] Add a [Test Plan](TestPlan.md)
- [ ] Investigate web drivers for testing
- [ ] Instrument app events to a level of granularity sufficient for debugging & analytics
- [ ] Build and release for web
- [ ] Deploy to GitHub Pages
- [ ] Build and test for Android
- [ ] Investigate Google Tag Manager
- [ ] Investigate Google Play Store ads
- [ ] Publish to the Google Play Store
- [ ] Build and test for iOS
- [ ] [Optional] Publish to TestFlight
- [ ] [Optional] Integrate with Fabric.io (deprecated; Crashlytics recommended) or Sentry.io
- [ ] Publish to the App Store
- [ ] Set up a CI/CD pipeline
- [x] Internationalize everything
- [x] Translations (English)
- [x] Translations (French)
- [ ] Translations (Spanish)
