---
title: AgendaFormatRange
---

This output filter formats a date range from the `startdate||enddate` format to
the displayed format with the [format
rules](01_AgendaList.md#range-placeholder-format) described on the are described
on the AgendaList page. The output filter was introduced with Agenda 1.7.0.

## Output Filter Properties

The output filter uses the following properties:

| Property | Description                                                                                                                                                                                                                                                                                                                    | Default |
|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------|
| input    | A date range in the `startdate\|\|enddate` format where both dates can be [parsed](https://www.php.net/manual/en/datetime.formats.php) by php DateTime.                                                                                                                                                                        | -       |
| options  | A JSON encoded array of the format options. The array can have the keys `format`, `separator` and `locale`. The format has to use the [format rules](01_AgendaList.md#range-placeholder-format) and can be filled with the format placeholders of [DateTime::format](https://www.php.net/manual/de/datetime.format.php). Default: `{"format":"j.\| F \|Y\|, \|g\|:i\| a","separator":"&thinsp;–&thinsp;","locale":""}` | -       |
