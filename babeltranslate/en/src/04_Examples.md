---
title: Examples
---

## ContentBlocks fields

The following example system setting in
`babeltranslate.translate_resource_cb_fields` manages the translation of
ContentBlocks fields. The first three fields are based on the standard field
configuration that can be installed with ContentBlocks. A field content can be
released for translation directly with the type `text`. An existing or
additional text field in a ContentBlocks field can be released for translation
with the type `single` or `grid` in the `fields` array. A repeater can be
released for translation with the type `repeater`. ContentBlocks fields within a
repeater are released for translation with the key of the respective field.

The type `text`, `single` or `grid` is to be used depending on the ContentBlocks
field type.

The following ContentBlocks fields are of type `text`:

- `code`
- `heading`
- `link`
- `quote`
- `richtext`
- `textarea`
- `textfield`

The following ContentBlocks fields are of type `single`:

- `image_with_title`

The following ContentBlocks fields are of type `grid`:

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

The following example system setting in `babeltranslate.translate_resource_tvs`
manages the translation of template variables fields. A template variable
content can be released for translation directly with the type `text`. An
existing nested template variable text can be released for translation with the
type `single` or `grid` in the `fields` array. A custom template variable can be
released for translation with the type `custom` and a plugin in the
`OnBabelTranslateCustomTV` event.

The type `text`, `single` or `grid` is to be used depending on the template
variable type.

The most template variable types are of type `text`.

The following template variable types are of type `single`:

- `imageplus`

The following template variable types are of type `grid`:

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
