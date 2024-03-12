---
layout: default-layout
title: Interface DetectedQuadsResult - Dynamsoft Document Normalizer JS Edition API Reference
description: This page shows the JS edition of the interface DetectedQuadsResult.
keywords: detected quad, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# DetectedQuadsResult

The `DetectedQuadsResult` interface holds information on detected quadrilaterals, of type `DetectedQuadResultItem`, within an image.

## Definition

```ts
interface DetectedQuadsResult {
    readonly errorCode: number;
    readonly errorString: string;
    readonly originalImageHashId: string;
    readonly originalImageTag: ImageTag;
    readonly quadsResultItems: Array<DetectedQuadResultItem>;
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

## quadsResultItems

An array of `DetectedQuadResultItem` objects, each representing a detected quadrilateral within the original image. 

**See Also**

[DetectedQuadResultItem](./detected-quad-result-item.md)