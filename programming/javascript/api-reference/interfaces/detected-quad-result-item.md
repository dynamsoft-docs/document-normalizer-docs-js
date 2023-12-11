---
layout: default-layout
title: Interface DetectedQuadResultItem - Dynamsoft Label Recognizer JS Edition API Reference
description: This page shows the JS edition of the interface DetectedQuadResultItem.
keywords: detected quad, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# DetectedQuadResultItem

An interface that extends the CapturedResultItem interface from the Core.BasicStructures namespace. It represents a detected quad result item and includes properties such as location (the quadrilateral's coordinates) and confidenceAsDocumentBoundary (the confidence score of the quad as a document boundary).

## Definition

```ts
interface DetectedQuadResultItem extends Core.BasicStructures.CapturedResultItem {
    location: Core.BasicStructures.Quadrilateral;
    confidenceAsDocumentBoundary: number;
}
```

| Properties             | Type |
|----------------------|-------------|
| [`location`](#location) | *Core.BasicStructures.Quadrilateral* |
| [`confidenceAsDocumentBoundary`](#confidenceasdocumentboundary) | *number* |

### location

The detected quadrilateral's coordinates.

```ts
location: Core.BasicStructures.Quadrilateral;
```

### confidenceAsDocumentBoundary

A number representing the confidence score of the detected quad element. The confidence score indicates the certainty or accuracy of the quad element being identified as a boundary of a document.

```ts
confidenceAsDocumentBoundary: number;
```