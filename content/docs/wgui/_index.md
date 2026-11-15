---
title: "Wgui Framework"
bookFlatSection: false
bookCollapseSection: true
bookIcon: "wgui_logo_traced"
weight: 4
description: "Vulkan-based GUI library for WayVR - widgets, components, and theming."
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

`min_width`, `min_height`: **float** | **percent** | "auto"

`max_width`, `max_height`: **float** | **percent** | "auto"

`width`, `height`: **float** | **percent** | "auto"

`aspect_ratio`: **float**

## Advanced attributes

`interactable`: "true" | "false"

_Set to 0 if you want to exclude this widget from altering the event state_

`consume_mouse_events`: "true" | "false"

_Used in case of overlapping pop-ups or windows, most notably applied to various backgrounds_

`new_pass`: "true" | "false"

_Set to 1 if you want to render overlapping pop-ups to properly render your widgets in order. Wgui renders with as few Vulkan drawcalls as possible, so this is your responsibility._

## Palette Colors

_These colors can be defined by the user to control the color scheme. They always exist and can be used in any place a normal color could be used. Names are case-sensitive._

`primary`, `on_primary`, `secondary`, `on_secondary`, `tertiary`, `on_tertiary`, `danger`, `on_danger`, `background`, `on_background`, `background_variant`, `on_background_variant`, `background_contrast`, `on_background_contrast`, `success`, `on_success`, `outline`, `highlight`, `shadow`

_wgui_ also supports specifying color modifiers, like so:

`primary(opacity-0.5)`

_Sets the opacity to 50%_

`primary(opacity-0.95)`

_Sets the opacity to 95%_

`primary(transparent)`

_Sets the opacity to 0.0_

`primary(opaque)`

_Sets the opacity to 1.0_

`primary(rgb-mult-0.5)`

_Multiplies RGB values by 0.5 (darker color)_

`primary(rgb-add-0.5)`

_Adds 0.5 to RGB channels_

`primary(opacity-0.5,rgb-mult-0.75,rgb-add-0.25)`

_Sets opacity to 0.5, multiplies RGB by 0.75 and adds RGB by 0.25_
