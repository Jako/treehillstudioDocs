---
title: Beispiele
---

## ContentBlocks fields

Die folgende Beispiel-Systemeinstellung in
`babeltranslate.translate_resource_cb_fields` verwaltet die Übersetzung von
ContentBlocks-Feldern. Die ersten drei Felder basieren auf der
Standardfeldkonfiguration, die mit ContentBlocks installiert werden kann. Ein
Feldinhalt kann direkt mit dem Typ `text` zur Übersetzung freigegeben werden.
Ein bestehendes oder zusätzliches Textfeld in einem ContentBlocks-Feld kann mit
dem Typ `single` oder `grid` im Array `fields` für die Übersetzung freigegeben
werden. Ein Repeater kann mit dem Typ `repeater` für die Übersetzung freigegeben
werden. ContentBlocks Felder innerhalb eines Repeaters werden mit dem Schlüssel
des jeweiligen Feldes zur Übersetzung freigegeben.

Je nach ContentBlocks Feldtyp ist der Typ `text`, `single` oder `grid` zu
verwenden.

Die folgenden ContentBlocks Felder sind vom Typ `Text`:

- `code`
- `heading`
- `link`
- `quote`
- `richtext`
- `textarea`
- `textfield`

Die folgenden ContentBlocks-Felder sind vom Typ `single`:

- `image_with_title`

Die folgenden ContentBlocks-Felder sind vom Typ `grid`:

- `gallery`
- `list`
- `ordered_list`
- `table`
- `file`

``` json
{
  "1": {
    "type": "text"
  },
  "8": {
    "type": "single",
    "fields": [
      "title"
    ]
  },
  "9": {
    "type": "grid",
    "nested": "images",
    "fields": [
      "title",
      "description"
    ]
  },
  "19": {
    "type": "repeater",
    "repeater": {
      "file": {
        "type": "grid",
        "nested": "files",
        "fields": [
          "title"
        ]
      }
    }
  }
}
```

## Template variables

Die folgende Beispiel-Systemeinstellung in
`babeltranslate.translate_resource_tvs` verwaltet die Übersetzung von
Template-Variablenfeldern. Der Inhalt einer Template-Variablen kann direkt mit
dem Typ `text` zur Übersetzung freigegeben werden. Eine bestehende
verschachtelte Template-Variable Text kann mit dem Typ `single` oder `grid` im
`fields`-Array zur Übersetzung freigegeben werden. Eine benutzerdefinierte
Template-Variable kann mit dem Typ `custom` und einem Plugin im Ereignis
`OnBabelTranslateCustomTV` für die Übersetzung freigegeben werden.

Je nach Typ der Template-Variable ist der Typ `text`, `single` oder `grid` zu
verwenden.

Die meisten Template-Variablen-Typen sind vom Typ `Text`.

Die folgenden Template-Variablen-Typen sind vom Typ `single`:

- `imageplus`

Die folgenden Template-Variablen-Typen sind vom Typ `grid`:

- `grid`

``` json
{
  "rte": {
    "type": "text"
  },
  "migx": {
    "type": "grid",
    "fields": [
      "title",
      "description"
    ]
  },
  "imageplus": {
    "type": "single",
    "fields": [
      "title",
      "description"
    ]
  },
  "special": {
    "type": "custom"
  }
}
```
