---
title: "Wgui Framework"
bookFlatSection: false
bookCollapseSection: true
bookIcon: "wgui_logo_traced"
weight: 4
---

{{% center %}}

<h1>Wgui Framework</h1>

![wgui logo](wgui_logo.webp)

{{% /center %}}

This is a non-immediate-mode GUI library for rendering widgets using Vulkan. It's internally used by WayVR.

# Quick jump

## Widgets

[div](widgets/div), [label](widgets/label), [rectangle](widgets/rectangle), [sprite](widgets/sprite)

## Built-in components

[Button](components/button), [Slider](components/slider), [CheckBox](components/checkbox), [Tabs](components/tab) ([Tab](components/tab)), [EditBox](components/editbox), [RadioBox](components/radiobox)

## Examples

[Simple layout](examples/simple_layout)

[Value substitution (themes)](examples/value_substitution)

[File inclusion](examples/file_inclusion)

[Macros](examples/macros)

[Templates](examples/templates)

# Universal widget attributes

_They can be used in any widget/component._

`display`: "flex" | "block" | "grid"

`position`: "absolute" | "relative"

`flex_grow`: **float**

`flex_shrink`: **float**

`gap`: **float** | **percent**

`flex_basis`: **float** | **percent**

`justify_self`: "center" | "end" | "flex_end" | "flex_start" | "start" | "stretch"

`justify_content`: "center" | "end" | "flex_start" | "flex_end" | "space_around" | "space_between" | "space_evenly" | "start" | "stretch"

`flex_wrap`: "wrap" | "no_wrap" | "wrap_reverse"

`flex_direction`: "row" | "column" | "column_reverse" | "row_reverse"

`align_items`, `align_self`: "baseline" | "center" | "end" | "flex_start" | "flex_end" | "start" | "stretch"

`box_sizing`: "border_box" | "content_box"

`margin`, `margin_left`, `margin_right`, `margin_top`, `margin_bottom`: **float** | **percent**

`padding`, `padding_left`, `padding_right`, `padding_top`, `padding_bottom`: **float** | **percent**

`overflow`, `overflow_x`, `overflow_y`: "hidden" | "visible" | "clip" | "scroll"

`min_width`, `min_height`: **float** | **percent**

`max_width`, `max_height`: **float** | **percent**

`width`, `height`: **float** | **percent**

## Advanced attributes

`interactable`: "1" | "0"

_Set to 0 if you want to exclude this widget from altering the event state_

`consume_mouse_events`: "1" | "0"

_Used in case of overlapping pop-ups or windows, most notably applied to various backgrounds_

`new_pass`: "1" | "0"

_Set to 1 if you want to render overlapping pop-ups to properly render your widgets in order. Wgui renders with as few Vulkan drawcalls as possible, so this is your responsibility._

## Default Colors

_These colors can be defined by the user to control the color scheme. They always exists and can be used in any place a normal color could be used._

`~color_text`: default: white(#FFFFFF)
`~color_accent`: default: light blue(#21ADFF)
`~color_danger`: default: red(#E60000)
`~color_faded`: default: grey(#ABBDCC)
`~color_bg`: default: black(#00121ABF) (color_background in config)

_Only the default colors can be changed with the following suffixes._

`_translucent`

_Halves the alpha of the color._

`_10`
`_20`
`_30`
`_40`
`_50`

_Darkens the color by multiplying it with a percentage. `~color_accent_50` Would be half of the normal brightness but the same alpha. You can't combine the suffixes_
