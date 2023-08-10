---
layout: default-layout
title: interface NormalizedImagesResult - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface NormalizedImagesResult in Dynamsoft Core Module.
keywords: normalized image, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# NormalizedImagesResult

An interface represents the result of normalized images. It includes properties such as originalImageHashId, originalImageTag, and normalizedImageResultItems (an array of `NormalizedImageResultItem` objects).

## Definition

```ts
export interface NormalizedImagesResult {
            readonly originalImageHashId: string;
            readonly originalImageTag: Core.BasicStructures.ImageTag;
            normalizedImageResultItems: Array<NormalizedImageResultItem>;
        }
```

| Properties              | Type |
|----------------------|-------------|
| [`originalImageHashId`](#originalimagehashid) | *String* |
| [`originalImageTag`](#originalimagetag) | *Core.BasicStructures.ImageTag* |
| [`normalizedImageResultItems`](#normalizedimageresultitems) | *Array<NormalizedImagesResult>* |

### originalImageHashId

Gets the hash ID of the original image.

```ts
readonly originalImageHashId: string;
```

### originalImageTag

Gets the tag of the original image.

```ts
readonly originalImageTag: Core.BasicStructures.ImageTag;
```

### normalizedImageResultItems

An array of NormalizedImageResultItem objects, represented by Array<NormalizedImageResultItem>.

```ts
normalizedImageResultItems: Array<NormalizedImageResultItem>;
```