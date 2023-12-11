---
layout: default-layout
title: interface DetectedQuadsResult - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface DetectedQuadsResult in Dynamsoft Core Module.
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
    readonly originalImageTag: Core.BasicStructures.ImageTag;
    quadsResultItems: Array<DetectedQuadResultItem>;
}
```

| Properties            | Type |
|----------------------|-------------|
| [`originalImageHashId`](#originalimagehashid) | *string* |
| [`originalImageTag`](#originalimagetag) | *Core.BasicStructures.ImageTag* |
| [`quadsResultItems`](#quadsresultitems) | *Array\<DetectedQuadResultItem>* |

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

### quadsResultItems

It stores the quadrilaterals detected during processing.

```ts
quadsResultItems: Array<DetectedQuadResultItem>;
```