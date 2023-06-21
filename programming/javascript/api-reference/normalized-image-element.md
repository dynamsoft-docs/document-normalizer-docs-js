---
layout: default-layout
title: CNormalizedImageElement Class
description: This page shows CNormalizedImageElement class definition of Dynamsoft Document Normalizer SDK JavaScript Edition.
keywords: GetImageData, GetReferencedElement, CNormalizedImageElement, api reference
permalink: /programming/javascript/api-reference/normalized-image-element.html
---

# CNormalizedImageElement Class

The CNormalizedImageElement class stores an intermediate result whose type is normalized image.

## Definition

*Namespace:* dynamsoft::ddn::intermediate_results

*Assembly:* DynamsoftDocumentNormalizer.dll

```cpp
class CNormalizedImageElement
```

## Methods

| Method | Description |
|--------|-------------|
| [`GetImageData`](#getimagedata) | Gets the ImageData of current object. |

### GetImageData

Gets the ImageData of current object.

```cpp
const CImageData* GetImageData() 
```

**Return Value**

The image data.

**See Also**

* [CImageData]({{ site.dcv_cpp_api }}core/basic-structures/image-data.html)
