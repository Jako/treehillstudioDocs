---
title: CursusTrainerList
---

This snippet displays Cursus trainers in a list.

## Properties

It uses the following snippet properties:

| Property          | Description                                                                                                                                                                       | Default                 |
|-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------|
| ajax              | If this option is set, the snippet output will be directly returned to the browser as a JSON result when the page is requested with the same value in the ajax request parameter. | -                       |
| emptyTpl          | Name of a chunk that contains the template for an empty list of trainers.                                                                                                         | tplCursusTrainerEmpty   |
| limit             | Limit the number of trainers in the result. Use "0" for unlimited trainers.                                                                                                       | 20                      |
| offset            | The offset of trainers to skip.                                                                                                                                                   | -                       |
| outputSeparator   | An optional string to separate each tpl instance.                                                                                                                                 | -                       |
| placeholderPrefix | Prefix for all placeholders set by the snippet.                                                                                                                                   | -                       |
| sortby            | Field name according to which the trainers are sorted.                                                                                                                            | id                      |
| sortdir           | Direction in which the trainers are sorted.                                                                                                                                       | ASC                     |
| toPlaceholder     | If this option is set, the snippet result will be assigned to this placeholder instead of outputting it directly.                                                                 | -                       |
| totalVar          | The key of a placeholder that indicates the total number of trainers.                                                                                                             | trainerlist.total       |
| tpl               | Name of a chunk that contains the template for an trainer.                                                                                                                        | tplCursusTrainerRow     |
| trainers          | Comma separated list of trainer ids to filter the displayed trainers.                                                                                                             | -                       |
| where             | JSON encoded xPDO where clause to filter the trainers.                                                                                                                            | -                       |
| wrapperTpl        | Name of a chunk that contains the wrapper template for all trainers.                                                                                                              | tplCursusTrainerWrapper |

## Placeholders

The following placeholders are available in the different (default) chunks.
Also, each snippet property will be set as placeholder in each template chunk,
i.e. a snippet call ```[[!CursusTrainerList? &subtitle=`whatever`]]``` will fill
the placeholder subtitle in each used chunk with the value `whatever`.

**CAUTION:** The default template chunks for both snippets are overwritten
during each package update, so please rename the chunks before editing them.

### tplCursusTrainerRow

| Placeholder | Description                                                                                                                                     |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| address     | The address of the event participant.                                                                                                           |  
| birthdate   | The birthdate of the event participant formatted in ISO 8601 (could be formatted i.e. with ```[[+birthdate:strtotime:date=`%a. %d.%m.%Y`]]```). |
| birthplace  | The address of the event participant.                                                                                                           |  
| city        | The address of the event participant.                                                                                                           |  
| comment     | The comment of the event participant.                                                                                                           |
| company     | The company of the event participant.                                                                                                           |  
| country     | The country of the event participant.                                                                                                           |
| email       | The email of the event participant.                                                                                                             |
| fax         | The fax number of the event participant.                                                                                                        |  
| firstname   | The first name of the event participant.                                                                                                        |
| gender      | The gender of the event participant.                                                                                                            |
| idx         | The number of the event participant starting with 1.                                                                                            |
| jobtitle    | The job title of the event participant.                                                                                                         |  
| lastname    | The last name of the event participant.                                                                                                         |
| mobile      | The mobile number of the event participant.                                                                                                     |  
| name        | The name of the event participant.                                                                                                              |
| phone       | The phone number of the event participant.                                                                                                      |  
| state       | The state of the event participant.                                                                                                             |  
| website     | The website of the event participant.                                                                                                           |  
| zip         | The zip of the event participant.                                                                                                               |  

[Extended fields](../07_Extended_Fields.md) are available as placeholder with
the prefix `extended_` in the trainer row template.

If the `tpl` property contains a not found chunk, all possible placeholders are
displayed with print_r.

### tplCursusTrainerWrapper

| Placeholder | Description                                                                                             |
|-------------|---------------------------------------------------------------------------------------------------------|
| count       | Count of the event participants by the snippet properties (without limit/offset)                        |
| output      | All event participants collected by the snippet separated by the string in the outputSeparator property |

If the `tpl` property contains a not found chunk, all possible placeholders are
displayed with print_r.

### tplCursusTrainerEmpty

Only the current script properties are available as placeholders.

If the `tpl` property contains a not found chunk, all possible placeholders are
displayed with print_r.
