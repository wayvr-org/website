---
title: "Video"
---

## Video component

### `<Video>`

### A playable video.

Internally, wgui uses [dav1d](https://code.videolan.org/videolan/dav1d) codec for video playback.

Supported video codec: **AV1**

Supported video container: **Duck IVF (.ivf)**

### Video conversion (ffmpeg):

```sh
ffmpeg -i input.mkv -c:v libsvtav1 -preset 3 -qp 50 output.ivf
```

`-i input.mkv`: Input video footage

`-c:v libsvtav1`: Use AV1 encoder

`-preset 3`: Encoder effort (1: very slow, good quality, 9: very fast)

`-qp 50`: Video quality (1: Nearly lossless, 63: Very low quality)

---

#### Parameters

`src` | `src_ext` | `src_builtin` | `src_internal`: **string**

_.ivf Video path_

`speed`: **float** (default: 1.0)

_Playback speed multiplier_

`looping`: **int** (default: 0)

_Play video infinitely instead of once_
