---
layout: default-layout
title: CDetectedQuadElement Class
description: This page shows CDetectedQuadElement class definition of Dynamsoft Document Normalizer SDK JavaScript Edition.
keywords: GetConfidenceAsDocumentBoundary, CDetectedQuadElement, api reference
permalink: /programming/javascript/api-reference/detected-quad-element.html
---

# CDetectedQuadElement Class

The CDetectedQuadElement class stores an intermediate result whose type is detected quad.

## Definition

*Namespace:* dynamsoft::ddn::intermediate_results

*Assembly:* DynamsoftDocumentNormalizer.dll

```cpp
class CDetectedQuadElement: CRegionObjectElement
```

*Inheritance:* [CRegionObjectElement]({{ site.dcv_cpp_api }}core/intermediate-results/region-object-element.html) -> CDetectedQuadElement

## Methods

| Method | Description |
|--------|-------------|
| [`GetConfidenceAsDocumentBoundary`](#getconfidenceasdocumentboundary) | Gets the confidence as document boundary of current object. |

### GetConfidenceAsDocumentBoundary

Gets the confidence as document boundary of current object.

```cpp
int GetConfidenceAsDocumentBoundary() 
```

**Return Value**

The confidence as document boundary of current object.
