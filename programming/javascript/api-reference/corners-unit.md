---
layout: default-layout
title: CCornersUnit Class
description: This page shows CCornersUnit class definition of Dynamsoft Document Normalizer SDK JavaScript Edition.
keywords: GetCount, GetCorner, CCornersUnit, api reference
permalink: /programming/javascript/api-reference/corners-unit.html
---

# CCornersUnit Class

The CCornersUnit class represents an intermediate result unit whose type is corners.

## Definition

*Namespace:* dynamsoft::ddn::intermediate_results

*Assembly:* DynamsoftDocumentNormalizer.dll

```cpp
class CCornersUnit: CIntermediateResultUnit
```

*Inheritance:* [CIntermediateResultUnit]({{ site.dcv_cpp_api }}core/intermediate-results/intermediate-result-unit.html) -> CCornersUnit

## Methods

| Method | Description |
|--------|-------------|
| [`GetCount`](#getcount) | Gets the count of Corner objects in current object.|
| [`GetCorner`](#getcorner) | Gets a Corner object from current object by specifying a index. |

### GetCount

Gets the count of Corner objects in current object.

```cpp
int GetCount() 
```

**Return Value**

The count of Corner objects in current object.

### GetCorner

Gets a Corner object from current object by specifying a index.

```cpp
int GetCorner(int index, CCorner* corner)
```

**Parameters**

`[in] index` The index of the Corner object.

`[in, out] corner` The Corner object got by the specific index.

**Return Value**

Returns the error code.

**See Also**

* [CCorner]({{ site.dcv_cpp_api }}core/basic-structures/corner.html)
* [ErrorCode]({{ site.enumerations }}core/error-code.html?src=cpp&&lang=cpp)
