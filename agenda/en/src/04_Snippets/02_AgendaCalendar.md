---
title: AgendaCalendar
---

This snippet displays events in a list separared into intervals. The
snippet was introduced with Agenda 1.1.0.

## Properties

It uses the following snippet properties:

| Property           | Description                                                                                                                                                                        | Default                |
|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------|
| active             | **Since 1.6.3** If this option is disabled, the active status of an event is not regarded.                                                                                         | 1 (Yes)                |
| ajax               | **Since 1.4.0** If set, the snippet output will be directly returned to the browser as a JSON result when the page is requested with the same value in the ajax request parameter. | 0 (No)                 |
| allowedRequestKeys | Comma-separated list of request keys, that can be used to filter the displayed events. Defaults to all allowed.                                                                    | -                      |
| calendars          | Comma-separated list of aliases of calendars to filter the displayed events.                                                                                                       | -                      |
| categories         | Comma separated list of aliases of categories to filter the displayed events.                                                                                                      | -                      |
| categoryTpl        | Name of a chunk that contains the template of one category in the category list of an event.                                                                                       | tplAgendaEventCategory |
| contexts           | Comma separated list of context keys to filter the displayed events.                                                                                                               | -                      |
| daterangeFormat    | Format of the daterange displayed in an event.                                                                                                                                     | -                      |
| daterangeSeparator | Separator in the daterange displayed in an event.                                                                                                                                  | -                      |
| detailId           | ID of a resource containing an AgendaDetail snippet call.                                                                                                                          | -                      |
| durationParts      | Number of detail parts of the event duration output.                                                                                                                               | 1                      |
| durationRound      | **Since 1.5.0** Rounding type for event duration.                                                                                                                                  | ceil                   |
| end                | The end date to filter the displayed events. Must contain a [supported date and time format](https://www.php.net/manual/de/datetime.formats.php).                                  | -                      |
| excludeEvents      | Comma separated list of event IDs to exclude from the displayed events.                                                                                                            | -                      |
| excludeRepeats     | Comma separated list of repeating event IDs to exclude from the displayed events.                                                                                                  | -                      |
| imageTpl           | Name of a chunk that contains the template for one image in the image list of an event.                                                                                            | tplAgendaEventImage    |
| interval           | The interval into which the period between start and end date is divided. Must contain a [supported date and time format](https://www.php.net/manual/de/datetime.formats.php).     | -                      |
| intervalTpl        | Name of a chunk that contains the template for an interval.                                                                                                                        | tplAgendaEventInterval |
| listId             | ID of a resource containing an AgendaList snippet call.                                                                                                                            | -                      |
| locale             | The locale for the displayed formatted date. Defaults to the current system/context locale setting.                                                                                | -                      |
| locations          | Comma separated list of aliases of locations to filter the displayed events.                                                                                                       | -                      |
| locationTpl        | Name of a chunk that contains the template for the location of an event.                                                                                                           | tplAgendaEventLocation |
| outputSeparator    | An optional string to separate each tpl instance.                                                                                                                                  | -                      |
| resourceTpl        | Name of a chunk that contains the template for the linked resource of an event.                                                                                                    | -                      |
| start              | The start date to filter the displayed events. Must contain a [supported date and time format](https://www.php.net/manual/de/datetime.formats.php).                                | -                      |
| toPlaceholder      | If set, the snippet result will be assigned to this placeholder instead of outputting it directly.                                                                                 | -                      |
| tpl                | Name of a chunk that contains the template for one event.                                                                                                                          | tplAgendaEventRow      |
| usergroups         | Comma separated list of user group names to filter the displayed events.                                                                                                           | -                      |
| users              | Comma separated list of user IDs to filter the displayed events.                                                                                                                   | -                      |
| videoTpl           | Name of a chunk that contains the template for one video in the video list of an event.                                                                                            | tplAgendaEventVideo    |
| where              | **Since 1.5.0** JSON encoded xPDO where clause to filter the displayed events.                                                                                                     | -                      |
| wrapperTpl         | Name of a chunk that contains the wrapper template for all events.                                                                                                                 | tplAgendaEventWrapper  |

## Placeholders

The following placeholders are available in the different (default) chunks. Each
snippet property will be set as placeholder in each template chunk, i.e. a
snippet call ```[[!AgendaDetail? &subtitle=`whatever`]]``` will fill the
placeholder subtitle in each used chunk with the value `whatever`.

**CAUTION:** The default template chunks for both snippets are overwritten
during each package update, so please rename the chunks before editing them.

### tplAgendaEventRow

| Placeholder         | Description                                                                                                                                                                                                                                                                                                                |
|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| allday              | Contains 1 if the event is an all day event (otherwise 0).                                                                                                                                                                                                                                                                 |
| calendar_background | The background color of the calendar of the event.                                                                                                                                                                                                                                                                         |
| calendar_foreground | The foreground color of the calendar of the event.                                                                                                                                                                                                                                                                         |
| calendar_name       | The calendar name.                                                                                                                                                                                                                                                                                                         |
| categories          | All categories of the event formatted by the chunk set with the categoryTpl property.                                                                                                                                                                                                                                      |
| content             | The content of the event.                                                                                                                                                                                                                                                                                                  |
| description         | The description of the event.                                                                                                                                                                                                                                                                                              |
| detail_url          | The url that shows the event detail. Will be generated with the system/context setting `agenda.detail_id`. This resource should contain an AgendaDetail snippet call.                                                                                                                                                      |
| duration            | The formatted duration of the event. The details of the duration can be set with the `durationParts` snippet property.                                                                                                                                                                                                     |
| enddate             | The start date of the event formatted in ISO 8601 (can be formatted i.e. with ```[[+enddate:strtotime:date=`%a. %d.%m.%Y`]]```).                                                                                                                                                                                           |
| idx                 | The number of the event starting with 1.                                                                                                                                                                                                                                                                                   |
| images              | All images of the event formatted by the chunk set with the imageTpl property.                                                                                                                                                                                                                                             |
| imageurls           | An array of all image urls. The placeholder `[[+imageurls.1]]` contains the url of the first image                                                                                                                                                                                                                         |
| location            | The location of the event formatted by the chunk set with the locationTpl property.                                                                                                                                                                                                                                        |
| main_description    | The description of the main event (useful for repeating events).                                                                                                                                                                                                                                                           |
| main_location       | The location of the main event formatted by the chunk set with the locationTpl property (useful for repeating events).                                                                                                                                                                                                     |
| main_resource_id    | The id of a linked resource of the main event (useful for repeating events).                                                                                                                                                                                                                                               |
| main_title          | The title of the main event (useful for repeating events).                                                                                                                                                                                                                                                                 |
| range               | The formatted date range of the event. The format is defined with the lexicon entries `agenda.php_format_daterange` and `agenda.php_format_separator` and can be overridden by the `daterangeFormat` snippet property. The [format rules](01_AgendaList.md#range-placeholder-format) are described on the AgendaList page. |
| repeating           | Contains 1 if the event is an repeating event (otherwise 0).                                                                                                                                                                                                                                                               |
| repeating_id        | The id of the event date if the event is a repeating event.                                                                                                                                                                                                                                                                |
| resource_id         | The id of a linked resource of the event.                                                                                                                                                                                                                                                                                  |
| startdate           | The start date of the event formatted in ISO 8601 (can be formatted i.e. with ```[[+startdate:strtotime:date=`%a. %d.%m.%Y`]]```).                                                                                                                                                                                         |
| title               | The title of the event.                                                                                                                                                                                                                                                                                                    |
| videos              | All videos of the event formatted by the chunk set with the videosTpl property.                                                                                                                                                                                                                                            |
| videourls           | An array of all video urls. The placeholder `[[+videourls.1]]` contains the url of the first video.                                                                                                                                                                                                                        |

[Extended fields](../06_Extended_Fields.md) are available as placeholder with the prefix `extended` in the
event row template.

If the `tpl` property contains a not found chunk, all possible placeholders are displayed with print_r.

### tplAgendaInterval

| Placeholder | Description                                                                                                                                                                                                                                                                                                    |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| count       | Count of the events in the interval filtered by the snippet properties.                                                                                                                                                                                                                                        |
| enddate     | The end date of the interval formatted in ISO 8601 (can be formatted i.e. with ```[[+startdate:strtotime:date=`%a. %d.%m.%Y`]]```).                                                                                                                                                                          |
| idy         | The number of the interval starting with 1.                                                                                                                                                                                                                                                                    |
| output      | All events in one interval collected by the snippet separated by the string in the outputSeparator property.                                                                                                                                                                                                   |
| range       | The formatted date range of the interval. The format is defined with the lexicon entries `agenda.php_format_daterange` and `agenda.php_format_separator` and can be overridden by the `daterangeFormat` snippet property. The [format rules](01_AgendaList.md#range-placeholder-format) are described below. |
| startdate   | The start date of the interval formatted in ISO 8601 (can be formatted i.e. with ```[[+startdate:strtotime:date=`%a. %d.%m.%Y`]]```).                                                                                                                                                                        |

If the `intervalTpl` property contains a not found chunk, all possible placeholders are displayed with print_r.

### tplAgendaEventWrapper

| Placeholder | Description                                                                                     |
|-------------|-------------------------------------------------------------------------------------------------|
| count       | Count of all events filtered by the snippet properties.                                         |
| output      | All intervals collected by the snippet separated by the string in the outputSeparator property. |

If the `wrapperTpl` property contains a not found chunk, all possible placeholders are displayed with print_r.

### tplAgendaEventEmpty

Only the current script properties are available as placeholders.

If the `emptyTpl` property contains a not found chunk, all possible placeholders are displayed with print_r.

### tplAgendaEventCategory

| Placeholder | Description                                                                                                                                                                                        |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| alias       | The alias of the category.                                                                                                                                                                         |
| background  | The background color of the category of the event.                                                                                                                                                 |
| foreground  | The foreground color of the category of the event.                                                                                                                                                 |
| name        | The name of the category.                                                                                                                                                                          |
| resource_id | The id of a linked resource of the category.                                                                                                                                                       |
| selected    | Contains `selected="selected"`, when the category request value is equal to the alias of the category.                                                                                             |
| url         | The url that shows the event list filtered by the displayed category. Will be generated with the system/context setting `agenda.list_id`. This resource should contain an AgendaList snippet call. |

If the `categoryTpl` property contains a not found chunk, all possible placeholders are displayed with print_r.

### tplAgendaEventImage

| Placeholder | Description                              |
|-------------|------------------------------------------|
| description | The description of the image.            |
| idx         | The number of the image starting with 1. |
| title       | The title of the image.                  |
| url         | The url that shows the event image.      |

If the `imageTpl` property contains a not found chunk, all possible placeholders are displayed with print_r.

### tplAgendaEventLocation

| Placeholder | Description                                                                                            |
|-------------|--------------------------------------------------------------------------------------------------------|
| address     | The address of the location.                                                                           |
| alias       | The alias of the location.                                                                             |
| center_lat  | The latitude of the center of a map of the location.                                                   |
| center_lng  | The longitude of the center of a map of the location.                                                  |
| description | The description of the location.                                                                       |
| lat         | The latitude of the location.                                                                          |
| lng         | The longitude of the location.                                                                         |
| name        | The name of the location.                                                                              |
| resource_id | The id of a linked resource of the location.                                                           |
| selected    | Contains `selected="selected"`, when the location request value is equal to the alias of the location. |
| zoom        | The zoom level of a map of the location.                                                               |

If the `locationTpl` property contains a not found chunk, all possible placeholders are displayed with print_r.

### tplAgendaEventVideo

| Placeholder | Description                              |
|-------------|------------------------------------------|
| description | The description of the video.            |
| idx         | The number of the video starting with 1. |
| title       | The title of the video.                  |
| url         | The url that shows the event video.      |

If the `videoTpl` property contains a not found chunk, all possible placeholders are displayed with print_r.
