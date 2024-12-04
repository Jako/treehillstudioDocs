---
title: Standard-Dienste 
---

ConsentFriend installiert und verwendet die folgenden Standard-Dienste. Alle
Dienste werden während des Installationsprozesses optional installiert oder
können mit der [Alle Dienste YAML-Datei](../yaml/consentfriend_all.yml) importiert werden.

## Grundlegende Dienste

### ConsentFriend

| Einstellung                    | Wert                                            |
|--------------------------------|-------------------------------------------------|
| Aktiv                          | Ja                                              |
| Standard                       | Nein                                            |
| Erforderlich                   | Ja                                              |
| Opt-out                        | Nein                                            |
| Nur einmalig                   | Nein                                            |
| Nur Kontextbezogene Zustimmung | Nein                                            |
| Cookies                        | Cookie: consentfriend<br>Pfad: ''<br>Domain: '' |

Dieser Dienst kann mit der [consentFriend Dienst YAML
Datei](../yaml/consentfriend_consentFriend.yml) importiert werden.

### Session

| Einstellung                    | Wert                                        |
|--------------------------------|---------------------------------------------|
| Aktiv                          | Ja                                          |
| Standard                       | Nein                                        |
| Erforderlich                   | Ja                                          |
| Opt-out                        | Nein                                        |
| Nur einmalig                   | Nein                                        |
| Nur Kontextbezogene Zustimmung | Nein                                        |
| Cookies                        | Cookie: PHPSESSID<br>Pfad: ''<br>Domain: '' |

Dieser Dienst kann mit der [session Dienst YAML
Datei](../yaml/consentfriend_session.yml) importiert werden.

## Weitere Dienste

### Matomo

| Einstellung                    | Wert                                                                                                      |
|--------------------------------|-----------------------------------------------------------------------------------------------------------|
| Aktiv                          | Nein                                                                                                      |  
| Standard                       | Nein                                                                                                      |
| Erforderlich                   | Nein                                                                                                      |  
| Opt-out                        | Nein                                                                                                      |
| Nur einmalig                   | Ja                                                                                                        |
| Nur Kontextbezogene Zustimmung | Nein                                                                                                      |
| Cookies                        | Cookie: '/^matomo\_.\*$/i'<br>Pfad: ''<br>Domain: ''<br>Cookie: '/^\_pk\_.\*$/'<br>Pfad: ''<br>Domain: '' |

Dieser Dienst nutzt zwei MODX System- bzw. Kontext-Einstellungen im Standard
Code. Die Einstellungen müssen selbst angelegt werden:

| Schlüssel      | Wert                        |
|----------------|-----------------------------|
| matomo_site_id | Site ID in Matomo           |
| matomo_url     | URL der Matomo Installation |  

#### Code

```html
    <script type="text/javascript">
        var _paq = window._paq = window._paq || [];
        _paq.push(['trackPageView']);
        _paq.push(['enableLinkTracking']);
        (function() {
            var u="[[++matomo_url]]";
            _paq.push(['setTrackerUrl', u+'matomo.php']);
            _paq.push(['setSiteId', [[++matomo_site_id]] ]);
            var d=document, g=d.createElement('script'), s=d.getElementsByTagName('script')[0];
            g.type='text/javascript'; g.async=true; g.src=u+'matomo.js'; s.parentNode.insertBefore(g,s);
        })();
    </script>
    <noscript><p><img src="[[++matomo_url]]matomo.php?idsite=[[++matomo_site_id]]&rec=1" style="border:0" alt="" /></p></noscript>
```

Dieser Dienst kann mit der [Matomo Dienst YAML
Datei](../yaml/consentfriend_matomo.yml) importiert werden.

### Google Analytics

| Einstellung                    | Wert                                                                                   |
|--------------------------------|----------------------------------------------------------------------------------------|
| Code-Abschnitt                 | HEAD                                                                                   |
| Aktiv                          | Nein                                                                                   |
| Standard                       | Nein                                                                                   |
| Erforderlich                   | Nein                                                                                   |
| Opt-out                        | Nein                                                                                   |
| Nur einmalig                   | Ja                                                                                     |
| Nur Kontextbezogene Zustimmung | Nein                                                                                   |
| Cookies                        | Cookie: _ga<br>Pfad: ''<br>Domain: ''<br>Cookie: '/^_ga.*$/'<br>Pfad: ''<br>Domain: '' |

Dieser Dienst nutzt eine MODX System- bzw. Kontext-Einstellung im Standard Code.
Die Einstellung muss selbst angelegt werden:

| Schlüssel           | Wert                |
|---------------------|---------------------|
| google_analytics_id | Google Analytics ID |

#### Code

```html
    <script async src="https://www.googletagmanager.com/gtag/js?id=[[++google_analytics_id]]"></script>
    <script>
        window.dataLayer = window.dataLayer || [];
        function gtag(){dataLayer.push(arguments);}
        gtag('js', new Date());
      
        gtag('config', '[[++google_analytics_id]]');
    </script>
```

#### Callbacks

#### On Init

```js
    function (opts) {
        window.dataLayer = window.dataLayer || [];
        window.gtag = function(){
            dataLayer.push(arguments);
        }
        gtag('consent', 'default', {'ad_storage': 'denied', 'ad_user_data': 'denied', 'ad_personalization': 'denied', 'analytics_storage': 'denied'});
    }
```

#### On Accept

```js
    function (opts) {
        window.dataLayer = window.dataLayer || [];
        window.gtag = function(){
            dataLayer.push(arguments);
        }
        gtag('consent', 'update', {'ad_storage': 'denied', 'ad_user_data': 'denied', 'ad_personalization': 'denied', 'analytics_storage': 'granted'});
    }
```

#### On Decline

```js
    function (opts) {
        window.dataLayer = window.dataLayer || [];
        window.gtag = function(){
            dataLayer.push(arguments);
        }
        gtag('consent', 'update', {'ad_storage': 'denied', 'ad_user_data': 'denied', 'ad_personalization': 'denied', 'analytics_storage': 'denied'});
    }
```

Dieser Dienst kann mit der [Google Analytics Dienst YAML
Datei](../yaml/consentfriend_googleAnalytics.yml) importiert werden.

### Google AdSense

| Einstellung                    | Wert |
|--------------------------------|------|
| Code-Abschnitt                 | BODY |
| Aktiv                          | Nein |
| Standard                       | Nein |
| Erforderlich                   | Nein |
| Opt-out                        | Nein |
| Nur einmalig                   | Nein |
| Nur Kontextbezogene Zustimmung | Nein |

#### Code

```html
    <script data-ad-client="[[++google_ad_client_id]]" async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
```

Dieser Dienst kann mit der [Google AdSense Dienst YAML
Datei](../yaml/consentfriend_googleAdSense.yml) importiert werden.

### Google Fonts

| Einstellung                    | Wert |
|--------------------------------|------|
| Code-Abschnitt                 | HEAD |
| Aktiv                          | Nein |
| Standard                       | Nein |
| Erforderlich                   | Nein |
| Opt-out                        | Nein |
| Nur einmalig                   | Nein |
| Nur Kontextbezogene Zustimmung | Nein |

#### Code

```html
    <link href="https://fonts.googleapis.com/css2?family=Open+Sans&display=swap" rel="stylesheet">
```

Dieser Dienst kann mit der [Google Fonts Dienst YAML
Datei](../yaml/consentfriend_googleFonts.yml) importiert werden.

### Cloudflare

| Einstellung                    | Wert                                                                                                                                                                                                                                     |
|--------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aktiv                          | Nein                                                                                                                                                                                                                                     |
| Standard                       | Nein                                                                                                                                                                                                                                     |
| Erforderlich                   | Ja                                                                                                                                                                                                                                       |
| Opt-out                        | Nein                                                                                                                                                                                                                                     |
| Nur einmalig                   | Nein                                                                                                                                                                                                                                     |
| Nur Kontextbezogene Zustimmung | Nein                                                                                                                                                                                                                                     |
| Cookies                        | Cookie: _cflb<br>Pfad: ''<br>Domain: ''<br>Cookie: _cf_bm<br>Pfad: ''<br>Domain: ''<br>Cookie: _cfduid<br>Pfad: ''<br>Domain: ''<br>Cookie: cf_ob_info<br>Pfad: ''<br>Domain: ''<br>Cookie: 'cf_use_ob cookie'<br>Pfad: ''<br>Domain: '' |

Dieser Dienst kann mit der [Cloudflare Dienst YAML
Datei](../yaml/consentfriend_cloudflare.yml) importiert werden.

### YouTube

| Einstellung                    | Wert                                  |
|--------------------------------|---------------------------------------|
| Aktiv                          | Nein                                  |
| Standard                       | Nein                                  |
| Erforderlich                   | Nein                                  |
| Opt-out                        | Nein                                  |
| Nur einmalig                   | Nein                                  |
| Nur Kontextbezogene Zustimmung | Nein                                  |
| Cookies                        | Cookie: abc<br>Pfad: ''<br>Domain: '' |

Dieser Dienst kann mit der [Cloudflare Dienst YAML
Datei](../yaml/consentfriend_cloudflare.yml) importiert werden.

### Google reCAPTCHA

| Einstellung                    | Wert                                                                                                                                                                                                                                                         |
|--------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aktiv                          | Nein                                                                                                                                                                                                                                                         |
| Standard                       | Nein                                                                                                                                                                                                                                                         |
| Erforderlich                   | Nein                                                                                                                                                                                                                                                         |
| Opt-out                        | Nein                                                                                                                                                                                                                                                         |
| Nur einmalig                   | Nein                                                                                                                                                                                                                                                         |
| Nur Kontextbezogene Zustimmung | Nein                                                                                                                                                                                                                                                         |
| Cookies                        | Cookie: IDE<br>Pfad: ''<br>Domain: ''<br>Cookie: 1P_JAR<br>Pfad: ''<br>Domain: ''<br>Cookie: ANID<br>Pfad: ''<br>Domain: ''<br>Cookie: CONSENT<br>Pfad: ''<br>Domain: ''<br>Cookie: NID<br>Pfad: ''<br>Domain: ''<br>Cookie: DVacd<br>Pfad: ''<br>Domain: '' |

#### Callbacks

##### On Toggle

```js
    function(consent, service) {
        var buttons = document.body.querySelectorAll('input[data-name="' + service.name + '"],button[data-name="' + service.name + '"]'), index;
        for (index = 0; index < buttons.length; index++) {
            buttons[index].disabled = !consent;
        }
    }
```

Dieser Dienst kann mit der [Google reCAPTCHA Dienst YAML
Datei](../yaml/consentfriend_googleRecaptcha.yml) importiert werden.

Es gibt ein [Beispiel](Google_reCAPTCHA.md) für die erweiterte Konfiguration des
reCAPTCHA Dienstes.

### Facebook Pixel

| Einstellung                    | Wert                                                                                                                                                                                                                                                                                                                                                                                   |
|--------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Code-Abschnitt                 | BODY                                                                                                                                                                                                                                                                                                                                                                                   |
| Aktiv                          | Nein                                                                                                                                                                                                                                                                                                                                                                                   |
| Standard                       | Nein                                                                                                                                                                                                                                                                                                                                                                                   |
| Erforderlich                   | Nein                                                                                                                                                                                                                                                                                                                                                                                   |
| Opt-out                        | Nein                                                                                                                                                                                                                                                                                                                                                                                   |
| Nur einmalig                   | Nein                                                                                                                                                                                                                                                                                                                                                                                   |
| Nur Kontextbezogene Zustimmung | Nein                                                                                                                                                                                                                                                                                                                                                                                   |
| Cookies                        | Cookie: xs<br>Pfad: ''<br>Domain: ''<br>Cookie: wd<br>Pfad: ''<br>Domain: ''<br>Cookie: spin<br>Pfad: ''<br>Domain: ''<br>Cookie: c_user<br>Pfad: ''<br>Domain: ''<br>Cookie: locale<br>Pfad: ''<br>Domain: ''<br>Cookie: datr<br>Pfad: ''<br>Domain: ''<br>Cookie: fr<br>Pfad: ''<br>Domain: ''<br>Cookie: presence<br>Pfad: ''<br>Domain: ''<br>Cookie: sb<br>Pfad: ''<br>Domain: '' |

#### Code

```html
    <script>
        !function(f,b,e,v,n,t,s)
        { if(f.fbq)return;n=f.fbq=function(){ n.callMethod?
        n.callMethod.apply(n,arguments):n.queue.push(arguments) };
        if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
        n.queue=[ ];t=b.createElement(e);t.async=!0;
        t.src=v;s=b.getElementsByTagName(e)[ 0 ];
        s.parentNode.insertBefore(t,s) }(window, document,'script',
        'https://connect.facebook.net/en_US/fbevents.js');
        fbq('init', '[[++facebook_pixel_id]]');
        fbq('track', 'PageView');
    </script>
    <noscript><img height="1" width="1" style="display:none" src="https://www.facebook.com/tr?id=[[++facebook_pixel_id]]&ev=PageView&noscript=1"/></noscript>
```

Dieser Dienst kann mit der [Facebook Pixel Dienst YAML
Datei](../yaml/consentfriend_facebookPixel.yml) importiert werden.

### Google Tag Manager

| Einstellung                    | Wert |
|--------------------------------|------|
| Code-Abschnitt                 | HEAD |
| Aktiv                          | Nein |
| Standard                       | Nein |
| Erforderlich                   | Nein |
| Opt-out                        | Nein |
| Nur einmalig                   | Nein |
| Nur Kontextbezogene Zustimmung | Nein |

#### Code

```html
    <script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
    new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
    j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
    'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
    })(window,document,'script','dataLayer','[[++google_tag_manager_id]]');</script>
```

#### Callbacks

#### On Init

```js
    function (opts) {
        // initialization code here (will be executed only once per page-load)
        window.dataLayer = window.dataLayer || [];
        window.gtag = function () {
            dataLayer.push(arguments);
        }
        gtag('consent', 'default', {'ad_storage': 'denied', 'ad_user_data': 'denied', 'ad_personalization': 'denied', 'analytics_storage': 'denied'});
        gtag('set', 'ads_data_redaction', true);
    }
```

#### On Accept

```js
    function (opts) {
        // we notify the tag manager about all services that were accepted. You can define
        // a custom event in GTM to load the service if consent was given.
        for (let k of Object.keys(opts.consents)) {
            if (opts.consents[k]) {
                let eventName = 'consentfriend-' + k + '-accepted';
                dataLayer.push({'event': eventName});
            }
        }
        // if consent for Google Analytics was granted we enable analytics storage
        if (opts.consents['googleAnalytics']) {
            console.log('Google analytics usage was granted!');
            gtag('consent', 'update', {'analytics_storage': 'granted'});
        }
        // if consent for Google Ads was granted we enable ad storage
        if (opts.consents['googleAdSense']) {
            console.log('Google ads usage was granted!');
            gtag('consent', 'update', {'ad_storage': 'granted'});
        }
    }
```

#### On Decline

```js
    function (opts) {
        // we notify the tag manager about all services that were declined. You can define
        // a custom event in GTM to unload the service if consent was denied.
        window.dataLayer = window.dataLayer || [];
        window.gtag = function () {
            dataLayer.push(arguments)
        }
        gtag('consent', 'default', {'ad_storage': 'denied', 'ad_user_data': 'denied', 'ad_personalization': 'denied', 'analytics_storage': 'denied'})
        gtag('set', 'ads_data_redaction', true)
    }
```

Dieser Dienst kann mit der [Google Tag Manager Dienst YAML
Datei](../yaml/consentfriend_googleTagManager.yml) importiert werden.

### Google Maps

| Setting                        | Value |
|--------------------------------|-------|
| Aktiv                          | No    |
| Standard                       | No    |
| Erforderlich                   | No    |
| Opt-out                        | No    |
| Nur einmalig                   | No    |
| Nur Kontextbezogene Zustimmung | No    |

Dieser Dienst kann mit der [Google Maps Dienst YAML
Datei](../yaml/consentfriend_googleMaps.yml) importiert werden.

Es gibt ein [Beispiel](Google_Maps.md) für die erweiterte Konfiguration des
Google Maps Dienstes.
