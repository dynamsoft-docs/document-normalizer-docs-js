---
layout: default-layout
title: Interface LongLinesUnit - Dynamsoft Document Normalizer JS Edition API Reference
description: This page shows the JS edition of the interface LongLinesUnit.
keywords: long lines, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# LongLinesUnit

The LongLinesUnit interface inherits from IntermediateResultUnit interface in the Core.IntermediateResult namespace. It includes additional properties `longLines`.

## Definition

```ts
interface LongLinesUnit extends Core.IntermediateResult.IntermediateResultUnit {
    longLines: Array<LineSegment>;
}
```

| Properties               | Type |
|----------------------|-------------|
| [`longLines`](#longlines) | *Array\<LineSegment>* |

### longLines

An array of LineSegment objects, represented by Array<LineSegment>. It holds the long lines detected or processed as part of the intermediate result. Each LineSegment represents a line segment defined by its start and end points.

```ts
longLines: Array<LineSegment>;
```