---
layout: default-layout
title: DocumentNormalizerModule Class - Dynamsoft Document Normalizer JavaScript Edition API
description: This page introduces APIs related to the DocumentNormalizerModule Class of Dynamsoft Document Normalizer JavaScript Edition.
keywords: capture vision, Barcode Reader Module, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
---

# DocumentNormalizerModule Class

The `DocumentNormalizerModule` class defines common functionality in the `DocumentNormalizer` module.

| API Name                             | Description                                             |
| ------------------------------------ | ------------------------------------------------------- |
| static [`getVersion()`](#getversion) | Returns the version of the `DocumentNormalizer` module. |

### getVersion

Returns the version of the DocumentNormalizer module.

```typescript
static getVersion(): string;
```

**Code snippet**

```javascript
const version = Dynamsoft.DDN.DocumentNormalizerModule.getVersion();
console.log(version);
```