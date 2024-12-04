---
title: CursusEventGet
---

This hook allows to fill FormIt values by Cursus events.

The event is retrieved with the event ID or the repeat ID, if the event ID is
not set. If no event can be retrieved, the hook returns false

## FormIt Hook Properties

It uses the following hook properties:

| Property               | Description                                                                                         | Default |
|------------------------|-----------------------------------------------------------------------------------------------------|---------|
| cursusAgendaEvent      | ID of one Agenda event to load into FormIt.                                                         | 0       |
| cursusContexts         | Comma separated list of context keys to filter the loaded events.                                   |         |
| cursusEvent            | ID of one Cursus event to load into FormIt.                                                         | 0       |
| cursusHaving           | JSON encoded xPDO having clause to filter the loaded events.                                        |         |
| cursusHistorical       | Historical status to filter the loaded events. 0: past events, 1: future events, 'both': all events | 'both'  |
| cursusLocale           | The locale for the displayed formatted date. Defaults to the current system/context locale setting. | -       |
| cursusNotFoundRedirect | ID of the MODX resource the user is redirected to, if the event resource is not found.              | 0       |
| cursusOwnEvent         | Load only own events (created by the current user) into FormIt.                                     | false   |
| cursusPublished        | Publication status to filter the loaded events. 0: unpublished, 1: published, 2: both               | 0       |
| cursusWhere            | JSON encoded xPDO where clause to filter the loaded events.                                         |         |

## Hook fields

The following FormIt fields are set by the loaded Cursus event in the hook:

| Field           | Description                                                                                                                                                |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| active          | The active status of the loaded event.                                                                                                                     |
| allday          | The all day status of the loaded event.                                                                                                                    |
| calendar        | The alias of the calendar of the loaded event.                                                                                                             |
| calendar_id     | The id of the calendar of the loaded event.                                                                                                                |
| category        | The aliases of the categories of the loaded event.                                                                                                         |
| content         | The content of the loaded event.                                                                                                                           |
| context_key     | The context key of the loaded event.                                                                                                                       |
| description     | The description of the loaded event.                                                                                                                       |
| enddate         | The enddate of the loaded event (or the loaded repeating event).                                                                                           |
| id              | The id of the loaded event.                                                                                                                                |
| images          | An array of all images of the loaded event. Contains path, basepath, baseurl, title and description of each image,                                         |
| location        | The alias of the location of the loaded event.                                                                                                             |
| location_id     | The id of the location of the loaded event.                                                                                                                |
| repeat_enddate  | The enddate of the repeats of the loaded event.                                                                                                            |
| repeat_interval | The repeat interval of the loaded event.                                                                                                                   |
| repeat_on       | The repeat weekdays of the loaded event, when the repeat type is weekly                                                                                    |
| repeat_ordinal  | The repeat ordinal of the loaded event, when the repeat type is monthly by weekday                                                                         |
| repeat_type     | The repeat type of the loaded event. (1 = daily , 2 = weekly, 3 = monthly, 4 = yearly, 5 = montly by weekday )                                             |
| repeat_weekday  | The repeat weekday of the loaded event, when the repeat type is weekly                                                                                     |
| repeating       | The repeating status of the loaded event.                                                                                                                  |
| repeating_id    | The id of the loaded repeating event.                                                                                                                      |
| resource        | An array of some values of the linked resource of the loaded event. Contains id, pagetitle, longtitle, content and all template variables of the resource. |
| resource_id     | The id of the linked resource of the loaded event.                                                                                                         |
| startdate       | The startdate of the loaded event (or the loaded repeating event).                                                                                         |
| title           | The title of the loaded event.                                                                                                                             |

[Extended fields](../07_Extended_Fields.md) are set for FormIt with the prefix `extended_`
in the hook.
