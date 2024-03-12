---
layout: default-layout
title: Interface CornersUnit - Dynamsoft Document Normalizer JS Edition API Reference
description: This page shows the JS edition of the interface CornersUnit.
keywords: corners, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# CornersUnit

The `CornersUnit` interface extends the `IntermediateResultUnit` interface and represents a unit of detected corners.

```ts
interface CornersUnit extends IntermediateResultUnit {
    corners: Array<Corner>;
}
```

## corners

An array of detected corners within the image, identified during image processing.

**See Also**

[IntermediateResultUnit](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/intermediate-results/intermediate-result-unit.html)

[Corner](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/corner.html)