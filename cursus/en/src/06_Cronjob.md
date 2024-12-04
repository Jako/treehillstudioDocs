---
title: Cronjob
---

_Cursus_ can be controlled by a _cronjob command_.

## Executing the cronjob command

The cronjob command can be executed from the command line with

``` php
php /path/to/your/modx/installation/assets/components/cursus/cron.php
```

or with an external webcronjob using the following url:

``` shell
https://your.domain/assets/components/cursus/cron.php?cronjob_id=xxx
```

The value xxx has to be filled with the random string in the MODX system setting
`cursus.cronjob_id`

## The cronjob command tasks

The cronjob command will run three different tasks:

- [send the reminder mails](#send-the-reminder-mails)
- [purge the event date reserverations](#purge-the-event-date-reserverations)
- [process the mail queue](#process-the-mail-queue)

Normally only the reminder mails are sent when no property is set for the
cronjob command. To run a single task you can use the property `mode=reminder`,
`mode=purgeReserved` or `mode=mailQueue` for the cronjob:

``` php
php /path/to/your/modx/installation/assets/components/cursus/cron.php mode=reminder
```

or

``` shell
https://your.domain/assets/components/cursus/cron.php?cronjob_id=xxx&mode=reminder
```

### Send the reminder mails

All reminder mails defined by the reminders are mailed. If Curus is running in
the debug mode, the mails are sent to the address specified in the
`cursus.email_to` system setting.

### Purge the event date reserverations

If you want to sell the cursus events with a web shop you should set the
`status` of the event participant to `reserved` and set `validuntil` to an
unixtime in the future. The reserved event participants are purged with this
task.

### Process the mail queue

If you enable the Cursus [system setting](03_Custom_Manager_Page/07_Settings.md)
`cursus.queued_email` the mails of Cursus are sent with the built-in mail queue.

## Debug the cronjob

To detect cronjob issues, you can enable the Cursus [system
setting](03_Custom_Manager_Page/07_Settings.md) `cursus.debug`. Per default cronjob
errors are logged in the standard MODX error log. Also, the mails are sent to
the address specified in the `cursus.email_to` system setting when the debug
mode is active.
