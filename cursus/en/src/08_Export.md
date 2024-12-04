---
title: Export
---

## Events

To export the events the user has to get the `cursus_export_events` permission.
After that an export button is displayed at the top left above events grid in
the [events tab](03_Custom_Manager_Page/01_Events.md) of the custom manager
page. The export will contain the events data and a comma separated list of the
participants.

## Participants

To export the participants the user has to get the `cursus_export_participants`
permission. After that an export button is displayed right of the create
participant button in the [participants
tab](03_Custom_Manager_Page/02_Participants.md) of the custom manager page. The
export will contain the participants' data.

## Trainers

To export the trainers the user has to get the `cursus_export_trainers`
permission. After that an export button is displayed right of the create trainer
button in the [trainerts tab](03_Custom_Manager_Page/03_Trainers.md) of the
custom manager page. The export will contain the trainers' data.

## Format

The export and import format can be set with the `cursus.import_export_type`
system setting. The supported formats are `csv`, `excel` and `yaml`. The default
format is `excel`.

## Custom Format

The export methods can be overridden in a [Cursus
module](03_Custom_Manager_Page/06_Modules.md) with extended methods.
