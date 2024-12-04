---
title: Kontextbezogene Zustimmung 
---

Die kontextbezogene Zustimmung ermöglicht eine Zustimmung zu einem Dienst am
Platz. Dies wird z.B. verwendet, um eingebettete YouTube-Videos auszublenden und
einen Platzhalter mit einer Zustimmungsschaltfläche darin anzuzeigen.

Diese Funktion kann mit der Service-Einstellung 'Nur kontextbezogene Zustimmung'
erweitert werden. Wenn diese Einstellung aktiviert ist, kann der Dienst nicht
global mit dem 'Alle Akzeptieren' im Zustimmungsmanagement aktiviert werden. Der
Dienst wird weiterhin durch einen Platzhalter versteckt. Dort wird aber eine
zweite Schaltfläche angezeigt, mit der der Benutzer den Dienst global aktivieren
kann.

Die kontextbezogene Zustimmung kann nicht deaktiviert werden, der Platzhalter
für die Einwilligung kann aber durch die folgende css-Regel ausgeblendet werden:

```css
div[data-type="placeholder"] {
    display: none;
}
```
