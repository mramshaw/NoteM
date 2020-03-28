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
2. Sync'ing with the cloud (optionally)

Ideally should NOT be dependent upon a device's Cloud account.

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

#### Tests

- [x] Tests for singleton DAO

## Reference

Some useful links follow.

#### App Store

App Store Review Guidelines: http://developer.apple.com/app-store/review/

App Store Submissions: http://developer.apple.com/app-store/submissions/

#### Google Play Store

Overview: http://developer.android.com/distribute/best-practices/launch

#### TestFlight

Beta Testing Made Simple with TestFlight: http://developer.apple.com/testflight/

## To Do

- [x] Add links for various deployment options
- [ ] Build and release for web
- [ ] Deploy to GitHub Pages
- [ ] Build and test for Android
- [ ] Publish to the Google Play Store
- [ ] Build and test for iOS
- [ ] [Optional] Publish to TestFlight
- [ ] Publish to the App Store
- [ ] Set up a CI/CD pipeline
- [x] Internationalize everything
- [x] Translations (French)
- [ ] Translations (Spanish)
