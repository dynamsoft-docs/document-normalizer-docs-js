---
layout: default-layout
title: interface LongLinesUnit - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interfaace LongLinesUnit in Dynamsoft Core Module.
keywords: long lines, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# LongLinesUnit

The LongLinesUnit interface inherits from IntermediateResultUnit interface in the Core.IntermediateResult namespace. It includes additional properties `longLines`.

## Definition

```js
export interface LongLinesUnit extends Core.IntermediateResult.IntermediateResultUnit {
                longLines: Array<Core.BasicStructures.LineSegment>;
            }
```

## Attributes Summary

| Attribute               | Type |
|----------------------|-------------|
| [`longLines`](#longLlines) | *Array<LongLinesUnit>* |

### longLines

An array of LineSegment objects, represented by Array<Core.BasicStructures.LineSegment>. It holds the long lines detected or processed as part of the intermediate result. Each LineSegment represents a line segment defined by its start and end points.

```js
longLines: Array<Core.BasicStructures.LineSegment>;
```