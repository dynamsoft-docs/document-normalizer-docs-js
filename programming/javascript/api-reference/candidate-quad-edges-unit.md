---
layout: default-layout
title: CCandidateQuadEdgesUnit Class
description: This page shows CCandidateQuadEdgesUnit class definition of Dynamsoft Document Normalizer SDK JavaScript Edition.
keywords: GetCount, GetCandidateQuadEdge, CCandidateQuadEdgesUnit, api reference
permalink: /programming/javascript/api-reference/candidate-quad-edges-unit.html
---

# CCandidateQuadEdgesUnit Class

The CCandidateQuadEdgesUnit class represents an intermediate result unit whose type is candidate quad edges.

## Definition

*Namespace:* dynamsoft::ddn::intermediate_results

*Assembly:* DynamsoftDocumentNormalizer.dll

```cpp
class CCandidateQuadEdgesUnit: CIntermediateResultUnit
```

*Inheritance:* [CIntermediateResultUnit]({{ site.dcv_cpp_api }}core/intermediate-results/intermediate-result-unit.html) -> CCandidateQuadEdgesUnit

## Methods

| Method | Description |
|--------|-------------|
| [`GetCount`](#getcount) | Gets the count of CandidateQuadEdge objects in current object.|
| [`GetCandidateQuadEdge`](#getcandidatequadedge) | Gets a CandidateQuadEdge object from current object by specifying a index. |

### GetCount

Gets the count of CandidateQuadEdge objects in current object.

```cpp
int GetCount() 
```

**Return Value**

The count of CandidateQuadEdge objects in current object.

### GetCandidateQuadEdge

Gets a CandidateQuadEdge object from current object by specifying a index.

```cpp
int GetCandidateQuadEdge(int index, CEdge* edge)
```

**Parameters**

`[in] index` The index of the CandidateQuadEdge object.

`[in, out] edge` The CandidateQuadEdge object got by the specific index.

**Return Value**

Returns the error code.

**See Also**

* [CEdge]({{ site.dcv_cpp_api }}core/basic-structures/edge.html)
* [ErrorCode]({{ site.enumerations }}core/error-code.html?src=cpp&&lang=cpp)
