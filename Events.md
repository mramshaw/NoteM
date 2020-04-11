# Events

A list of events to be logged for debugging/analytics purposes

## Rationale

Even though this is a relatively small application, the number
of events (user and otherwise) to be logged is really surprising.

[Presently ___26___ (although all will not be logged) and this
 is without any attempt to log hardware, language or demographic
 characteristics.]

This document is an attempt to list all log events. While it may
prove unnecessary to log all of them, the first step in deciding
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
the app release version (according to __SemVer__ principles).

[Apple App Store/Google Play Store tracks installs/uninstalls
 to some extent, but it's a good idea to log them anyway - as
 downloads do not have to exactly match installations, and logging
 uninstalls is probably just a good practice anyway. Any user
 demographics will be from either App Store reporting or Play
 Store reporting. Still, it would probably be useful to track
 language, as this might be used to justify a professional
 translation effort.]

## Session

1. Session initiated
2. <del>Session abandoned</del>

[It will be somewhat difficult to determine __2__ without
 defining some definition of a timeout period. This is
 probably more of a __dashboard__ responsibility.]

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
4. Database vacuumed
5. Notes table deallocated
6. Database deallocated

At present there are no plans for application update, so __3__
is only listed for methodology purposes.

Probably only __4__ needs to be logged, as the others are part
of application installation and uninstallation, respectively.

## To Do

- [ ] Update this document as new Events are discovered