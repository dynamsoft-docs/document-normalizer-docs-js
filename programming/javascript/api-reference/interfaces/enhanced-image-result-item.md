---
layout: default-layout
title: Interface EnhancedImageResultItem - Dynamsoft Document Normalizer JS Edition API Reference
description: This page shows the JS edition of the interface EnhancedImageResultItem.
keywords: enhanced image result, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# EnhancedImageResultItem

The `EnhancedImageResultItem` interface extends the `CapturedResultItem` interface and represents a enhanced image result item.

```ts
interface EnhancedImageResultItem extends CapturedResultItem {
    imageData: DSImageData;
    location: Quadrilateral;
    toCanvas(): HTMLCanvasElement;
    toImage(MIMEType: "image/png" | "image/jpeg"): HTMLImageElement;
    toBlob(MIMEType: "image/png" | "image/jpeg"): Promise<Blob>;
}
```

## imageData

The image data for the enhanced image result.

**See Also**

[DSImageData](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/ds-image-data.html)

## location

The location where the enhanced image was extracted from within the original image, represented as a quadrilateral.

**See Also**

[Quadrilateral](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/quadrilateral.html)

## toCanvas

Converts the enhanced image data into an HTMLCanvasElement for display or further manipulation in web applications.

**See Also**

[HTMLCanvasElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement)

## toImage

Converts the enhanced image data into an HTMLImageElement of a specified MIME type ('image/png' or 'image/jpeg').

**See Also**

[HTMLImageElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLImageElement)

## toBlob

Converts the enhanced image data into a Blob object of a specified MIME type ('image/png' or 'image/jpeg').

**See Also**

[Blob](https://developer.mozilla.org/en-US/docs/Web/API/Blob)
