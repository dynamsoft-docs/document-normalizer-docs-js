---
layout: default-layout
title: Interface LogicLinesUnit - Dynamsoft Document Normalizer JS Edition API Reference
description: This page shows the JS edition of the interface LogicLinesUnit.
keywords: logic lines, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# LogicLinesUnit

The `LogicLinesUnit` interface extends the `IntermediateResultUnit` interface and represents a unit of line segments.

```ts
interface LogicLinesUnit extends IntermediateResultUnit {
    logicLines: Array<LineSegment>;
}
```

## logicLines

An array of line segment detected within the image.

**See Also**

[IntermediateResultUnit](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/intermediate-results/intermediate-result-unit.html)

[LineSegment](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/line-segment.html)