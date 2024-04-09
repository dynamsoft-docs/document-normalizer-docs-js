---
layout: default-layout
title: Interface SimplifiedDocumentNormalizerSettings - Dynamsoft Document Normalizer JS Edition API Reference v2.2.10
description: This page shows the JS edition of the interface SimplifiedDocumentNormalizerSettings in Dynamsoft DDN Module v2.2.10.
keywords: simplified setting, document normalizer, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# SimplifiedDocumentNormalizerSettings

This interface defines simplified settings for document normalizer tasks.

## Definition

```typescript
interface SimplifiedDocumentNormalizerSettings {
    grayscaleEnhancementModes: Array<Core.EnumGrayscaleEnhancementMode>;
    grayscaleTransformationModes: Array<Core.EnumGrayscaleTransformationMode>;
    colourMode: EnumImageColourMode;
    pageSize: [number, number];
    brightness: number;
    contrast: number;
    scaleDownThreshold: number;
}
```

## grayscaleEnhancementModes

Set the grayscale enhancement modes with an array of enumeration `GrayscaleEnhancementMode`. View the reference page of `GrayscaleEnhancementModes` for more detail about grayscale enhancement modes.

```typescript
grayscaleEnhancementModes: Array<Core.EnumGrayscaleEnhancementMode>; 
```

**See also**

* [EnumGrayscaleEnhancementMode]({{ site.enums }}core/grayscale-enhancement-mode.html?lang=js)

## grayscaleTransformationModes

Set the grayscale transformation modes with an array of enumeration `GrayscaleTransformationMode`. View the reference page of `GrayscaleTransformationModes` for more detail about grayscale transformation modes.

```typescript
grayscaleTransformationModes: Array<Core.EnumGrayscaleTransformationMode>;
```

**See also**

* [EnumGrayscaleTransformationMode]({{ site.enums }}core/grayscale-transformation-mode.html?lang=js)

## colourMode

Sets the colour mode of the normalized image with enumeration `ImageColourMode`. View the reference page of `ImageColourMode` for more detail about colour mode.

```typescript
colourMode: EnumImageColourMode;
```

**See also**

* [EnumImageColourMode]({{ site.enums }}document-normalizer/image-colour-mode.html?lang=js)

## pageSize

Sets the page size (width by height in pixels) of the normalized image.

```typescript
pageSize: [number, number];
```

## brightness

Sets the brightness of the normalized image. The value range is [-100,100].

```typescript
brightness: number;
```

## contrast

Sets the contrast of the normalized image. The value range is [-100,100].

```typescript
contrast: number;
```

## scaleDownThreshold

Set the threshold for scaling down the input image during barcode localization. If the shorter edge size of the image is larger than this threshold,the original may be scaled down to reduce processing time. The default value is 2300.

```typescript
scaleDownThreshold: number;
```