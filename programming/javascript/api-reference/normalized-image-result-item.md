---
layout: default-layout
title: interface NormalizedImageResultItem - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface NormalizedImageResultItem in Dynamsoft Core Module.
keywords: normalized image result, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# NormalizedImageResultItem

An interface that extends the CapturedResultItem interface from the Core.BasicStructures namespace. It represents a normalized image result item and includes properties such as imageData (the image data), location (the quadrilateral's coordinates), and additional methods such as toCanvas, toImage, toBlob, and saveToFile for further processing and conversion.

## Definition

```js
export interface NormalizedImageResultItem extends Core.BasicStructures.CapturedResultItem {
            imageData: Core.BasicStructures.DSImageData;
            location: Core.BasicStructures.Quadrilateral;
            toCanvas: () => HTMLCanvasElement;
            toImage: (MIMEType: "image/png" | "image/jpeg") => HTMLImageElement;
            toBlob: (MIMEType: "image/png" | "image/jpeg") => Promise<Blob>;
            saveToFile: (name: string, download?: boolean) => Promise<File>;
        }
```

## Attributes Summary

| Attribute               | Type |
|----------------------|-------------|
| [`imageData`](#imagedata) | *Core.BasicStructures.Quadrilateral* |
| [`location`](#location) | *Core.BasicStructures.Quadrilateral* |

## Methods Summary

| Method               | Description |
|----------------------|-------------|
| [`toCanvas`](#toCanvas) | Returns an HTMLCanvasElement representing the normalized image. |
| [`toImage`](#toImage) | Returns an HTMLImageElement representing the normalized image with the specified MIME type. |
| [`toBlob`](#toBlob) | Returns a Promise that resolves to a Blob representing the normalized image with the specified MIME type. |
| [`saveToFile`](#saveToFile) | Saves the normalized image to a File object in memory and optionally downloads it to the local drive. |


### imageData

 A property of type DSImageData from the Core.BasicStructures namespace. It holds the image data for the normalized image.

```js
imageData: Core.BasicStructures.DSImageData;
```

### location

 A property of type Quadrilateral from the Core.BasicStructures namespace. It represents the location of the normalized image as a quadrilateral.

```js
location: Core.BasicStructures.Quadrilateral;
```

### toCanvas

```js
toCanvas: () => HTMLCanvasElement;
```

**Return Value**

Returns an HTMLCanvasElement representing the normalized image.

### toImage

```js
toImage: (MIMEType: "image/png" | "image/jpeg") => HTMLImageElement;
```

**Parameters**

`MIMEType`:  Take a type of "image/png" or "image/jpeg".

**Return Value**

Returns an HTMLImageElement representing the normalized image with the specified MIME type.

### toBlob

```js
toBlob: (MIMEType: "image/png" | "image/jpeg") => Promise<Blob>;
```

**Parameters**

`MIMEType`:  Take a type of "image/png" or "image/jpeg".

**Return Value**

Returns a Promise that resolves to a Blob representing the normalized image with the specified MIME type.

### saveToFile

```js
saveToFile: (name: string, download?: boolean) => Promise<File>;
```

**Parameters**

`name`:  Specifies the name of the file object.
`download`: Specifies whether to download the file when it's created.

**Return Value**

Returns a Promise that resolves to the File object.