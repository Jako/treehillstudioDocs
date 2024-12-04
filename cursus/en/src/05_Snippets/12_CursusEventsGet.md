---
title: CursusEventsGet
---

This hook allows to set Cursus events values with FormIt.

## FormIt Hook Properties

It uses the following hook properties:

| Property               | Description                                                                                         | Default |
|------------------------|-----------------------------------------------------------------------------------------------------|---------|
| cursusAgendaEvents     | JSON encoded array of IDs of Agenda events to load into FormIt.                                     |         |
| cursusContexts         | Comma separated list of context keys to filter the loaded events.                                   |         |
| cursusEvents           | JSON encoded array of IDs of Cursus events to load into FormIt.                                    |         |
| cursusHaving           | JSON encoded xPDO having clause to filter the loaded events.                                        |         |
| cursusLocale           | The locale for the displayed formatted date. Defaults to the current system/context locale setting. | -       |
| cursusNotFoundRedirect | ID of the MODX resource the user is redirected to, if the event resource is not found.              | 0       |
| cursusOwnEvent         | Load only own events (created by the current user) into FormIt.                                     | false   |
| cursusPublished        | Publication status to filter the loaded events. 0: unpublished, 1: published, 2: both               | 0       |
| cursusWhere            | JSON encoded xPDO where clause to filter the loaded events.                                         |         |

## Hook fields

The following FormIt fields are set by the loaded Cursus event in the hook:

| Field            | Description                                                              |
|------------------|--------------------------------------------------------------------------|
| agenda_event_ids | JSON encoded array of IDs of Agenda events.                              |
| event_ids        | JSON encoded array of IDs of Cursus events.                              |
| events_values    | An array of all events. It can be used in hooks running after this hook. |
