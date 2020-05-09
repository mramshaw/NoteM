# Events

A list of events to be logged for debugging/analytics purposes

[When an app crashes, tracing the logged events can give some
 useful ___context___ to the actual problem. Generally, Crash
 Reporting services merely provide stack-traces (although some
 ___breadcrumbs___ may also be supplied).]

## Rationale

Even though this is a relatively small application, the number
of events (user and otherwise) to be logged is surprising.

[Presently ___31___ (although not all will be logged) and this
 is without any consideration of hardware/language/demographic
 characteristics - these are investigated in [Logging](Logging.md).]

This document is an attempt to list all events. While it may
be unnecessary to log all of them, the first step in deciding
what level of granularity is needed for debugging/logging/analytics
purposes is to list all of the possible events to be logged.

No particular methodology was followed, however it proved useful
to think in terms of life-cycle events.

## Application

1. Application installed
2. Application updated
3. Application uninstalled

Too many applications fail to consider the second possibility,
which generally makes debugging (and even bug triage) quite
difficult, as the application __release version__ (and also
the __Application Environment__ - as in, Testing, Staging, QA,
Production) is pretty much critical to do either of these things
effectively.

Accordingly, all of the of the event logging should include
the app release version (according to [SemVer](http://semver.org)
principles).

[Apple App Store/Google Play Store tracks installs/uninstalls
 to some extent, but it's a good idea to log them anyway - as
 downloads do not have to exactly match installations, and logging
 uninstalls is probably just a good practice anyway. Any user
 demographics will be from either App Store reporting or Play
 Store reporting. Still, it would be useful to track language
 (and locale), as these might be useful for justifying
 a professional translation effort.]

## Session

1. Session initiated
2. <del>Session ended</del>
3. <del>Session abandoned</del>

[Due to the way apps work, determining the difference between
 __2__ and __3__ is problematic. Likewise determining length
 of session is problematic. Assume __1__ will only be reported
 after 10 seconds (which is a good margin to allow for actual
 app engagement while ignoring false-opens) and that the
 session times-out after 30 minutes of inactivity (it doesn't
 seem as if closing the app affects this). These session
 definitions are perhaps more of a __dashboard__ responsibility.]

## Page Views

1. Home page viewed
2. Update page viewed
3. Menu viewed
4. About popup viewed

## CRUD (Actions)

1. Note created
2. Note updated
3. Note deleted

It is possible to return from the Update page without
updating a Note so __2__ here does not have to correspond
to __2__ above. Likewise it is possible to update a Note
more than once on the Update page.

## Flagging/Starring

[These actions occur on the __Home__ page rather than
 the __Update Note__ page, so they need to be considered
 as events in their own right.]

1. Note flagged
1. Note un-flagged
2. Note starred
2. Note un-starred

[Flagging or starring a Note doesn't affect the Note
 presentation order, however it is possible to filter
 Notes based upon whether they have been flagged and/or
 starred.]

## Validation

1. Add note validation failed
2. Edit note validation failed

[It seems a little excessive to be reporting on these.]

## Filtering

1. __Star__ selected
1. __Star__ deselected
1. __Flag__ selected
1. __Flag__ deselected

## Scrolling

1. Scroll list of notes up
2. Scroll list of notes down

[It's probably not possible or useful to report on either of these.]

## Storage

1. Database created and initialized
2. Notes table created
3. Notes table updated (app update)
4. Database maintenance performed
5. Notes table deallocated
6. Database deallocated

At present there are no plans for application update, so __3__
is only listed for methodology purposes.

Probably only __4__ needs to be logged, as the others are part
of application installation and uninstallation, respectively.

## Timing

In order to maintain a consistent approach, in all cases the
event will be logged just __before__ the actual event takes
place. This may create problems in the unlikely case that the
event ___fails___ however logging the ___intent___ of the action
should create the clearest possible audit trail.

## To Do

- [ ] Update this document as new Events are discovered
