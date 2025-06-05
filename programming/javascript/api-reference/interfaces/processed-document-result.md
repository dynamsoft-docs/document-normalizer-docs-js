---
layout: default-layout
title: Interface ProcessedDocumentResult - Dynamsoft Document Normalizer JS Edition API Reference
description: This page shows the JS edition of the interface ProcessedDocumentResult.
keywords: detected quad, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# ProcessedDocumentResult

The `ProcessedDocumentResult` interface holds information on detected quadrilaterals, deskewed images and the enhanced images from the original images.

## Definition

```ts
interface ProcessedDocumentResult extends CapturedResultBase{
    readonly detectedQuadResultItems: Array<DetectedQuadResultItem>;
    readonly deskewedImageResultItems: Array<DeskewedImageResultItem>;
    readonly enhancedImageResultItems: Array<EnhancedImageResultItem>;
};
```

## detectedQuadResultItems

An array of [`DetectedQuadResultItem`](./detected-quad-result-item.md) objects, each representing a quadrilateral after document detection.

## deskewedImageResultItems

An array of [`DeskewedImageResultItem`](./deskewed-image-result-item.md) objects, each representing a piece of the original image after deskewing.

## enhancedImageResultItems

An array of [`EnhancedImageResultItem`](./enhanced-image-result-item.md) objects, each representing a piece of the original image after enhancement.
