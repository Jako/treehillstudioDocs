---
title: Cronjob
---

_ConsentFriend_ kann durch einen _cronjob-Befehl_ gesteuert werden.

## Executing the cronjob command

Der cronjob-Befehl kann von der Kommandozeile aus ausgeführt werden mit

```
php /path/to/your/modx/installation/assets/components/consentfriend/cron.php
```

oder mit einem externen Webcronjob unter Verwendung der folgenden URL:

```
https://your.domain/assets/components/consentfriend/cron.php?cronjob_id=xxx
```

Der Wert xxx muss mit dem zufälligen String in der MODX-Systemeinstellung
`consentfriend.cronjob_id` gefüllt werden.

## Die Cronjob-Aufgaben

The cronjob command will run one task:

- [Aktualisierung der GeoIP2-Datenbank](#aktualisierung-der-geoip2-datenbank)

### Aktualisierung der GeoIP2-Datenbank

Normalerweise wird die GeoIP2-Datenbank beim Managerzugriff nach 30 Tagen
aktualisiert. Dies kann durch den Cronjob geschehen. In diesem Fall sollten Sie
die Systemeinstellung `use_cron` auf true setzen.
