# Test Plan

A test plan to verify proper functioning of Notes application

## Contents

The contents are as follows:

* [Initial app](#initial-app)
* [Adding Notes](#adding-notes)
    * [Add note validation](#add-note-validation)
* [Tooltips](#tooltips)
* [Filtering](#filtering)
    * [Star Filter](#star-filter)
    * [Star and Flag Filter](#star-and-flag-filter)
    * [Flag Filter](#flag-filter)
    * [No filtering](#no-filtering)
* [Scrolling](#scrolling)
* [Updating Notes](#updating-notes)
    * [Update note validation](#update-note-validation)
* [Deleting Notes](#deleting-notes)
* [Menu items](#menu-items)
    * [About Notes](#about-notes)
    * [Clean up database](#clean-up-database)
* [Monitoring](#monitoring)
    * [Ongoing](#ongoing)
    * [Crashlytics/Sentry setup](#crashlyticssentry-setup)
    * [Debugging/Staging/Production](#debuggingstagingproduction)
    * [Release tagging](#release-tagging)
* [To Do](#to-do)

## Initial app

After installation, the app should look as follows:

![Installed](images/installed.png)

## Adding Notes

Add four notes as shown:

![Set up](images/set_up.png)

#### Add note validation

Verify that a note must have ___either___ a title ___or___ a body.

## Tooltips

![Tool tips](images/tooltips.png)

Long press the following items as shown:

1. Star filter
2. Flag filter
3. Note Star
4. Note Flag

Verify that an appropriate tooltip appears.

## Filtering

Flag/Star the individual notes as shown:

![Flagged/Starred](images/flagged_starred.png)

#### Star Filter

Select the 'star' filter. Verify the results are as shown:

![Starred](images/starred.png)

#### Star and Flag Filter

Select the 'flag' filter. Verify the results are as shown:

![Starred](images/starred_and_flagged.png)

#### Flag Filter

Deselect the 'star' filter. Verify the results are as shown:

![Starred](images/flagged.png)

#### No filtering

Deselect the 'flag' filter. Verify the results are as shown:

![No filter](images/no_filter.png)

## Scrolling

Add some more notes.

Verify scrolling works correctly.

## Updating Notes

Update some notes (double-tap the note body to switch to the Update Note screen).

Verify updating notes works correctly.

#### Update note validation

Verify that a note must have ___either___ a title ___or___ a body.

## Deleting Notes

To clean up, delete all four notes (swipe right-to-left).

The app should now be back in its ___as installed___ state:

![As installed](images/as_installed.png)

## Menu items

Open the menu and verify the following items.

#### About Notes

Select the 'About Notes' option.

Verify the about popup shows.

Close the popup.

#### Clean up database

Select the 'Clean up database' option.

Verify that it doesn't crash.

## Monitoring

Verify that there have been no crash reports in Crashlytics/Sentry.

#### Ongoing

Monitor Crashlytics/Sentry on an ongoing basis for crash reports.

#### Crashlytics/Sentry setup

The project should be added to Crashlytics/Sentry as early as possible to verify proper function.

[Bug/Crash reports tend to be intermittent and/or sporadic, so best to have strong confidence in their reporting.]

#### Debugging/Staging/Production

It is sometimes possible to separate these (bug/crash reports when developing are not normally serious).

But for practical reasons it is probably best to always have bug/crash reporting enabled during development.

#### Release tagging

In order to be better able to ___triage___ bug/crash reports, robust release versions (and tagging) should be employed.

[SemVer](http://semver.org/) release versions should be used for each release.

## To Do

- [ ] Automate this testing
- [ ] Incorporate into CI/CD pipeline
