---
title: Google Tag Manager 
---

Sie können ConsentFriend ganz einfach mit dem Google Tag Manager (GTM)
integrieren und Einwilligungen für Google Analytics mit ConsentFriend über den
GTM steuern. Die Demo Callback-Skripte im googleTagManager-Service enthalten den
notwendigen Code dafür.

Ändern Sie zunächst den googleAnalytics-Service und löschen Sie dort den
Code-Block. Dies gilt auch für andere Dienste, die Sie über den über den GTM
steuern wollen. Sie müssen nur die Cookies auflisten, die diese Dienste setzen.

Erstellen Sie nun ein Google Analytics-Tag in der GTM-Web-UI. Als Auslöser
erstellen Sie einen [custom event
trigger](https://support.google.com/tagmanager/answer/7679219) mit dem Namen
`consentfriend-googleAnalytics-accepted`. Damit wird sichergestellt, dass GTM
den Google-Analytics-Service nur dann lädt, wenn der Nutzer über „ConsentFriend“
seine Zustimmung gegeben hat. Und das war's!

ConsentFriend verwaltet nun GTM und stellt sicher, dass nur Dienste geladen
werden, für die der Nutzer ConsentFriend zugestimmt hat.

> Wichtig! Um einen weiteren Dienst über GTM hinzuzufügen, aktivieren oder
erstellen Sie zunächst einen Dienst in ConsentFriend und definieren Sie einfach
einen benutzerdefinierten Ereignisauslöser der Form
`consentfriend-[service-name]-accepted`, wobei `[service-name]` der Name des
Dienstes in der ConsentFriend-Konfiguration ist.
