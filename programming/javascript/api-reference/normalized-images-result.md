---
layout: default-layout
title: CNormalizedImagesResult Class
description: This page shows CNormalizedImagesResult class definition of Dynamsoft Document Normalizer SDK JavaScript Edition.
keywords: GetCount, GetErrorCode, GetErrorString, GetItem, GetSourceImageHashId, GetSourceImageTag, CNormalizedImagesResult, api reference
permalink: /programming/javascript/api-reference/normalized-images-result.html
---

# CNormalizedImagesResult

The CNormalizedImagesResult class stores a collection of captured result items whose type are normalized images.

## Definition

*Namespace:* dynamsoft::ddn

*Assembly:* DynamsoftDocumentNormalizer.dll

```cpp
class CNormalizedImagesResult
```

## Methods

| Method               | Description |
|----------------------|-------------|
| [`GetCount`](#getcount) | Gets the number of normalized images in the result. |
| [`GetErrorCode`](#geterrorcode) | Gets the error code of the operation. |
| [`GetErrorString`](#geterrorstring) | Gets the error message of the operation. |
| [`GetItem`](#getitem) | Gets a specific normalized image from the result. |
| [`HasItem`](#hasitem) | Check if the item is present in the array.|
| [`RemoveItem`](#removeitem) | Remove a specific item from the array in the normalized images.|
| [`GetRotationTransformMatrix`](#getrotationtransformmatrix) | Get the rotation transformation matrix of the original image relative to the rotated image.|
| [`GetSourceImageHashId`](#getsourceimagehashid) | Gets the hash ID of the source image that was normalized. |
| [`GetSourceImageTag`](#getsourceimagetag) | Gets the tag of the source image that was normalized. |

### GetCount

Gets the number of normalized images in the result.

```cpp
int GetCount()
```

**Return value**

Returns the number of normalized images in the result.

### GetErrorCode

Gets the error code of the operation.

```cpp
int GetErrorCode()
```

**Return value**

Returns the error code of the operation. A non-zero value indicates an error occurred.

**See Also**

* [ErrorCode]({{ site.enumerations }}core/error-code.html?src=cpp&&lang=cpp)

### GetErrorString

Gets the error message of the operation.

```cpp
const char* GetErrorString()
```

**Return value**

Returns the error message of the operation.

### GetItem

Gets a specific normalized image from the result.

```cpp
const CNormalizedImageResultItem* GetItem(int index)
```

**Parameters**

`[in] index` The index of the normalized image to get.

**Return value**

Returns a pointer to the normalized image at the specified index. If the index is out of range, returns nullptr.

**See Also**

* [CNormalizedImageResultItem](normalized-image-result-item.md)

### HasItem

Check if the item is present in the array.

```cpp
bool HasItem(const CNormalizedImageResultItem* item) const
```

**Parameters**

`[in] item` The specific item to check.

**Return value**

Returns a bool value indicating whether the item is present in the array or not.

### RemoveItem

Remove a specific item from the array in the normalized images.

```cpp
int RemoveItem(const CNormalizedImageResultItem* item)
```

**Parameters**

`[in] item` The specific item to remove.

**Return value**

Return value indicating whether the deletion was successful or not.

### GetRotationTransformMatrix

Get the rotation transformation matrix of the original image relative to the rotated image.

```cpp
void GetRotationTransformMatrix(double matrix[9]) const;
```

**Parameters**

`[out] matrix` A double array which represents the rotation transform matrix.


### GetSourceImageHashId

Gets the hash ID of the source image that was normalized.

```cpp
const char* GetSourceImageHashId()
```

**Return value**

Returns the hash ID of the source image that was normalized.

### GetSourceImageTag

Gets the tag of the source image that was normalized.

```cpp
const CImageTag* GetSourceImageTag()
```

**Return value**

Returns a pointer to the tag of the source image that was normalized.

**See Also**

* [CImageTag]({{ site.dcv_cpp_api }}core/basic-structures/image-tag.html)
