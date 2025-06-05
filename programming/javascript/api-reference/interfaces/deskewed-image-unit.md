---
layout: default-layout
title: Interface DeskewedImagesUnit - Dynamsoft Document Normalizer JS Edition API Reference
description: This page shows the JS edition of the interface DeskewedImagesUnit.
keywords: deskewed image, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# DeskewedImagesUnit

The `DeskewedImagesUnit` interface extends the `IntermediateResultUnit` interface and represents a unit of deskewed images.

```ts
interface DeskewedImagesUnit extends IntermediateResultUnit {
    deskewedImage: DeskewedImageElement;
}
```

## deskewedImage

`DeskewedImageElement` objects, representing a piece of the original image after deskewing.

```ts
deskewedImages: DeskewedImageElement;
```

**See Also**

[IntermediateResultUnit](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/intermediate-results/intermediate-result-unit.html)

[DeskewedImageElement](./deskewed-image-element.md)