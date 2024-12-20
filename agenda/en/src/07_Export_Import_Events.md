---
title: Export/Import Events
---

The export and import of events were introduced with Agenda 1.5.0.

To export or import the events the user has to get the `agenda_export` or
`agend_import` permissions. After that an export and import button is displayed
right of the create event button in the events tab of the custom manager page.

## Format

The export and import format can be set with the `agenda.import_export_type`
system setting. The supported formats are `csv`, `excel` and `yaml`. The default
format is `csv`.

The default export method will create a list of events for repeating events. If
the repeating event does not have an identifier for the main event (i.e. by a
field in agenda.extended_event_fields), it is difficult to reimport those
events. During an import, events with the same event data (except start and end
dates) are treated as a repeating event. The repeat is set to user defined and
the repeat data is set for each recurrence.

## Custom Format

The import/export methods can be overridden in a [Agenda
module](02_Custom_Manager_Page/07_Modules.md) with extended methods.
