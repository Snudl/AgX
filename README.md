This is an OCIO config adapted from the HDR-Experimental branches of [EaryChow AgX](https://github.com/EaryChow/AgX/tree/HDR-Experimental) and [EaryChow LUT Gen](https://github.com/EaryChow/AgX_LUT_Gen/tree/HDR_Experimental). In addition to all the existing definitions including `Rec.2100-HLG` and `Rec.2100-PQ`, it adds `AgX HDR` presets to extended `sRGB` under `Display Device`, outputting floating-point color values above 1.0 for HDR brightness beyond the SDR peak white reference and negative values for achieving wider than sRGB gamut colors.

The presets represent a 100 nits SDR reference extending HDR peak brightness by 1.5x to 150 nits, 2x to 200 nits, 3x to 300 nits, 4x to 400 nits, 5x to 500 nits, and the original 10x to 1000 nits. All derive from their corresponding HLG with P3 limited gamut LUT created by the generator.

Change the OCIO `View Transform` from `Standard` to the `AgX HDR` preset that best fits the SDR and HDR peak brightness targets in your system settings. For example AgX HDR 2x matches 500 nits SDR and 1000 nits HDR.

Any application utilizing OCIO configs for color management can use it, but only gets the unclipped highlights if it supports HDR display output to those targets. The `Look` presets being explicitly defined may pollute the list with duplicate entries outside of Blender.

Your HDR display may also add its own tone mapping on top, showing a less accurate result. This is often the default on HDR capable TVs, and can be fixed by setting its tone mapping option to None or HGIG, if available.

Blender currently only supports HDR output through the Vulkan backend on Linux with an HDR capable Wayland compositor. See the [Developer Forum post](https://devtalk.blender.org/t/vulkan-wayland-hdr-support/41214).