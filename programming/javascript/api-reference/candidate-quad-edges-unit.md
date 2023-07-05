---
layout: default-layout
title: interface CandidateQuadEdgesUnit - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interfaace CandidateQuadEdgesUnit in Dynamsoft Core Module.
keywords: candidate quads, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# CandidateQuadEdgesUnit

The CandidateQuadEdgesUnit interface extends the IntermediateResultUnit interface and represents a unit of intermediate result specifically for candidate quadrilateral edges. It includes additional properties that provide information about the edges.

## Definition

```js
export interface CandidateQuadEdgesUnit extends Core.IntermediateResult.IntermediateResultUnit {
                candidateQuadEdges: Array<Core.BasicStructures.Edge>;
            }
```

## Attributes Summary

| Attribute               | Type |
|----------------------|-------------|
| [`candidateQuadEdges`](#candidatequadEedges) | *Array<Core.BasicStructures.Edge>* |

### candidateQuadEdges

Gets the candidate quad edges related to the intermediate result. The Edge type is defined in the Core.BasicStructures namespace.

```js
candidateQuadEdges: Array<Core.BasicStructures.Edge>;
```