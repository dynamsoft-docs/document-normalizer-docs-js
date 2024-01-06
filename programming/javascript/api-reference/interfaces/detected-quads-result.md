---
layout: default-layout
title: Interface DetectedQuadsResult - Dynamsoft Label Recognizer JS Edition API Reference
description: This page shows the JS edition of the interface DetectedQuadsResult.
keywords: detected quad, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# DetectedQuadsResult

An interface representing the result of detected quads. It includes properties such as originalImageHashId, originalImageTag, and quadsResultItems (an array of `DetectedQuadResultItem` objects).

## Definition

```ts
interface DetectedQuadsResult {
    readonly originalImageHashId: string;
    readonly originalImageTag: ImageTag;
    quadsResultItems: Array<DetectedQuadResultItem>;
}
```

| Properties            | Type |
|----------------------|-------------|
| [`originalImageHashId`](#originalimagehashid) | *string* |
| [`originalImageTag`](#originalimagetag) | *ImageTag* |
| [`quadsResultItems`](#quadsresultitems) | *Array\<DetectedQuadResultItem>* |

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

### quadsResultItems

It stores the quadrilaterals detected during processing.

```ts
quadsResultItems: Array<DetectedQuadResultItem>;
```