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
    crossVerificationStatus: EnumCrossVerificationStatus;
}
```

## location

The location of the detected quadrilateral within the original image, represented as a quadrilateral shape.

## confidenceAsDocumentBoundary

A confidence score measuring the certainty that the detected quadrilateral represents the boundary of a document.

## crossVerificationStatus

Indicates whether the DetectedQuadResultItem has passed cross verification.

**See Also**

[CapturedResultItem](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/captured-result-item.html)

[Quadrilateral](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/quadrilateral.html)

[EnumCrossVerificationStatus]({{ site.dcv_js_api }}core/enum-cross-verification-status.html?lang=js)