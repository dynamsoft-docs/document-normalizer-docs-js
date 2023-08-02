---
layout: default-layout
title: interface NormalizedImagesResult - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface NormalizedImagesResult in Dynamsoft Core Module.
keywords: normalized image, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# NormalizedImagesResult

An interface represents the result of normalized images. It includes properties such as sourceImageHashId, sourceImageTag, and normalizedImageResultItems (an array of `NormalizedImageResultItem` objects).

## Definition

```ts
export interface NormalizedImagesResult {
            readonly sourceImageHashId: string;
            readonly sourceImageTag: Core.BasicStructures.ImageTag;
            normalizedImageResultItems: Array<NormalizedImageResultItem>;
        }
```

| Properties              | Type |
|----------------------|-------------|
| [`sourceImageHashId`](#sourceimagehashid) | *String* |
| [`sourceImageTag`](#sourceimagetag) | *Core.BasicStructures.ImageTag* |
| [`normalizedImageResultItems`](#normalizedimageresultitems) | *Array<NormalizedImagesResult>* |

### sourceImageHashId

Gets the hash ID of the source image.

```ts
readonly sourceImageHashId: string;
```

### sourceImageTag

Gets the tag of the source image.

```ts
readonly sourceImageTag: Core.BasicStructures.ImageTag;
```

### normalizedImageResultItems

An array of NormalizedImageResultItem objects, represented by Array<NormalizedImageResultItem>.

```ts
normalizedImageResultItems: Array<NormalizedImageResultItem>;
```