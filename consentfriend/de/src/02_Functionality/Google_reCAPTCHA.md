---
title: Google reCAPTCHA 
---

Um das automatische Laden und Ausführen des reCAPTCHA-Skripts zu deaktivieren,
müssen Sie müssen Sie z.B. den Chunk recaptchav3_html mit dem folgenden Code
ändern:

```html
<script type="application/javascript">
    function loadCaptcha() {
        grecaptcha.ready(function() {
            grecaptcha.execute('[[+site_key]]', {action: '[[+form_id]]'}).then(function(token) {
                document.querySelector('[name="[[+token_key]]"]').value = token;
            });
        });
    }
</script>
<script onload="loadCaptcha()" type="text/plain" data-type="application/javascript" data-src="https://www.google.com/recaptcha/api.js?render=[[+site_key]]&hl=[[++cultureKey]]" data-name="googleRecaptcha"></script>
<input type="hidden" name="[[+token_key]]">
<input type="hidden" name="[[+action_key]]" value="[[+form_id]]">
```

Da die Reihenfolge der Ausführung der Javascripte, wenn sie von Klaro! aktiviert
werden, nicht eindeutig festgelegt ist, muss die Methode `grecaptcha.ready` von
einer Methode aufgerufen werden, die die nach dem Laden des reCAPTCHA-Skripts
mit dem onload-Attribut ausgeführt wird. Andernfalls erhält man eventuell einen
`Uncaught ReferenceError: grecaptcha is not defined` Fehler in der
Browserkonsole und reCAPTCHA funktioniert in diesem Fall nicht.

### Deaktivieren der Inputs/Buttons

Die Formulare, die durch reCAPTCHA gesichert sind, können mit einer
Callback-Funktion anhand des Zustimmungsstatus vom reCAPTCHA-Dienst geändert
werden. Der folgende Code ist in den Demo-Daten im onToggle-Callback vom
reCAPTCHA-Dienst vordefiniert:

```js
function(consent, service) {
    var buttons = document.body.querySelectorAll('input[data-name="' + service.name + '"],button[data-name="' + service.name + '"]'), index;
    for (index = 0; index < buttons.length; index++) {
       buttons[index].disabled = !consent;
    }
}
```

Dieser Code deaktiviert alle Inputs/Buttons mit `data-name="googleRecaptcha"`,
wenn keine Zustimmung für diesen Dienst erteilt wird und aktiviert die Inputs/Buttons,
sobald die Zustimmung gegeben wird.

### Deaktivieren des Submit-Button

Eine andere Möglichkeit ist es, den Submit-Button des Formulars zu deaktivieren
und bei Bedarf ein modales Fenster zum Aktivieren des reCAPTCHA-Dienstes
anzuzeigen. Im Folgenden gibt es unterschiedliche Beispiele für den onToggle-Callback.

#### jQuery/Bootstrap 5:

**onToggle Code**

```js
function(consent, service) {
    var button = $('button[data-name="' + service.name + '"], input[type="submit"][data-name="' + service.name + '"]');
    button.css('display', 'inline-block');
    if (!consent) {
        button.on('click', function(event) {
            var recaptchaModal = new bootstrap.Modal(document.getElementById('recaptchaModal'));
            recaptchaModal.show();
            event.preventDefault();
        });
    } else {
        button.off('click');
    }
}
```

**Code für modales Fenster**

```html
<div class="modal fade" id="recaptchaModal" tabindex="-1" aria-labelledby="recaptchaModalLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="recaptchaModalLabel">reCAPTCHA service needed</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
        <p>You have disabled the reCAPTCHA service in the consent settings. This service provides spam protection for our forms. The forms cannot be submitted without enabling the reCAPTCHA service. Please <a data-bs-dismiss="modal" onclick="klaro.show(window.consentFriendConfig, { modal: true });return false;">enable</a> the service in the settings. Alternatively, you can send us an <a href="mailto:[[++emailsender]]">email</a>.</p>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
      </div>
    </div>
  </div>
</div>
```

#### Javascript/Tailwind CSS

**onToggle Code**

```js
function(consent, service) {
    window.consentFriend = window.consentFriend || {};
    window.consentFriend.recaptcha = consent;
    window.consentFriend.recaptchaModal = document.getElementById('recaptcha-modal')
    window.consentFriend.recaptchaButtons = document.body.querySelectorAll('input[data-name="' + service.name + '"],button[data-name="' + service.name + '"]');
    if (window.consentFriend.recaptchaModal && window.consentFriend.recaptchaButtons) {
        if (!window.consentFriend.recaptchaListeners) {
            document.getElementById('recaptcha-modal-change').addEventListener('click', function () {
                window.consentFriend.recaptchaModal.classList.add('hidden');
                klaro.show();
            });
            document.getElementById('recaptcha-modal-close').addEventListener('click', function () {
                window.consentFriend.recaptchaModal.classList.add('hidden');
            });
        }
        var index;
        for (index = 0; index < window.consentFriend.recaptchaButtons.length; index++) {
            var button = window.consentFriend.recaptchaButtons[index];
            button.style.display = 'inline-block';
            button.disabled = false;
            if (!window.consentFriend.recaptchaListeners) {
                button.addEventListener('click', function (evt) {
                    if (!window.consentFriend.recaptcha) {
                        evt.preventDefault();
                        window.consentFriend.recaptchaModal.classList.remove('hidden');
                    }
                });
            }
        }
    window.consentFriend.recaptchaListeners = true;
    }
}
```

**Code für modales Fenster**

```html
<div id="recaptcha-modal" class="hidden fixed z-10 inset-0 overflow-y-auto" aria-labelledby="modal-title" role="dialog" aria-modal="true">
    <div class="flex items-end justify-center min-h-screen pt-4 px-4 pb-20 text-center sm:block sm:p-0">
        <div aria-hidden="true" class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity"></div>
        <span aria-hidden="true" class="hidden sm:inline-block sm:align-middle sm:h-screen">&#8203;</span>
        <div class="inline-block align-bottom bg-white rounded px-4 pt-5 pb-4 text-left overflow-hidden shadow-xl transform transition-all sm:my-8 sm:align-middle sm:max-w-lg sm:w-full sm:p-6">
            <div class="sm:flex sm:items-start">
                <div class="mx-auto flex-shrink-0 flex items-center justify-center h-12 w-12 rounded-full bg-red-100 sm:mx-0 sm:h-10 sm:w-10">
                    <svg aria-hidden="true" class="h-6 w-6 text-red-600" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                        <path d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"/>
                    </svg>
                </div>
                <div class="mt-3 text-center sm:mt-0 sm:ml-4 sm:text-left">
                    <h3 class="text-lg leading-6 font-bold text-gray-900" id="modal-title">
                        reCAPTCHA service needed
                    </h3>
                    <div class="mt-2">
                        <p class="text-md text-gray-600">
                            You have disabled the reCAPTCHA service in the consent settings. This service provides spam protection for our forms. The forms cannot be submitted without enabling the reCAPTCHA service.<br><br>
                            Please <a id="recaptcha-modal-change" class="cursor-pointer text-gray-600 hover:text-gray-900 transition duration-150 ease-in-out">enable</a> the service in the settings. Alternatively, you can send us an <a class="cursor-pointer text-gray-600 hover:text-gray-900 transition duration-150 ease-in-out" href="mailto:[[++emailsender]]">email</a>.
                        </p>
                    </div>
                </div>
            </div>
            <div class="mt-5 sm:mt-4 sm:flex sm:flex-row-reverse">
                <button id="recaptcha-modal-close" class="mt-3 w-full sm:w-auto inline-flex justify-center btn btn-orange" type="button">
                    [[%close]]
                </button>
            </div>
        </div>
    </div>
</div>
```
