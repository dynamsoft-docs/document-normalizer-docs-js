---
layout: default-layout
title: Interface CandidateQuadEdgesUnit - Dynamsoft Document Normalizer JS Edition API Reference
description: This page shows the JS edition of the interface CandidateQuadEdgesUnit.
keywords: candidate quads, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# CandidateQuadEdgesUnit

The `CandidateQuadEdgesUnit` interface extends the `IntermediateResultUnit` interface and represents a unit of candidate edges.

```ts
interface CandidateQuadEdgesUnit extends IntermediateResultUnit {
    candidateQuadEdges: Array<Edge>;
}
```

## candidateQuadEdges

An array of candidate edges that may form quadrilaterals, identified during image processing.

**See Also**

[IntermediateResultUnit](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/intermediate-results/intermediate-result-unit.html)

[Edge](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/core/basic-structures/edge.html)