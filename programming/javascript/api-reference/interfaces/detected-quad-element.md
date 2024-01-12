---
layout: default-layout
title: Interface DetectedQuadElement - Dynamsoft Document Normalizer JS Edition API Reference
description: This page shows the JS edition of the interface DetectedQuadElement.
keywords: detected quad, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# DetectedQuadElement

The DetectedQuadElement interface inherits from RegionObjectElement interface in the Core.IntermediateResult namespace. It includes additional properties `confidenceAsDocumentBoundary`.

## Definition

```ts
interface DetectedQuadElement extends Core.IntermediateResult.RegionObjectElement {
    confidenceAsDocumentBoundary: number;
}
```

| Properties              | Type |
|----------------------|-------------|
| [`confidenceAsDocumentBoundary`](#confidenceasdocumentboundary) | *number* |

### confidenceAsDocumentBoundary

A number representing the confidence score of the detected quad element. The confidence score indicates the certainty or accuracy of the quad element being identified as a boundary of a document.

```ts
confidenceAsDocumentBoundary: number;
```