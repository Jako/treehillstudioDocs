---
title: Google Maps 
---

Um das automatische Laden und Ausführen des Google Maps-Skripts zu deaktivieren,
müssen Sie müssen Sie den Google Maps Code auf der Website nach folgendem Beispiel einbauen:

```html
<script type="application/javascript">
    function initMap() {
        ...
    }
</script>
<script onload="initMap()" type="text/plain" data-type="text/javascript" data-name="googlemaps" data-src="https://maps.google.com/maps/api/js?key=xxxxxxx"></script>
```

Da die Reihenfolge der Ausführung der Javascripte, wenn sie von Klaro! aktiviert
werden, nicht eindeutig festgelegt ist, muss das Object `google.maps` in einer
Methode konfiguriert werden, die die nach dem Laden des Google Maps-Skripts mit
dem onload-Attribut ausgeführt wird. Andernfalls erhält man eventuell einen
`Uncaught ReferenceError: google.maps is not defined` Fehler in der
Browserkonsole und Google Maps funktioniert in diesem Fall nicht.
