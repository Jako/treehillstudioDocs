---
title: Extended Fields
---

Some tables in Cursus can use predefined extended fields. The values of these
fields are saved as a JSON-encoded array in a text field. Sorting and filtering
by extended fields is therefore not possible.

## Event Fields

The events in Cursus can use extended fields. To define the extended fields, the
system setting `cursus.extended_event_fields` has to be filled with a nested
JSON encoded array. The following value gives an example:

``` json
[
  {
    "fields": [
      {
        "xtype": "cursus-combo-price",
        "name": "member_price",
        "renderer": "Cursus.util.priceRendererShow",
        "label": "Price Member",
        "width": 0.5,
        "column_label": "Member",
        "column_width": 50,
        "hidden": false
      },
      {
        "xtype": "cursus-combo-price",
        "name": "siblings_price",
        "renderer": "Cursus.util.priceRendererShow",
        "label": "Sibling price",
        "width": 0.5,
        "column_label": "Siblings",
        "column_width": 50,
        "hidden": false
      }
    ]
  }, {
    "fields": [
      {
        "xtype": "cursus-combo-price",
        "name": "special_price",
        "renderer": "Cursus.util.priceRendererShow",
        "label": "Price Special Offer",
        "width": 0.5,
        "column_label": "Special Offer",
        "column_width": 50,
        "hidden": false
      }, {
        "name": "special_text",
        "label": "Text Special Offer",
        "width": 0.5
      }
    ]
  }, {
    "xtype": "modx-texteditor",
    "name": "meeting_point",
    "label": "Meeting point"
  }
]
```

It will add the fields price, and the fields minimum and maximum in two columns
to the event create/update window.

Each array will create one extended field. The `name` key is required. The
`label` key will be used, when it exists. Otherwise, a lexicon entry with the
field name prefixed by `cursus.extended.` is searched in the lexicon. An `xtype`
key will be used, when it exists. Otherwise, the xtype defaults to `textfield`.
A `renderer` key will be used, when it exists. The renderer can be defined in
the file referenced in the `cursus.extended_xtypes_script` system setting.

If a nested `fields` key contains an array value, this value will be used for
subfields in columns. The `width` key inside is then used for the subfield
column width.

The extended fields can also generate columns in the events grid. The
`column_label` key is required to add a column in the grid. The `column_width`
key will define the width of the grid column. The column_width defaults to 100.
The column can be hidden in the grid with the `hidden` key.

Extended fields are available as placeholder with the prefix `extended` in the
event row template. The `price` field from the example will be available with
the `[[+extended.price]]` placeholder.

The setting can use `@FILE` or `@CHUNK` bindings. Path
placeholders like `{core_path}`, `{base_path}` and `{assets_path}` can be used.
All paths have to stay inside the MODX base path because of security reasons.

## User Fields

The fields are defined in the system setting `cursus.extended_user_fields`.
They work the same as the extended event fields, can use `@FILE` or `@CHUNK`
bindings and are shown in the edit participant window and the participants grid.

## Trainer Fields

The fields are defined in the system setting `cursus.extended_trainer_fields`.
They work the same as the extended event fields, can use `@FILE` or `@CHUNK`
bindings and are shown in the edit trainer window and the trainers grid.
