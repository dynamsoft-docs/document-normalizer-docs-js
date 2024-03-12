---
layout: default-layout
title: Interface DetectedQuadsUnit - Dynamsoft Document Normalizer JS Edition API Reference
description: This page shows the JS edition of the interface DetectedQuadsUnit.
keywords: detected quad, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# DetectedQuadsUnit

The `DetectedQuadsUnit` interface extends the `IntermediateResultUnit` interface and represents a unit of detected quadrilaterals.

```ts
interface DetectedQuadsUnit extends IntermediateResultUnit {
    detectedQuads: Array<DetectedQuadElement>;
}
```

## detectedQuads

An array of `DetectedQuadElement` objects, each representing a potential document or area of interest within the image.

**See Also**

[IntermediateResultUnit](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/intermediate-results/intermediate-result-unit.html)

[DetectedQuadElement](./detected-quad-element.md)