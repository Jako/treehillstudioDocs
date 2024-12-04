---
title: FAQ
hide:
   - toc
---

Wir haben die am häufigsten gestellten Fragen in einer FAQ zusammengefasst. Wenn
Ihre Frage nicht in der Liste enthalten ist, wenden Sie sich bitte an
treehillstudio-support@modmore.com und wir helfen Ihnen gerne weiter.

[TOC]

## Wie kann ich eine bestehende Google Analytics-Implementierung in einer MODX-Website in ConsentFriend umwandeln?

1. Suchen Sie die Verwendung von Google Analytics in Ihrem Template oder in den
   abhängigen Chunk-Aufrufen.
2. Kopieren Sie die Google Analytics ID (ein String, der mit `G-` beginnt) in
   der Vorlage oder dem Chunk und erstellen Sie eine Systemeinstellung
   `google_analytics_id` mit diesem Wert.
3. Deaktivieren Sie diesen Chunk (z.B. durch Umbenennung) oder den Template
   (z.B. durch Umbenennen) oder den Template-Teil (z.B. durch Umgeben mit `[[-`
   und `]]`).
4. Aktivieren Sie ConsentFriend im Frontend.
5. Löschen Sie den MODX-Cache.

## Kann ich verschiedene Google Analytics IDs in verschiedenen Kontexten verwenden?

Das ist möglich. Der Standard-Google-Analytics-Dienst verwendet das MODX
System/Kontext-Einstellungs-Tag `[[++google_analytics_id]]`. Sie müssen also
eine Kontexteinstellung `google_analytics_id` mit dem Wert der Google Analytics
ID erstellen.

Bitte stellen Sie sicher, dass das ConsentFriend-Plugin eine höhere Priorität
hat als das Kontext-Routing-Plugin im onHandleRequest-Ereignis eine höhere
Priorität hat. Dazu müssen Sie das ConsentFriend-Plugin bearbeiten. In der
Registerkarte System Events müssen Sie das OnHandleRequest-Plugin-Ereignis
aktualisieren und den Prioritätswert von ConsentFriend mit einem höheren Wert
als das Routing-Plugin.

## Kann ich verschiedene Datenschutzrichtlinien in verschiedenen Kontexten verwenden?

Dies ist mit einer Kontexteinstellung möglich. Dazu müssen Sie die Option
`consentfriend.privacy_policy_id` in jedem Kontext anders setzen. Bitte stellen
Sie auch sicher, dass das ConsentFriend-Plugin eine höhere Priorität im
onHandleRequest-Ereignis eine höhere Priorität hat als das
Context-Routing-Plugin. Siehe den FAQ-Eintrag oben für weitere Informationen.

## Das Zustimmungsmodal zeigt nur Lexikonschlüssel anstelle von übersetzten Strings

Das ist ein Ergebnis der unterschiedlichen Spracherkennung. MODX verwendet die
cultureKey System/Kontext-Einstellung und ConsentFriend verwendet das html
lang-Attribut. Sie müssen also müssen Sie das html lang-Attribut mit der
cultureKey-System-/Kontext-Einstellung füllen: `<html lang="[[++cultureKey]]">`.

## Ich möchte die Texte von ConsentFriend ändern

Dies kann mit dem ConsentFriend [Lexikon](07_Lexicon.md) geschehen.

## Wie kann ich ein eigenes Theme für ConsentFriend erstellen?

Wenn du dein eigenes Theme erstellen willst, kannst du die Datei
`assets/components/consentfriend/scss/consentfriend.scss` in deinen
scss-Workflow importieren. Dort sind einige scss-Variablen verfügbar in
`assets/components/consentfriend/scss/vars.scss`, die überschrieben werden
können vorher. Um das Standard-Styling des Modals nachträglich zu deaktivieren,
setzen Sie bitte die Systemeinstellung consentfriend.js_url auf
`/assets/components/consentfriend/js/web/consentfriend-no-css.js`.

## Wie kann ich das Fenster der Einwilligungsverwaltung auf einer Seite wieder anzeigen?

Wenn Sie dem Benutzer die Möglichkeit geben wollen, seine
Einwilligungseinstellungen zu ändern, können Sie einen Link zum Fenster der
Einwilligungsverwaltung mit folgendem Code hinzufügen:

```html
<a onclick="klaro.show(window.consentFriendConfig, { modal: true });return false;">
   [[%consentfriend.services.change_setting? &namespace=`consentfriend`]]
</a>
```

## Wie kann ich externen html-Code automatisch für ConsentFriend ändern?

Es ist möglich, den html-Code von z.B. YouTube-Videos in einem Platzhalter mit
dem folgenden Ausgabefilter zu ersetzen. Erstellen Sie ein Snippet
FilterConsentFriendVideo mit folgendem Code und verwenden Sie es auf den
Platzhalter mit `[[+placeholder:FilterConsentFriendVideo]]`

Snippet FilterConsentFriendVideo
```php
<?php
// Replace youtube iframe attributes with ConsentFriend compatible attributes
return preg_replace(
    '~<iframe(.*?)src="https://www\.youtube\.com/embed/(.*?)"(.*?)width="(.*?)"(.*?)</iframe>~m',
    '<iframe$1data-name="youtube" data-src="https://www.youtube.com/embed/$2"$3></iframe>',
    $input
);
```

Es steht Ihnen frei, Ihren eigenen Ausgabefilter für andere externe Dienste zu erstellen.

## Ist es möglich, den Google Consent Mode v2 mit ConsentFriend zu verwenden?

Ja, der Consent Mode v2 kann mit ConsentFriend für Google Analytics
eingestellt werden. Er ist jetzt in die Standardkonfiguration des Google
Analytics-Services integriert. In bereits bestehenden Installationen können Sie
den neuen Code installieren, indem Sie die [Google Analytics service YAML
file](yaml/consentfriend_googleAnalytics.yml) importieren oder einfach die
[Callbacks](https://docs.treehillstudio.de/en/consentfriend/02_Functionality/02_Default_Services/#callbacks)
zum Google Analytics Service selbst hinzufügen.
