---
layout: default-layout
title: Interface LongLinesUnit - Dynamsoft Document Normalizer JS Edition API Reference
description: This page shows the JS edition of the interface LongLinesUnit.
keywords: long lines, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# LongLinesUnit

The `LongLinesUnit` interface extends the `IntermediateResultUnit` interface and represents a unit of long line segments.

```ts
interface LongLinesUnit extends IntermediateResultUnit {
    longLines: Array<LineSegment>;
}
```

## longLines

An array of long line segments detected within the image.

**See Also**

[IntermediateResultUnit](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/intermediate-results/intermediate-result-unit.html)

[LineSegment](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/line-segment.html)