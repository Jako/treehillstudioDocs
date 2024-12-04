---
title: Quick Start
---

To implement Cursus on your website, you must first set up
[Agenda](https://docs.treehillstudio.de/en/agenda/). The simplest Agenda
configuration would be a calendar with a repeating event.

!!! note "Agenda events have to be repeating events"

    Keep in mind that in Cursus you can only book repeating events from Agenda. You
    are completely free to choose the type of recurrence. It can be a calculated or
    a customized recurrence. Single repeating events are possible.

Next you need to set up Cursus and fill the system setting `cursus.event_where`
with a JSON encoded xPDO where clause to filter the Agenda events, i.e.
`{"Calendar.alias:=": "Courses"}`.

Then you have to add Cursus to the
[Modules](https://docs.treehillstudio.de/en/agenda/02_Custom_Manager_Page/07_Modules/)
of Agenda by entering `cursus` as the module name. After a reload of the Agenda
custom manager page, the Agenda Event window will contain the Cursus fields
`Min. participants`, `Max. Participants`, `Price`, `Trainer` and `Auto Publish`
and the event grid contains the columns `Min`, `Max`, `Price` and `Auto
Publish`.

Now the Agenda repeat events appear in the [Cursus event
grid](03_Custom_Manager_Page/01_Events.md), and you can assign participants to
these events in the backend.

To display the events in the frontend, you have to add some Agenda and/or
[Cursus snippets](05_Snippets/index.md). To book those event dates, you have to
implement a booking form with the Cursus hooks.

Cursus is very flexible and can be customized a lot with extended fields, system
settings and permissions. Those options are often inactive and have to be
enabled. So please check the documentation where you can enable i.e.
[Trainers](03_Custom_Manager_Page/03_Trainers.md),
[Reminders](03_Custom_Manager_Page/04_Reminders.md) and the [Mail
Queue](03_Custom_Manager_Page/05_Mail_Monitor.md).

If you miss a custom option please send a mail to
[treehillstudio-support@modmore.com](mailto:treehillstudio-support@modmore.com).
Hopefully we can show you how to implement the option, or we can add that option
to a future release. If it is urgent, we also offer custom coding.
