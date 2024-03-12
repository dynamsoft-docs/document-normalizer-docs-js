---
layout: default-layout
title: Interface DetectedQuadResultItem - Dynamsoft Document Normalizer JS Edition API Reference
description: This page shows the JS edition of the interface DetectedQuadResultItem.
keywords: detected quad, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# DetectedQuadResultItem

The `DetectedQuadResultItem` interface extends the `CapturedResultItem` interface and represents a detected quadrilateral result item.

```ts
interface DetectedQuadResultItem extends CapturedResultItem {
    location: Quadrilateral;
    confidenceAsDocumentBoundary: number;
}
```

## location

The location of the detected quadrilateral within the original image, represented as a quadrilateral shape.

## confidenceAsDocumentBoundary

A confidence score related to the detected quadrilateral's accuracy as a document boundary.

**See Also**

[CapturedResultItem](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/captured-result-item.html)

[Quadrilateral](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/quadrilateral.html)