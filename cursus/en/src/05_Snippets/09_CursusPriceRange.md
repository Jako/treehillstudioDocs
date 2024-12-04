---
title: CursusPriceRange
---

This snippet gets the price range of events.

## Properties

It uses the following snippet properties:

| Property           | Description                                                                                                                                          | Default             |
|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
| contexts           | Comma separated list of context keys to filter the pricerange events.                                                                                | -                   |
| end                | The end date to filter the pricerange events. Must contain a [supported date and time format](https://www.php.net/manual/de/datetime.formats.php).   | today +1 month 0:00 |
| having             | JSON encoded xPDO having clause to filter the pricerange events.                                                                                     | -                   |
| latestRegistration | The latest registration for each event. Can be overridden on event base, if the system setting "show_latest_registration" is enabled.                | -                   |
| published          | Publication status of the pricerange events. 0: unpublished, 1: published, 2: both.                                                                  | 1                   |
| start              | The start date to filter the pricerange events. Must contain a [supported date and time format](https://www.php.net/manual/de/datetime.formats.php). | today 0:00          |
| toPlaceholder      | If this option is set, the snippet result will be assigned to this placeholder instead of outputting it directly.                                    | -                   |
| tpl                | Name of a chunk that contains the template for the pricerange.                                                                                       | tplCursusPriceRange |
| where              | JSON encoded xPDO where clause to filter the pricerange events.                                                                                      | -                   |

## Placeholders

The following placeholders are available in the different (default) chunks.
Also, each snippet property will be set as placeholder in each template chunk,
i.e. a snippet call ```[[!CursusPriceRange? &subtitle=`whatever`]]``` will fill
the placeholder subtitle in each used chunk with the value `whatever`.

**CAUTION:** The default template chunks for both snippets are overwritten
during each package update, so please rename the chunks before editing them.

### tplCursusPriceRange

| Placeholder | Description        |
|-------------|--------------------|
| min         | The minimum price. |
| max         | The maximum price. |

[Extended fields](../07_Extended_Fields.md) are available as placeholder with
the prefix `extended_` in the event row template.

If the `tpl` property contains a not found chunk, all possible placeholders are
displayed with print_r.
