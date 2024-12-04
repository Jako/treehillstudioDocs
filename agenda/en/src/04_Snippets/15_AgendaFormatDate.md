---
title: AgendaFormatDate
---

This output filter formats a date to the displayed format. The output filter was
introduced with Agenda 1.7.0.

## Output Filter Properties

The output filter uses the following properties:

| Property | Description                                                                                                                                                                                                                                                                    | Default |
|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------|
| input    | A date that can be [parsed](https://www.php.net/manual/en/datetime.formats.php) by php DateTime.                                                                                                                                                                               | -       |
| options  | A JSON encoded array of the format options. The array can have the keys `format` and `locale`. The format can be filled with the format placeholders of [DateTime::format](https://www.php.net/manual/de/datetime.format.php). Default: `{"format":"d.m.Y g:i a","locale":""}` | -       |
