---
title: Textübersetzungsoptionen
---

## DeepL Textübersetzungsoptionen

Die folgenden Optionen können in in
`babeltranslate.deepl_text_translation_options` gesetzt werden. Die genaue
Beschreibung und die möglichen Werte können in der [DeepL API
Dokumentation](https://developers.deepl.com/docs/api-reference/translate/openapi-spec-for-text-translation)
gefunden werden.

``` json
{
  "split_sentences": "1",
  "preserve_formatting": false,
  "formality": "default",
  "glossary_id": "",
  "tag_handling": "",
  "outline_detection": true,
  "non_splitting_tags": "",
  "splitting_tags": "",
  "ignore_tags": "",
}
```

Diese Beispieloptionen werden nicht getestet. Das Beispiel listet nur die
Optionen auf, die laut der DeepL API-Dokumentation derzeit möglich sind.
Möglicherweise funktionieren die Optionen für die leere Tag-Liste nicht.
Verwenden Sie also nur die Optionen, die Sie verwenden möchten.
