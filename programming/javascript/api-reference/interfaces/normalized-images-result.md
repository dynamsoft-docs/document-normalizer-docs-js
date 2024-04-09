---
layout: default-layout
title: Interface NormalizedImagesResult - Dynamsoft Document Normalizer JS Edition API Reference
description: This page shows the JS edition of the interface NormalizedImagesResult.
keywords: normalized image, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# NormalizedImagesResult

The `NormalizedImagesResult` interface holds information on normalized images, of type `NormalizedImageResultItem`, derived from an original image.

## Definition

```ts
interface NormalizedImagesResult {
    readonly errorCode: number;
    readonly errorString: string;
    readonly originalImageHashId: string;
    readonly originalImageTag: ImageTag;
    readonly normalizedImageResultItems: Array<NormalizedImageResultItem>;
}
```


## errorCode

Error code associated with the capture result.

## errorString

Error string providing details about the error.

## originalImageHashId

The hash ID of the original image.

## originalImageTag

The tag associated with the original image.

**See Also**

[ImageTag](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/image-tag.html)

## normalizedImageResultItems

An array of `NormalizedImageResultItem` objects, each representing a piece of the original image after normalization.

**See Also**

[NormalizedImageResultItem](./normalized-image-result-item.md)
