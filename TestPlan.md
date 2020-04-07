# Test Plan

A test plan to verify proper functioning of Notes application

## Initial

After installation, the app should look as follows:

![Installed](images/installed.png)

## Adding Notes

Add four notes as shown:

![Set up](images/set_up.png)

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

Add some more notes. Verify scrolling works correctly.

## Updating Notes

Update some notes. Verify updating notes works correctly.

## Deleting Notes (Clean-up)

Delete all four notes (swipe right-to-left).

The app should now be back in its ___as installed___ state:

![As installed](images/as_installed.png)

## Monitoring

Verify that there have been no crash reports in Fabric/Sentry.

#### Ongoing

Monitor Fabric/Sentry on an ongoing basis for crash reports.

#### Fabric/Sentry setup

The project should be added to Fabric/Sentry as early as possible to verify proper function.

[Bug/Crash reports tend to be intermittent and/or sporadic, so best to have strong confidence in their reporting.]

#### Debugging/Staging/Production

It is sometimes possible to separate these (bug/crash reports when developing are not normally serious).

But for practical reasons it is probably best to always have this enabled.

#### Release tagging

In order to be better able to ___triage___ bug/crash reports, robust release versions (and tagging) shoudl be employed.

## To Do

- [ ] Automate this testing
- [ ] Incorporate into CI/CD pipeline
