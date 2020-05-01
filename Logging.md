# Logging

Investigate the details to be logged to facilitate debugging/analytics

## Overview

As the following diagram shows, there are a number of areas to consider:

![Event Reporting](images/Event_Reporting.png)

Broadly speaking (ignoring historical details such `First Launch Time`,
`Cellular Service Provider`, etc) these fall into three categories:

1. [User](#user)
2. [Device](#device)
3. [Application](#application)

These categories overlap to a certain extent (this is not shown on the diagram).

## User

Mainly useful for demographic/analytic/marketing purposes, but also important
for legal purposes:

* Age (or Age Group)
* Gender
* Residence (Country, region, principality)
* Nationality

Mostly these details will be from one, or a combination, of:

1. Apple App Store
2. Google Play Store
3. Identity Provider

While the user's physical location while using the app (which neither confirms
residence nor nationality) can largely be determined from the transmission location
via I.P. Blocks, demographic information requires that the user sign-in to our app.

[This, of course, should require ___informed consent___. Consent is the __C__
 in the __POTOMAC__ model; with the others being Privacy, Ownership,
 Traceability, Objectivity, Misuse, and Accuracy. As it is generally a requirement
 to publish a ___Privacy Policy___, it is a good idea  to carefully consider privacy
 concerns, as laws will probably only increase.]

Without these user details, traditional __Audience Identification__ (sometimes
known as __Market Segmentation__) may well prove difficult. Of course, it will
still be possible to identify audiences due to in-app engagement (but this requires
some thought as to the details to be recorded to enable this).

[Enough details must also be tracked to enable __Cohort Identification__, or
 more specifically ___Retention___, if this is desired.]

## Device

Mostly useful for testing/debugging purposes, but also of interest for
demographic/analytic/marketing purposes:

* Device Type
* Device Model
* Device Processor
* Operating System (Android, iOS)
* Operating System version
* Language & Locale (locale does not have to be present)

Device Type / Device Processor / Operating System are necessary to
isolate the particular app build that may be problematic.

Language (English, French) is a user setting, but is listed here as a
device characteristic. Locale may not be present, but is generally a
sub-category of language (as in __en\_US__, __fr\_FR__, etc).

Determining the user's preferred language setting may be somewhat more
complicated without a user sign-in, as this seems to be how this datum
is normally obtained.

#### Android

Android devices have a more limited form-factor, but many more suppliers
(each of which may trail Official Android releases by quite some effort).

Android devices generally fall into three broad processor types [it is
non-trivial to determine the processor type from the model, but this is
something that Google Play Store reporting probably handles].

#### iOS

iOS devices come in a wide variety of form factors, but are generally a
lot more restricted in terms of generally being up-to-date with the
latest iOS release (but might trail by a release or two).

## Application

Mainly of interest for debugging/maintenance purposes, but also of
interest for demographic/analytic/marketing purposes:

* App Version
* App Environment
* App Build (OS, processor type, etc)

These are all critical for triage of bug/crash reports (generally,
bug/crash reports that originate from a `development` environment
are not investigated. Staging, QA and Production environments are
progressively more critical).

This would also be the category where we might introduce app-specific
event details (highly-active or engaged users, for example) that are
of particular interest for future marketing or retargeting efforts
(these remain to be defined).

## To Do

- [ ] Add more details as they are discovered
- [ ] Add more application event details as they are defined
- [ ] How to determine user's preferred language without a sign-in?
- [ ] Can Apple App Store / Google Play Store be relied on for legal requirements?
