---
title: "Custom textures and skymaps"
bookIcon: "panorama"
---

# Custom textures

Custom textures are accepted in the form of DDS files.

## What is a DDS file?

DDS is a container format for GPU-native textures. The image data is ready to be uploaded to the GPU.

The image data of a DDS file can use various raw and compressed formats, with some of these focusing on specific use cases.

## Recommended formats

These formats are generally available on all modern desktop+laptop GPUs. For ARM SoC's and such, you may need to do your own research.

Some of the common compression formats and their use cases:

- `BC1`: When low VRAM use is desired. No transparency. (aka DXT1)
- `BC3`: When transparency and/or fast compression times are desired. (aka DXT5)
- `BC7`: When transparency and/or high quality is desired.

`BC7` is recommended for skyboxes, as it shows less banding artifacts.

## Convert standard picture to DDS: Texpresso

Texpresso does not support `BC7`, so if you're working on a skybox, try Compressonator instead!

[Texpresso](https://github.com/jansol/texpresso) is available via Cargo:

```bash
cargo install texpresso_cli
```

Usage example:

```bash
texpresso compress --format BC3 path/to/image.png
```

The resulting .dds file will be placed in your working directory.

## Convert standard picture to DDS: Compressonator

Compressonator is a set of open-source graphics utilities by AMD.

[Compressonator Website](https://gpuopen.com/compressonator/)・[Download Compressonator](https://github.com/GPUOpen-Tools/Compressonator/releases)

Example usage:

```bash
compressonatorcli -nomipmap -fd BC7 ~/Downloads/table_mountain_2_puresky.png ~/.config/wayvr/table_mountain_2.dds
```

## Convert standard picture to DDS: GIMP

GIMP supports .dds image import/export out of the box.

To export it, go to `File -> Export As...`, and then select your output filename with `.dds` at the end.

Select your compression type, for example BC3.

Be aware GIMP doesn't support BC7 compression.
