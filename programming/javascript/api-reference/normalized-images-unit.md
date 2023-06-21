---
layout: default-layout
title: CNormalizedImagesUnit Class
description: This page shows CNormalizedImagesUnit class definition of Dynamsoft Document Normalizer SDK JavaScript Edition.
keywords: GetNormalizedImage, CNormalizedImagesUnit, api reference
permalink: /programming/javascript/api-reference/normalized-image-unit.html
---

# CNormalizedImagesUnit Class

The CNormalizedImagesUnit class represents an intermediate result unit whose type is normalized images.

## Definition

*Namespace:* dynamsoft::ddn::intermediate_results

*Assembly:* DynamsoftDocumentNormalizer.dll

```cpp
class CNormalizedImagesUnit: CIntermediateResultUnit
```

*Inheritance:* [CIntermediateResultUnit]({{ site.dcv_cpp_api }}core/intermediate-results/intermediate-result-unit.html) -> CNormalizedImagesUnit

## Methods

| Method | Description |
|--------|-------------|
| [`GetCount`](#getcount) | Gets the count of `CNormalizedImageElement` objects in current object. |
| [`GetNormalizedImage`](#getnormalizedimage) | Gets a NormalizedImage object from current object. |

### GetCount

Gets the count of `CNormalizedImageElement` objects in current object.

```cpp
int GetCount() 
```

**Return Value**

The count of `CNormalizedImageElement` objects in current object.

### GetNormalizedImage

Gets a NormalizedImage object from current object.

```cpp
const CNormalizedImageElement* GetNormalizedImage(int index)
```

**Return Value**

Returns the NormalizedImage object.

**See Also**

* [CNormalizedImageElement]({{cpp_api}}normalized-image-element.html)
