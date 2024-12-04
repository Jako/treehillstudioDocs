---
title: CursusEventDetail
---

This snippet displays one Cursus event.

## Properties

It uses the following snippet properties:

| Property           | Description                                                                                                                                                                       | Default              |
|--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|
| active             | Show only active events and event dates.                                                                                                                                          | 1 (Yes)              |
| agenda_event       | ID of the agenda event whose data is displayed.                                                                                                                                   | -                    |
| ajax               | If this option is set, the snippet output will be directly returned to the browser as a JSON result when the page is requested with the same value in the ajax request parameter. | 0 (No)               |
| allowedRequestKeys | Comma-separated list of request keys, that could be used to filter the displayed events. Defaults to all allowed.                                                                 | -                    |
| contexts           | Comma separated list of context keys to filter the displayed events.                                                                                                              | -                    |
| daterangeFormat    | Format of the daterange displayed in an event.                                                                                                                                    | -                    |
| daterangeSeparator | Separator in the daterange displayed in an event.                                                                                                                                 | -                    |
| detailId           | ID of a resource containing an AgendaDetail/CursusList snippet call.                                                                                                              | 1                    |
| durationParts      | Number of detail parts of the event duration output.                                                                                                                              | 1                    |
| emptyTpl           | Name of a chunk that contains the template for an empty list of events.                                                                                                           | tplCursusEventEmpty  |
| event              | ID of the agenda event date whose data is displayed.                                                                                                                              | -                    |
| having             | JSON encoded xPDO having clause to filter the events.                                                                                                                             | -                    |
| listId             | ID of a resource containing an AgendaList/CursusList snippet call.                                                                                                                | -                    |
| locale             | The locale for the displayed formatted date. Defaults to the current system/context locale setting.                                                                               | -                    |
| published          | Publication status of the event. 0: unpublished, 1: published, 2: both.                                                                                                           | 1                    |
| toPlaceholder      | If this option is set, the snippet result will be assigned to this placeholder instead of outputting it directly.                                                                 | -                    |
| tpl                | Name of a chunk that contains the template for an event.                                                                                                                          | tplCursusEventDetail |
| where              | JSON encoded xPDO where clause to filter the events.                                                                                                                              | -                    |

## Placeholders

The following placeholders are available in the different (default) chunks.
Also, each snippet property will be set as placeholder in each template chunk,
i.e. a snippet call ```[[!CursusEventDetail? &subtitle=`whatever`]]``` will fill
the placeholder subtitle in each used chunk with the value `whatever`.

**CAUTION:** The default template chunks for both snippets are overwritten
during each package update, so please rename the chunks before editing them.

### tplCursusEventDetail

| Placeholder            | Description                                                                                                                                                                                                                                                                                 |                                                                                  |
|------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|
| agenda_event_date_id   | The id of the Agenda event date of the event.                                                                                                                                                                                                                                               |                                                                                  | 
| allday                 | Contains 1 if the event is an all day event (otherwise 0).                                                                                                                                                                                                                                  | 0                                                                                | 
| bookable               | Contains 1 if the event is bookable (otherwise 0).                                                                                                                                                                                                                                          | 1                                                                                | 
| bookable_until         | The bookable until date of the event formatted in ISO 8601 (could be formatted i.e. with ```[[+bookable_until:strtotime:date=`%a. %d.%m.%Y`]]```).                                                                                                                                          | 2024-02-27 10:00:00                                                              | 
| calendar_alias         | calendar alias of the event.                                                                                                                                                                                                                                                                | kurse                                                                            | 
| calendar_id            | calendar id of the event.                                                                                                                                                                                                                                                                   | 8                                                                                | 
| category_aliases       | Comma separated list of category aliases of the event.                                                                                                                                                                                                                                      | &#91;&quot;bewegung&quot;,&quot;familienkurs&quot;,&quot;kindergarten&quot;&#93; | 
| category_ids           | Comma separated list of category ids of the event.                                                                                                                                                                                                                                          | 6,10,16                                                                          | 
| content                | The content of the event.                                                                                                                                                                                                                                                                   |
| count_current          | The number of participants assigned to the event.                                                                                                                                                                                                                                           |
| count_current_booked   | The number of participants with booked status assigned to the event.                                                                                                                                                                                                                        |
| count_current_reserved | The number of participants with reserved status assigned to the event.                                                                                                                                                                                                                      |
| description            | The description of the event.                                                                                                                                                                                                                                                               |
| detail_url             | The url that shows the event detail. Will be generated with the system/context setting `cursus.detail_id`. This resource should contain an AgendaDetail snippet call.                                                                                                                       |
| duration               | The formatted duration of the event. The details of the duration could be set with the `durationParts` snippet property.                                                                                                                                                                    |
| duration_hours         | The formatted hours of the duration of the event.                                                                                                                                                                                                                                           |
| duration_minutes       | The duration of the event in minutes.                                                                                                                                                                                                                                                       |
| enddate                | The start date of the event formatted in ISO 8601 (could be formatted i.e. with ```[[+enddate:strtotime:date=`%a. %d.%m.%Y`]]```).                                                                                                                                                          |
| event_participants     | Comma separated list of participant ids of the event.                                                                                                                                                                                                                                       |
| idx                    | The number of the event starting with 1.                                                                                                                                                                                                                                                    |
| location               | The id of a Agenda location for the event.                                                                                                                                                                                                                                                  |
| location_id            | The id of a Agenda location for the event.                                                                                                                                                                                                                                                  |
| max_participants       | The maximum number of participants that can be assigned to the event.                                                                                                                                                                                                                       |
| maximum_booked_reached | Contains 1 if the maximum number of booked participants has been reached (otherwise 0).                                                                                                                                                                                                     |
| maximum_reached        | Contains 1 if the maximum number of participants has been reached (otherwise 0).                                                                                                                                                                                                            |
| min_participants       | The minimum number of participants that has to be assigned to the event until it takes place.                                                                                                                                                                                               |
| minimum_booked_reached | Contains 1 if the minimum number of booked participants has been reached (otherwise 0).                                                                                                                                                                                                     |
| minimum_reached        | Contains 1 if the minimum number of participants has been reached (otherwise 0).                                                                                                                                                                                                            |
| price                  | The price of the event.                                                                                                                                                                                                                                                                     |
| published              | The publish state of the event.                                                                                                                                                                                                                                                             |
| range                  | The formatted date range of the event. The format is defined with the lexicon entries `agenda.php_format_daterange` and `agenda.php_format_separator` and could be overridden by the `daterangeFormat` snippet property. The [format rules](#range-placeholder-format) are described below. |
| remaining              | The number of the remaining participants that can be assigned to the event.                                                                                                                                                                                                                 |
| remaining_booked       | The number of the remaining bookable participants that can be assigned to the event.                                                                                                                                                                                                        |
| resource               | The id of a linked resource for the event.                                                                                                                                                                                                                                                  |
| resource_id            | The id of a linked resource for the event.                                                                                                                                                                                                                                                  |
| startdate              | The start date of the event formatted in ISO 8601 (could be formatted i.e. with ```[[+startdate:strtotime:date=`%a. %d.%m.%Y`]]```).                                                                                                                                                        |
| title                  | The title of the event.                                                                                                                                                                                                                                                                     |
| trainers               | Comma separated list of trainer ids of the event.                                                                                                                                                                                                                                           |
| week                   | The year and the calendar week of the event separated by '-'.                                                                                                                                                                                                                               |
| weekday                | The Number of the weekday of the event. Monday = 1.                                                                                                                                                                                                                                         |

[Extended fields](../07_Extended_Fields.md) are available as placeholder with
the prefix `extended_` in the event template.

If the `tpl` property contains a not found chunk, all possible placeholders are
displayed with print_r.

### tplCursusEventEmpty

Only the current script properties are available as placeholders.

If the `emptyTpl` property contains a not found chunk, all possible placeholders
are displayed with print_r.
