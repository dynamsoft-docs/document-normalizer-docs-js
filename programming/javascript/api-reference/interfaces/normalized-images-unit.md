---
layout: default-layout
title: interface NormalizedImagesUnit - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface NormalizedImagesUnit in Dynamsoft Core Module.
keywords: normalized image, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# NormalizedImagesUnit

The NormalizedImagesUnit interface inherits from IntermediateResultUnit interface in the Core.IntermediateResult namespace. It includes additional properties `normalizedImages`.

## Definition

```ts
interface NormalizedImagesUnit extends Core.IntermediateResult.IntermediateResultUnit {
                normalizedImages: Array<NormalizedImagesUnit>;
            }
```

| Properties               | Type |
|----------------------|-------------|
| [`normalizedImages`](#normalizedimages) | *Array<NormalizedImagesUnit>* |

### normalizedImages

An array of NormalizedImageElement objects. It holds the normalized image elements, each NormalizedImageElement represents an image that has been normalized (cropped and standardized).

```ts
normalizedImages: Array<NormalizedImagesUnit>;
```
