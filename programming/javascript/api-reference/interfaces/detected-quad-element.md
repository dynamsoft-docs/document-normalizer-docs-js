---
layout: default-layout
title: Interface DetectedQuadElement - Dynamsoft Document Normalizer JS Edition API Reference
description: This page shows the JS edition of the interface DetectedQuadElement.
keywords: detected quad, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# DetectedQuadElement

The `DetectedQuadElement` interface extends the `RegionObjectElement` interface and represents a detected quadrilateral element.

```ts
interface DetectedQuadElement extends RegionObjectElement {
    confidenceAsDocumentBoundary: number;
}
```

## confidenceAsDocumentBoundary

A confidence score measuring the certainty that the detected quadrilateral represents the boundary of a document.

**See Also**

[RegionObjectElement](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/intermediate-results/region-object-element.html)
