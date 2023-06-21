---
layout: default-layout
title: CLongLinesUnit Class
description: This page shows CLongLinesUnit class definition of Dynamsoft Document Normalizer SDK JavaScript Edition.
keywords: GetCount, GetLongLine, CLongLinesUnit, api reference
permalink: /programming/javascript/api-reference/long-lines-unit.html
---

# CLongLinesUnit Class

The CLongLinesUnit class represents an intermediate result unit whose type is long lines.

## Definition

*Namespace:* dynamsoft::ddn::intermediate_results

*Assembly:* DynamsoftDocumentNormalizer.dll

```cpp
class CLongLinesUnit: CIntermediateResultUnit
```

*Inheritance:* [CIntermediateResultUnit]({{ site.dcv_cpp_api }}core/intermediate-results/intermediate-result-unit.html) -> CLongLinesUnit

## Methods

| Method | Description |
|--------|-------------|
| [`GetCount`](#getcount) | Gets the count of LongLine objects in current object.|
| [`GetLongLine`](#getlongline) | Gets a LongLine object from current object by specifying a index. |

### GetCount

Gets the count of LongLine objects in current object.

```cpp
int GetCount() 
```

**Return Value**

The count of LongLine objects in current object.

### GetLongLine

Gets a LongLine object from current object by specifying a index.

```cpp
int GetLongLine(int index, CLineSegment* line)
```

**Parameters**

`[in] index` The index of the LongLine object.

`[in, out] line` The LongLine object got by the specific index.

**Return Value**

Returns the error code.

**See Also**

* [CLineSegment]({{ site.dcv_cpp_api }}core/basic-structures/line-segment.html)
* [ErrorCode]({{ site.enumerations }}core/error-code.html?src=cpp&&lang=cpp)
