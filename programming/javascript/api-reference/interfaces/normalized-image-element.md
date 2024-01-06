---
layout: default-layout
title: Interface NormalizedImageElement - Dynamsoft Label Recognizer JS Edition API Reference
description: This page shows the JS edition of the interface NormalizedImageElement.
keywords: normalized image, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# NormalizedImageElement

The NormalizedImageElement interface inherits from RegionObjectElement interface in the Core.IntermediateResult namespace. It includes additional properties `imageData` and `referencedElement`.

## Definition

```ts
interface NormalizedImageElement extends Core.IntermediateResult.RegionObjectElement {
    imageData: DSImageData;
    referencedElement: RegionObjectElement;
}
```

| Properties               | Type |
|----------------------|-------------|
| [`imageData`](#imagedata) | *DSImageData* |
| [`referencedElement`](#referencedelement) | *RegionObjectElement* |

### imageData

A property that holds image data represented by the DSImageData type, defined in the Core.BasicStructures namespace. 

```ts
imageData: DSImageData;
```

### referencedElement

A property that holds a reference to another RegionObjectElement from the Core.IntermediateResult namespace. This property is used to establish a connection or reference between the normalized image element and the original region object that it refers to.

```ts
referencedElement: RegionObjectElement;
```