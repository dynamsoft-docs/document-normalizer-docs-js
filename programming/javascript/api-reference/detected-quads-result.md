---
layout: default-layout
title: interface DetectedQuadsResult - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface DetectedQuadsResult in Dynamsoft Core Module.
keywords: detected quad, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# DetectedQuadsResult

An interface representing the result of detected quads. It includes properties such as sourceImageHashId, sourceImageTag, and quadsResultItems (an array of `DetectedQuadResultItem` objects).

## Definition

```ts
export interface DetectedQuadsResult {
            readonly sourceImageHashId: string;
            readonly sourceImageTag: Core.BasicStructures.ImageTag;
            quadsResultItems: Array<DetectedQuadsResult>;
        }
```

## Attributes Summary

| Attribute               | Type |
|----------------------|-------------|
| [`sourceImageHashId`](#sourceimagehashid) | *String* |
| [`sourceImageTag`](#sourceimagetag) | *Core.BasicStructures.ImageTag* |
| [`quadsResultItems`](#quadsresultitems) | *Array<DetectedQuadsResult>* |

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

### quadsResultItems

It stores the quadrilaterals detected during processing.

```ts
quadsResultItems: Array<DetectedQuadsResult>;
```