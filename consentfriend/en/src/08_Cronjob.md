---
title: Cronjob
---

_ConsentFriend_ can be controlled by a _cronjob command_.

## Executing the cronjob command

The cronjob command can be executed from the command line with

```
php /path/to/your/modx/installation/assets/components/consentfriend/cron.php
```

or with an external webcronjob using the following url:

```
https://your.domain/assets/components/consentfriend/cron.php?cronjob_id=xxx
```

The value xxx has to be filled with the random string in the MODX system setting
`consentfriend.cronjob_id`

## The cronjob tasks

The cronjob command will run one task:

- [update the GeoIP2 database](#update-the-geoip2-database)

### Update the GeoIP2 database

Normally the GeoIP2 database will be updated during manager access after 30
days. This can be done by the cronjob. In that case you should set the system
setting `use_cron` to true.
