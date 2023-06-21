---
layout: default-layout
title: class DocumentNormalizer Module - Dynamsoft Document Normalizer Classes
description: This page shows the JavaScript edition of the class DocumentNormalizer Module in Document Normalizer Module.
keywords: document normalizer module, JavaScript
needAutoGenerateSidebar: true
needGenerateH3Content: true
breadcrumbText: JavaScript DocumentNormalizer Module Class
permalink: /programming/javascript/api-reference/document-normalizer-module.html
---

# DocumentNormalizer Module

The "DocumentNormalizer" module is defined in the namespace `Dynamsoft.DDN`. At present, it consists of the class `DocumentNormalizer` and a few enumerations and interfaces.

## DocumentNormalizer Class

The `DocumentNormalizer` class now has only one static method which returns the version of the DocumentNormalizer Module.

| API Name                                            | Description                                              |
| --------------------------------------------------- | -------------------------------------------------------- |
| [getVersion()](./document-normalizer.md#getversion) | Returns the version of the `DocumentNormalizer` modules. |

## Interfaces

In order to make the code more predictable and readable, the module defines a series of supporting interfaces:

### Final Result Interfaces

* [DetectedQuadResultItem](./detected-quad-result-item.md)
* [DetectedQuadsResult](./detected-quads-result.md)
* [NormalizedImageResultItem](./normalized-image-result-item.md)
* [NormalizedImagesResult](./normalized-images-result.md)

### Intermediate Result Interfaces

* [CandidateQuadEdgesUnit](./candidate-quad-edges-unit.md)
* [CornersUnit](./corners-unit.md)
* [DetectedQuadElement](./detected-quad-element.md)
* [DetectedQuadsUnit](./detected-quads-unit.md)
* [LongLinesUnit](./long-lines-unit.md)
* [NormalizedImageElement](./normalized-image-element.md)
* [NormalizedImagesUnit](./normalized-images-unit.md)