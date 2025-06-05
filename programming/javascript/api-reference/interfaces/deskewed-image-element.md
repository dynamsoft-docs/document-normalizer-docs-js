---
layout: default-layout
title: Interface DeskewedImageElement - Dynamsoft Document Normalizer JS Edition API Reference
description: This page shows the JS edition of the interface DeskewedImageElement.
keywords: deskewed image, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# DeskewedImageElement

The `DeskewedImageElement` interface extends the `RegionObjectElement` interface and represents a deskewed image element.

```ts
interface DeskewedImageElement extends RegionObjectElement {
    imageData: DSImageData;
    sourceLocation: Quadrilateral;
    referencedElement: RegionObjectElement;
}
```

## imageData

The image data for the deskewed image.

## sourceLocation

The source location where the deskewed image was extracted from the original image, represented as a quadrilateral.

**See Also**

[Quadrilateral](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/quadrilateral.html)

**See Also**

[DSImageData](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/ds-image-data.html)

## referencedElement

The original element that this deskewed image was referenced from.

[RegionObjectElement](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/intermediate-results/region-object-element.html)
