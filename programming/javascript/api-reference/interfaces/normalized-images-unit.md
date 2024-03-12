---
layout: default-layout
title: Interface NormalizedImagesUnit - Dynamsoft Document Normalizer JS Edition API Reference
description: This page shows the JS edition of the interface NormalizedImagesUnit.
keywords: normalized image, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# NormalizedImagesUnit

The `NormalizedImagesUnit` interface extends the `IntermediateResultUnit` interface and represents a unit of normalized images.

```ts
interface NormalizedImagesUnit extends IntermediateResultUnit {
    normalizedImages: Array<NormalizedImageElement>;
}
```

## normalizedImages

An array of `NormalizedImageElement` objects, each representing a piece of the original image after normalization.

```ts
normalizedImages: Array<NormalizedImageElement>;
```

**See Also**

[IntermediateResultUnit](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/intermediate-results/intermediate-result-unit.html)

[NormalizedImageElement](./normalized-image-element.md)