---
layout: default-layout
title: interface DetectedQuadElement - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interfaace DetectedQuadElement in Dynamsoft Core Module.
keywords: detected quad, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# DetectedQuadElement

The DetectedQuadElement interface inherits from RegionObjectElement interface in the Core.IntermediateResult namespace. It includes additional properties `confidenceAsDocumentBoundary`.

## Definition

```js
export interface DetectedQuadElement extends Core.IntermediateResult.RegionObjectElement {
                confidenceAsDocumentBoundary: number;
            }
```

## Attributes Summary

| Attribute               | Type |
|----------------------|-------------|
| [`confidenceAsDocumentBoundary`](#confidenceasdocumentboundary) | *Number* |

### confidenceAsDocumentBoundary

A number representing the confidence score of the detected quad element. The confidence score indicates the certainty or accuracy of the quad element being identified as a boundary of a document.

```js
confidenceAsDocumentBoundary: number;
```