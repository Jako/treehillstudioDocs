---
title: Installation 
---

Das MODX-Installationsprogramm installiert das Paket automatisch aus dem modmore
Repository.

Dabei wird eine eigene Managerseite namens _ConsentFriend_ im Menü _Extras_
angelegt.

Es gibt nun einige Systemeinstellungen im Namensraum _ConsentFriend_. Diese
können zusätzlich auch im [settings](03_Custom_Manager_Page/05_Settings.md)
(Zahnrad Icon) auf der _ConsentFriend_ Custom Manager Seite bearbeitet werden.

## Vorbereiten der Website

ConsentFriend installiert verschiedene
[Standard-Dienste](02_Functionality/02_Default_Services.md). Einige von ihnen
verwenden System-/Kontext Einstellungen, die Sie selbst anlegen müssen.

Nach der Installation auf einer bestehenden Website müssen Sie die verwendeten
externen Dienste, wie Google Analytics, Matomo, Google Fonts, etc.
identifizieren. Wenn diese bisherigen Dienste am Ende des Head- oder
Body-Abschnitts referenziert werden, können Sie [einen bestehenden Dienst
bearbeiten oder einen neuen Dienst
anlegen](03_Custom_Manager_Page/01_Services.md#createedit) und den gefundenen
Code des bisherigen Dienstes auf der Registerkarte Code einsetzen. ConsentFriend
wird die notwendigen Änderungen am Code vornehmen für das
Zustimmungsmanagement-Fenster vornehmen.

Wenn Sie Inline-Code für externe Dienste verwenden, müssen Sie ihn [selbst
ändern](02_Functionality/01_Introduction.md#Benutzerdefinierte-externe-Dienste).

## Aktivieren des Zustimmungsmanagement

Nach diesen Vorbereitungen müssen Sie ConsentFriend mit dem Befehl
Systemeinstellung `consentfriend.enable` aktivieren. Danach wird das
Zustimmungsmanagement-Fenster im Frontend angezeigt. Eine Kontext-, eine
Benutzer- oder eine Benutzergruppeneinstellung kann ebenfalls zum Aktivieren
benutzt werden.
