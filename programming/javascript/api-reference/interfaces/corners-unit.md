---
layout: default-layout
title: Interface CornersUnit - Dynamsoft Label Recognizer JS Edition API Reference
description: This page shows the JS edition of the interface CornersUnit.
keywords: corners, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# CornersUnit

The CornersUnit interface extends the IntermediateResultUnit interface and represents a unit of intermediate result specifically for corners. It includes additional properties that provide information about the corners.

## Definition

```ts
interface CornersUnit extends Core.IntermediateResult.IntermediateResultUnit {
    corners: Array<Core.BasicStructures.Corner>;
}
```

| Properties              | Type |
|----------------------|-------------|
| [`corners`](#corners) | *Array\<Core.BasicStructures.Corner>* |

### corners

It stores the candidate corners detected during processing. The corner type is defined in the Core.BasicStructures namespace.

```ts
corners: Array<Core.BasicStructures.Corner>;
```