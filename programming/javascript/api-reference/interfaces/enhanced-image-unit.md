---
layout: default-layout
title: Interface EnhancedImagesUnit - Dynamsoft Document Normalizer JS Edition API Reference
description: This page shows the JS edition of the interface EnhancedImagesUnit.
keywords: enhanced image, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# EnhancedImagesUnit

The `EnhancedImagesUnit` interface extends the `IntermediateResultUnit` interface and represents a unit of enhanced images.

```ts
interface EnhancedImagesUnit extends IntermediateResultUnit {
    enhancedImage: EnhancedImageElement;
}
```

## EnhancedImage

`EnhancedImageElement` objects, representing a piece of the original image after enhancing.

```ts
enhancedImages: EnhancedImageElement;
```

**See Also**

[IntermediateResultUnit](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/intermediate-results/intermediate-result-unit.html)

[EnhancedImageElement](./enhanced-image-element.md)