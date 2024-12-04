---
title: Google Maps 
---

To disable the automatic loading and execution of the Google Maps script, you
must add the Google Maps code to the website according to the following example:

```html
<script type="application/javascript">
    function initMap() {
        ...
    }
</script>
<script onload="initMap()" type="text/plain" data-type="text/javascript" data-name="googlemaps" data-src="https://maps.google.com/maps/api/js?key=xxxxxxx"></script>
```

Since the order of execution of the javascripts when activated by Klaro! is not
clearly defined, the `google.maps` object must be configured in a method that is
executed loading the Google Maps script with the onload attribute. Otherwise you
may get an `Uncaught ReferenceError: google.maps is not defined` error in
the browser console and Google Maps will not work in this case.
