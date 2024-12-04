---
title: CursusEventList
---

This snippet displays Cursus events in a list.

## Properties

It uses the following snippet properties:

| Property           | Description                                                                                                                                                                  | Default               |
|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------|
| active             | Show only active events and event dates.                                                                                                                                     | 1 (Yes)               |
| ajax               | If this option is set, the snippet output will be directly output as JSON result to the browser when the page is requested with the same value in the ajax request property. | 0 (No)                |
| contexts           | Comma separated list of context keys to filter the displayed events.                                                                                                         | -                     |
| daterangeFormat    | Format of the daterange displayed in an event.                                                                                                                               | -                     |
| daterangeSeparator | Separator in the daterange displayed in an event.                                                                                                                            | -                     |
| durationParts      | Number of detail parts of the event duration output.                                                                                                                         | 1                     |
| emptyTpl           | Name of a chunk that contains the template for an empty list of events.                                                                                                      | tplCursusEventEmpty   |
| end                | The end date to filter the displayed events. Must contain a [supported date and time format](https://www.php.net/manual/de/datetime.formats.php).                            | today +1 month 0:00   |
| groupby            | xPDO group by clause to filter the events.                                                                                                                                   | -                     |
| having             | JSON encoded xPDO having clause to filter the events.                                                                                                                        | -                     |
| latestRegistration | The latest registration for each event. Can be overridden on event base, if the system setting "show_latest_registration" is enabled.                                        | -                     |
| limit              | Limit the number of events in the result. Use "0" for unlimited events.                                                                                                      | 20                    |
| locale             | The locale for the displayed formatted date. Defaults to the current system/context locale setting.                                                                          | -                     |
| offset             | The offset of events to skip.                                                                                                                                                | -                     |
| outputSeparator    | An optional string to separate each tpl instance.                                                                                                                            | -                     |
| published          | Publication status of the event. 0: unpublished, 1: published, 2: both.                                                                                                      | 1                     |
| sortby             | Field name according to which the events are sorted.                                                                                                                         | EventDate.startdate   |
| sortdir            | Direction in which the events are sorted.                                                                                                                                    | ASC                   |
| start              | The start date to filter the displayed events. Must contain a [supported date and time format](https://www.php.net/manual/de/datetime.formats.php).                          | today 0:00            |
| toPlaceholder      | If this option is set, the snippet result will be assigned to this placeholder instead of outputting it directly.                                                            | -                     |
| totalVar           | The key of a placeholder that indicates the total number of events.                                                                                                          | cursuslist.total      |
| tpl                | Name of a chunk that contains the template for an event.                                                                                                                     | tplCursusEventRow     |
| where              | JSON encoded xPDO where clause to filter the events.                                                                                                                         | -                     |
| wrapperTpl         | Name of a chunk that contains the wrapper template for all events.                                                                                                           | tplCursusEventWrapper |

## Placeholders

The following placeholders are available in the different (default) chunks.
Also, each snippet property will be set as placeholder in each template chunk,
i.e. a snippet call ```[[!CursusEventDetail? &subtitle=`whatever`]]``` will fill
the placeholder subtitle in each used chunk with the value `whatever`.

**CAUTION:** The default template chunks for both snippets are overwritten
during each package update, so please rename the chunks before editing them.

### tplCursusEventRow

| Placeholder            | Description                                                                                                                                                                                                                                                                                 |
|------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| allday                 | Contains 1 if the event is an all day event (otherwise 0).                                                                                                                                                                                                                                  |
| bookable               | Contains 1 if the event is bookable (otherwise 0).                                                                                                                                                                                                                                          |
| bookable_until         | The bookable until date of the event formatted in ISO 8601 (could be formatted i.e. with ```[[+bookable_until:strtotime:date=`%a. %d.%m.%Y`]]```).                                                                                                                                          |
| calendar_alias         | calendar alias of the event.                                                                                                                                                                                                                                                                | kurse                                                                            | 
| calendar_id            | calendar id of the event.                                                                                                                                                                                                                                                                   | 8                                                                                | 
| category_aliases       | Comma separated list of category aliases of the event.                                                                                                                                                                                                                                      |
| category_ids           | Comma separated list of category ids of the event.                                                                                                                                                                                                                                          |
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
| repeating_id           | The id of the Agenda event date of the event.                                                                                                                                                                                                                                               |
| resource               | The id of a linked resource for the event.                                                                                                                                                                                                                                                  |
| resource_id            | The id of a linked resource for the event.                                                                                                                                                                                                                                                  |
| startdate              | The start date of the event formatted in ISO 8601 (could be formatted i.e. with ```[[+startdate:strtotime:date=`%a. %d.%m.%Y`]]```).                                                                                                                                                        |
| title                  | The title of the event.                                                                                                                                                                                                                                                                     |
| trainers               | Comma separated list of trainer ids of the event.                                                                                                                                                                                                                                           |
| week                   | The year and the calendar week of the event separated by '-'.                                                                                                                                                                                                                               |
| weekday                | The Number of the weekday of the event. Monday = 1.                                                                                                                                                                                                                                         |

[Extended fields](../07_Extended_Fields.md) are available as placeholder with
the prefix `extended_` in the event row template.

If the `tpl` property contains a not found chunk, all possible placeholders are
displayed with print_r.

### tplCursusEventWrapper

| Placeholder | Description                                                                                 |
|-------------|---------------------------------------------------------------------------------------------|
| count       | Count of the events filtered by the snippet properties (without limit/offset)               |
| output      | All events collected by the snippet separated by the string in the outputSeparator property |

If the `wrapperTpl` property contains a not found chunk, all possible
placeholders are displayed in the print_r format.

### tplCursusEventEmpty

Only the current script properties are available as placeholders.

If the `emptyTpl` property contains a not found chunk, all possible placeholders
are displayed with print_r.

## Range placeholder format

The `range` placeholder could be formatted with the lexicon entries
`agenda.php_format_daterange` and `agenda.php_format_separator` or the snippet
properties `daterangeFormat` and `daterangeSeparator`. The format string has to
use exactly 7 parts separated by `|`. The default english lexicon entry is
`j.| F |Y|, |g|:i a|`.

The daterrange is formatted with the following rules:

- If both dates are different and the hour/minute of start and end is 0, parts 4-7 are removed from start and end date.
- If both dates are different and the hour/minute of start and end is 0 and year of start and end is equal, parts 4-7 are removed from start and end date and part 3 is removed from start date.
- If both dates are different and the hour/minute of start and end is 0 and year and month of start and end are equal, parts 4-7 are removed from start and end date and parts 2-3 are removed from start date.
- If both dates are different and the hour/minute of start and end is 0 and year, month and day of start and end are equal, parts 4-7 are removed from start and end date and parts 1-3 are removed from start date.
- If both dates are different and the hour/minute of start and end is not 0 and one detail of year, month and day of start and end is not equal, all parts are used in the start and end date.
- If both dates are different and the hour/minute of start and the hour of end is 0 and all details of year, month and day of start and end are equal, parts 4-7 are removed from start date.
- If both dates are different and the hour or minute of start or the hour of end not 0 and all details of year, month and day of start and end are equal, part 7 is removed from start date.
- If both dates are equal and the hour/minute of start is 0, part 4-7 is removed from the start date and separator and end date are removed.
- If both dates are equal and the hour/minute of start is not 0, separator and end date are removed.