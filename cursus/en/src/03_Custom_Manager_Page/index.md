---
title: Custom Manager Page
---

You can create and edit your event data on the custom manager page of _Cursus_.
This page contains up to seven tabs where you can manage different parts of the
event bookings.

#### Events

This tab contains a grid view upcoming and past [events](01_Events.md).

#### Participants

This tab contains a grid view of all [participants](02_Participants.md).

#### Trainers

This tab contains a grid view of all [trainers](03_Trainers.md). This tab is
only visible, when the system setting cursus.show_trainer is enabled.

#### Reminders

This tab contains a grid view of all [reminders](04_Reminders.md). It is only
visible for a user that has the cursus_reminders permission enabled. The
permission check is not executed for sudo users.

#### Mail Monitor

This tab contains a grid view of all [monitored mails](05_Mail_Monitor.md) in
the mail queue. It is only visible if the system setting `cursus.queued_email`
is enabled.

#### :fontawesome-solid-puzzle-piece: (Modules)

This tab contains a grid view of all [modules](06_Modules.md). It is only visible
to a user who has enabled the `cursus_modules` permission.

#### :fontawesome-solid-gear: (Settings)

This tab contains a grid view of all [settings](07_Settings.md). It
is only visible for a user that has the `setting` or the `cursus_settings`
permission enabled. The permission check is not executed for sudo users.
