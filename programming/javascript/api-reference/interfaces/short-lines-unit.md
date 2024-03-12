---
layout: default-layout
title: Interface ShortLinesUnit - Dynamsoft Document Normalizer JS Edition API Reference
description: This page shows the JS edition of the interface ShortLinesUnit.
keywords: short lines, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# ShortLinesUnit

The `ShortLinesUnit` interface extends the `IntermediateResultUnit` interface and represents a unit of short line segments.

```ts
interface ShortLinesUnit extends IntermediateResultUnit {
    shortLines: Array<LineSegment>;
}
```

## shortLines

An array of short line segments detected within the image.

**See Also**

[IntermediateResultUnit](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/intermediate-results/intermediate-result-unit.html)

[LineSegment](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/line-segment.html)