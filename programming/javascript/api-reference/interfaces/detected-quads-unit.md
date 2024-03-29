---
layout: default-layout
title: Interface DetectedQuadsUnit - Dynamsoft Document Normalizer JS Edition API Reference
description: This page shows the JS edition of the interface DetectedQuadsUnit.
keywords: detected quad, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# DetectedQuadsUnit

The DetectedQuadsUnit interface inherits from IntermediateResultUnit interface in the Core.IntermediateResult namespace. It includes additional properties `detectedQuads`.

## Definition

```ts
interface DetectedQuadsUnit extends Core.IntermediateResult.IntermediateResultUnit {
    detectedQuads: Array<DetectedQuadElement>;
}
```

| Properties              | Type |
|----------------------|-------------|
| [`detectedQuads`](#detectedquads) | *Array\<DetectedQuadsUnit>* |

### detectedQuads

An array of DetectedQuadElement objects and it holds the detected quads. Each DetectedQuadElement represents a single set of detected quads.

```ts
detectedQuads: Array<DetectedQuadElement>;
```