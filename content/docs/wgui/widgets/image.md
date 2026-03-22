## image widget

### `<image>`

### Image widget for large images

Always set the `width` & `height` of an `<image>`!

Supported formats: svg, png, jpeg, gif, webp

Maximum image size: Max texture size for the GPU (usually 8K+)

For small images such as icons, consider using the `<sprite>` tag instead.

`<image>` requires a single draw call per widget, while `<sprite>` widgets all share a single draw call per panel.

#### Parameters

`src`: **string**

_External (filesystem) image path. Falls back to Internal (assets) if not found._

`src_ext`: **string**

_External (filesystem) image path_

`src_builtin`: **string**

_Internal (assets) image path_

`src_internal`: **string**

_wgui internal image path. Do not use directly unless it's related to the core wgui assets._

`round`: **float** (default: 0) | **percent** (0-100%)

`border`: **float**

`border_color`: #FFAABB | #FFAABBCC
