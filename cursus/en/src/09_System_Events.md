---
title: System Events
---

The following system events exists in Cursus:

    'OnCursusBeforeSave',
    'OnCursusSave',
    'OnCursusBeforeRemove'

The use of these events allows additional code to be executed before and after
saving and before deleting Cursus database entries.

The following Cursus database objects invoke the system events:
CursusEventParticipants, CursusEvents, CursusEventTrainers, CursusParticipants,
CursusReminders and CursusTrainers.

The following properties can be used in the plugin events:

| Property  | Content                                                                                                                                                              |
|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| mode      | The state of the Cursus object. It can contain the following states: `modSystemEvent::MODE_NEW` or `modSystemEvent::MODE_UPD`. Not available in OnCursusBeforeRemove |
| className | The class name of the saved object.                                                                                                                                  |
| id        | The identifier of the saved object.                                                                                                                                  |
| object    | The Cursus object.                                                                                                                                                   |

Skeleton classes for the events can be found in
`core/components/cursus/src/Plugins/Events`. To use them, you have to remove the
underscore prefix from the filename and activate the according event in the
Cursus plugin.
