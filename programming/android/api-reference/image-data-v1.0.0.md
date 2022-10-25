---
layout: default-layout
title: Dynamsoft Core Java Class - ImageData
description: This page shows the ImageData Class of Dynamsoft Core for Java Language.
keywords: ImageData, java
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
---

# ImageData

Stores the image data.  

```java
class com.dynamsoft.core.ImageData
```  

## Attributes

| Attribute | Type |
|---------- | ---- |
| [`bytes`](#bytes) | *byte[]* |
| [`width`](#width) | *int* |
| [`height`](#height) | *int* |
| [`stride`](#stride) | *int* |
| [`format`](#format) | [`EnumImagePixelFormat`]({{ site.enumerations }}image-pixel-format.html?src=android) |
| [`orientation`](#orientation) | *int* |

&nbsp;

### bytes

The image data content in a byte array.

```java
byte[] bytes
```

&nbsp;

### width

The width of the image in pixels.  

```java
int width
```

&nbsp;

### height

The height of the image in pixels.  

```java
int height
```

&nbsp;

### stride

The stride (or scan width) of the image.

```java
int stride
```

&nbsp;

### format

The image pixel format used in the image byte array.

```java
EnumImagePixelFormat format
```

### orientation

The counterclockwise rotation angle of the image. It can be 0, 90, 180 or 270.

```java
int orientation
```

## Methods

| Method | Description |
| ------ | ----------- |
| `toBitmap` | Convert the `ImageData` object to a `Bitmap` object. |

### toBitmap

Convert the `ImageData` object to a `Bitmap` object.

```java
Bitmap toBitmap() throws CoreException
```

**Return Value**

A Bitmap object.