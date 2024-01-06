---
layout: default-layout
title: Interface NormalizedImagesResult - Dynamsoft Label Recognizer JS Edition API Reference
description: This page shows the JS edition of the interface NormalizedImagesResult.
keywords: normalized image, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# NormalizedImagesResult

An interface represents the result of normalized images. It includes properties such as originalImageHashId, originalImageTag, and normalizedImageResultItems (an array of `NormalizedImageResultItem` objects).

## Definition

```ts
interface NormalizedImagesResult {
    readonly originalImageHashId: string;
    readonly originalImageTag: ImageTag;
    normalizedImageResultItems: Array<NormalizedImageResultItem>;
}
```

| Properties              | Type |
|----------------------|-------------|
| [`originalImageHashId`](#originalimagehashid) | *string* |
| [`originalImageTag`](#originalimagetag) | *ImageTag* |
| [`normalizedImageResultItems`](#normalizedimageresultitems) | *Array\<NormalizedImagesResult>* |

### originalImageHashId

Gets the hash ID of the original image.

```ts
readonly originalImageHashId: string;
```

### originalImageTag

Gets the tag of the original image.

```ts
readonly originalImageTag: ImageTag;
```

### normalizedImageResultItems

An array of NormalizedImageResultItem objects, represented by Array<NormalizedImageResultItem>.

```ts
normalizedImageResultItems: Array<NormalizedImageResultItem>;
```