---
title: "Button"
---

## Button component

### `<Button>`

### A clickable, decorated button

#### Parameters

`text`: **string**

_Simple text_

`translation`: **string**

_Translated by key_

`round`: **float** (default: 4) | **percent** (0-100%)

`border`: **float** (default: 2)

`color`: #FFAABB | #FFAABBCC

`border_color`: #FFAABB | #FFAABBCC

`hover_color`: #FFAABB | #FFAABBCC

`hover_border_color`: #FFAABB | #FFAABBCC

`tooltip`: **string**

_Tooltip text on hover, translated by key_

`tooltip_str`: **string**

_Tooltip text on hover, raw text (not translated)_

`tooltip_side`: "top" | "bottom" | "left" | "right" (default: top)

`sticky`: "1" | "0" (default: "0")

_make button act as a toggle (visual only)_

`sprite_src` | `sprite_src_ext` | `sprite_src_builtin` | `sprite_src_internal`

_Image path (see [sprite](#sprite-widget)) for src descriptions_

#### Info

Child widgets are supported and can be added directly in XML.
