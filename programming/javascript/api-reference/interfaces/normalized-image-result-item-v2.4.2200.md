---
layout: default-layout
title: Interface NormalizedImageResultItem - Dynamsoft Document Normalizer JS Edition API Reference
description: This page shows the JS edition of the interface NormalizedImageResultItem.
keywords: normalized image result, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# NormalizedImageResultItem

The `NormalizedImageResultItem` interface extends the `CapturedResultItem` interface and represents a normalized image result item.

```ts
interface NormalizedImageResultItem extends CapturedResultItem {
    imageData: DSImageData;
    location: Quadrilateral;
    toCanvas(): HTMLCanvasElement;
    toImage(MIMEType: "image/png" | "image/jpeg"): HTMLImageElement;
    toBlob(MIMEType: "image/png" | "image/jpeg"): Promise<Blob>;
    saveToFile(name: string, download?: boolean): Promise<File>;
}
```

## imageData

The image data for the normalized image result.

**See Also**

[DSImageData](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/ds-image-data.html)

## location

The location where the normalized image was extracted from within the original image, represented as a quadrilateral.

**See Also**

[Quadrilateral](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/quadrilateral.html)

## toCanvas

Converts the normalized image data into an HTMLCanvasElement for display or further manipulation in web applications.

**See Also**

[HTMLCanvasElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement)

## toImage

Converts the normalized image data into an HTMLImageElement of a specified MIME type ('image/png' or 'image/jpeg').

**See Also**

[HTMLImageElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLImageElement)

## toBlob

Converts the normalized image data into a Blob object of a specified MIME type ('image/png' or 'image/jpeg').

**See Also**

[Blob](https://developer.mozilla.org/en-US/docs/Web/API/Blob)

## saveToFile

Saves the normalized image to a File object in memory, optionally downloading it to the user's device.

**Parameters**

`name`: the name to assign to the File object.

`download` optional. If true, triggers the download of the file once created; otherwise, retains the file in memory.

**See Also**

[File](https://developer.mozilla.org/en-US/docs/Web/API/File)
