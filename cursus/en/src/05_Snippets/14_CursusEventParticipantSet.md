---
title: CursusEventParticipantSet
---

This hook allows to fill Cursus event participants values with FormIt.

## FormIt Hook Properties

It uses the following hook properties:

| Property                             | Description                                                               | Default                                                   |
|--------------------------------------|---------------------------------------------------------------------------|-----------------------------------------------------------|
| cursusAssign                         | ID of one Cursus participant that is assigned without validation.         | request value `assign_id` or 0                            |                                           
| cursusEvent                          | ID of one Cursus event to.                                                | request value `event_id` or 0                             |
| cursusExtendedEventParticipantFields | JSON encoded array of extended event participant fields.                  | system setting `cursus.extended_event_participant_fields` | 
| cursusExtendedUserFields             | JSON encoded array of extended participant fields.                        | system setting `cursus.extended_user_fields`              | 
| cursusOnlyOwnUser                    | Load only own participant (created by the current user).                  | true                                                      |       
| cursusParticipant                    | ID of one Cursus participant.                                             | request value `participant_id` or 0                       |
| cursusPublished                      | Publication status of the event. 0: unpublished, 1: published, 2: both.   | 1                                                         | 
| cursusWhere                          | JSON encoded xPDO where clause to filter the events.                      |                                                           |
| cursusSendBookedMailUserSubject      | The subject of the booked mail sent to the participant.                   | tplCursusBookedMailUserSubject                            |
| cursusSendBookedMailUserText         | The subject of the booked mail sent to the participant.                   | tplCursusBookedMailUserText                               |
| cursusSendBookedMailOwnerSubject     | The subject of the booked mail sent to the owner.                         | tplCursusBookedMailOwnerSubject                           |
| cursusSendBookedMailOwnerText        | The subject of the booked mail sent to the owner.                         | tplCursusBookedMailOwnerText                              |
| cursusSendBookedMailTrainerRow       | The row template of one trainer used in the booked mail.                  | tplCursusBookedMailTrainerRow                             |                                        
| cursusSendBookedMailtrainerWrapper   | The wrapper template for all trainers used in the booked mail.            | tplCursusBookedMailTrainerWrapper                         |                                    
| cursusSendBookedMailTrainerSeparator | The string that is used to separate all trainers in the wrapper template. | `, `                                                      |
| cursusSendBookedOwnerMail            | Send the booked mail to the owner?                                        | 0 (No)                                                    |
| cursusSendBookedParticipantMail      | Send the booked mail to the participant?                                  | 0 (No)                                                    |
| cususStatus                          | The status of the booking created by the hook.                            | reserved                                                  |

## Hook fields

The following FormIt fields are used to fill the Cursus event participant in the hook:

| Field          | Description                                                                                                                      |
|----------------|----------------------------------------------------------------------------------------------------------------------------------|
| address        | The address of the event participant.                                                                                            |  
| birthdate      | The birthdate of the event participant.                                                                                          |
| birthplace     | The address of the event participant.                                                                                            |  
| city           | The address of the event participant.                                                                                            |  
| company        | The company of the event participant.                                                                                            |  
| country        | The country of the event participant.                                                                                            |
| email          | The email of the event participant.                                                                                              |
| fax            | The fax number of the event participant.                                                                                         |  
| firstname      | The first name of the event participant.                                                                                         |
| gender         | The gender of the event participant.                                                                                             |
| idx            | The number of the event participant starting with 1.                                                                             |
| jobtitle       | The job title of the event participant.                                                                                          |  
| lastname       | The last name of the event participant.                                                                                          |
| mobile         | The mobile number of the event participant.                                                                                      |  
| name           | The name of the event participant.                                                                                               |
| participant_id | The id of the participant.                                                                                                       |
| phone          | The phone number of the event participant.                                                                                       |  
| quantity       | The quantity of participants added to the event. Available when the `cursus.show_participant_quantity` system setting is enabled |  
| state          | The state of the event participant.                                                                                              |  
| website        | The website of the event participant.                                                                                            |  
| zip            | The zip of the event participant.                                                                                                |  

If the participant is assigned, the participant retrieved with the assign ID has to
exist. All other participant fields are bypassed then.

[Extended fields](../07_Extended_Fields.md) are retrieved from the FormIt fields
with the prefix `extended_` in the hook.
