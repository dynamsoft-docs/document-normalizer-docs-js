---
layout: default-layout
title: interface NormalizedImageElement - Dynamsoft Core Module JS Edition API Reference
description: This page shows the JS edition of the interface NormalizedImageElement in Dynamsoft Core Module.
keywords: normalized image, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# NormalizedImageElement

The NormalizedImageElement interface inherits from RegionObjectElement interface in the Core.IntermediateResult namespace. It includes additional properties `imageData` and `referencedElement`.

## Definition

```ts
interface NormalizedImageElement extends Core.IntermediateResult.RegionObjectElement {
    imageData: Core.BasicStructures.DSImageData;
    referencedElement: Core.IntermediateResult.RegionObjectElement;
}
```

| Properties               | Type |
|----------------------|-------------|
| [`imageData`](#imagedata) | *Core.BasicStructures.DSImageData* |
| [`referencedElement`](#referencedelement) | *Core.IntermediateResult.RegionObjectElement* |

### imageData

A property that holds image data represented by the DSImageData type, defined in the Core.BasicStructures namespace. 

```ts
imageData: Core.BasicStructures.DSImageData;
```

### referencedElement

A property that holds a reference to another RegionObjectElement from the Core.IntermediateResult namespace. This property is used to establish a connection or reference between the normalized image element and the original region object that it refers to.

```ts
referencedElement: Core.IntermediateResult.RegionObjectElement;
```