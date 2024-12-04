---
title: Text Translation Options
---

## DeepL Text Translation Options

The following options can be set in
`babeltranslate.deepl_text_translation_options`. The exact description and the
possible values can be found in the [DeepL API
documentation](https://developers.deepl.com/docs/api-reference/translate/openapi-spec-for-text-translation).

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

These example options are not tested. The expample just lists the options that
are currently possible according to the DeepL API documentation. Maybe the empty
tag list options don't work. So use only the options, that you want to use.
