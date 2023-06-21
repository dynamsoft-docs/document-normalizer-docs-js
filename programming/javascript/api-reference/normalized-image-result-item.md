---
layout: default-layout
title: CNormalizedImageResultItem Class
description: This page shows CNormalizedImageResultItem class definition of Dynamsoft Document Normalizer SDK JavaScript Edition.
keywords: GetImageData, SaveToFile, CNormalizedImageResultItem, api reference
permalink: /programming/javascript/api-reference/normalized-image-result-item.html
---

# CNormalizedImageResultItem Class

The CNormalizedImageResultItem class stores a captured result item whose type is normalized image.

## Definition

*Namespace:* dynamsoft::ddn

*Assembly:* DynamsoftDocumentNormalizer.dll

```cpp
class CNormalizedImageResultItem: CCapturedResultItem
```

*Inheritance:* [CCapturedResultItem]({{ site.dcv_cpp_api }}core/basic-structures/captured-result-item.html) -> CNormalizedImageResultItem

## Methods

| Method | Description |
|--------|-------------|
| [`GetImageData`](#getimagedata) | Gets the ImageData of current object. |
| [`GetLocation`](#getlocation) | Gets the location of current object. |
| [`GetRotationTransformMatrix`](#getrotationtransformmatrix) | Get the rotation transformation matrix. |

### GetImageData

Gets the ImageData of current object.

```cpp
const CImageData* GetImageData() 
```

**Return Value**

The image data.

**See Also**

* [CImageData]({{ site.dcv_cpp_api }}core/basic-structures/image-data.html)

### GetLocation

Gets the location of current object.

```cpp
const CQuadrilateral GetLocation() 
```

**Return Value**

The location of current object.

**See Also**

* [CQuadrilateral]({{ site.dcv_cpp_api }}core/basic-structures/quadrilateral.html)

### GetRotationTransformMatrix

Get the rotation transformation matrix.

```cpp
void GetRotationTransformMatrix(double matrix[9])
```
