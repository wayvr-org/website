## sprite widget

### `<sprite>`

### Image widget for small images

Always set the `width` & `height` of a `<sprite>`!

Supported formats: svg, png, jpeg, gif, webp

Maximum image size: 256x256 pixels

For large or frequently changing images (e.g. album art), or if borders/rounding is desired, consider the `<image>` tag instead.

Sprite images are atlassed, making them very efficient to render.

Adding large sprites permanently increases the atlas size (and thus VRAM usage) for the session. (Atlas space can be re-used, but the atlas won't shrink back.)

#### Parameters

`src`: **string**

_External (filesystem) image path. Falls back to Internal (assets) if not found._

`src_ext`: **string**

_External (filesystem) image path_

`src_builtin`: **string**

_Internal (assets) image path_

`src_internal`: **string**

_wgui internal image path. Do not use directly unless it's related to the core wgui assets._
