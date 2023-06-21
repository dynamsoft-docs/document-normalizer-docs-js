---
title: Upgrade Instructions - Dynamsoft Document Normalizer JavaScript Edition
keywords: JavaScript, JS, upgrade
description: This page introduces how to upgrade Dynamsoft Document Normalizer
needAutoGenerateSidebar: false
permalink: /programming/javascript/upgrade-instruction.html
---

# How to Upgrade

## From version 1.x to 2.x

`DynamsoftDocumentNormalizer` SDK has been refactored to integrate with `DynamsoftCaptureVision (DCV)` architecture. To upgrade from version 1.x to 2.x, we recommend you to follow the [`User Guide`](user-guide/getting-started.md) and re-write your codes.

Here are some of the main actions you may take:

### Update the Included Headers and Linked Libraries

Since the SDK architecture is changed, you have to change your code for including the headers, linking the libraries. You can use the following code to replace your previous code.

```cpp
#include "[INSTALLATION FOLDER]/Include/DynamsoftLicense.h"
#include "[INSTALLATION FOLDER]/Include/DynamsoftCaptureVisionRouter.h"
#include "[INSTALLATION FOLDER]/Include/DynamsoftDocumentNormalizer.h"

#if defined(_WIN64) || defined(_WIN32)
    #ifdef _WIN64
        #pragma comment(lib, "[INSTALLATION FOLDER]/Lib/Windows/x64/DynamsoftLicensex64.lib")
        #pragma comment(lib, "[INSTALLATION FOLDER]/Lib/Windows/x64/DynamsoftCaptureVisionRouterx64.lib")
        #pragma comment(lib, "[INSTALLATION FOLDER]/Lib/Windows/x64/DynamsoftDocumentNormalizerx64.lib")
    #else
        #pragma comment(lib, "[INSTALLATION FOLDER]/Lib/Windows/x86/DynamsoftLicensex86.lib")
        #pragma comment(lib, "[INSTALLATION FOLDER]/Lib/Windows/x86/DynamsoftCaptureVisionRouterx86.lib")
        #pragma comment(lib, "[INSTALLATION FOLDER]/Lib/Windows/x86/DynamsoftDocumentNormalizerx86.lib")
    #endif
#endif
```

### Migrate from Class CDocumentNormalizer to Class CCaptureVisionRouter

Class `CCaptureVisionRouter` is added to replace class `CDocumentNormalizer`. The APIs can be migrated as following mapping:

| v1.x API | v2.x API |
| --- | --- |
| class dynamsoft::ddn::CDocumentNormalizer | class dynamsoft::cvr::CCaptureVisionRouter |
| DetectQuad()<br>Normalize() | [`Capture()`]({{ site.dcv_cpp_api }}capture-vision-router/single-file-processing.md#capture) |
| InitRuntimeSettingsFromString()<br>InitRuntimeSettingsFromFile()<br>OutputRuntimeSettingsToString()<br>OutputRuntimeSettingsToFile() | [`InitSettings()`]({{ site.dcv_cpp_api }}capture-vision-router/settings.html#initsettings)<br>[`InitSettingsFromFile()`]({{ site.dcv_cpp_api }}capture-vision-router/settings.html#initsettingsfromfile)<br>[`OutputSettings()`]({{ site.dcv_cpp_api }}capture-vision-router/settings.html#outputsettings)<br>[`OutputSettingsToFile()`]({{ site.dcv_cpp_api }}capture-vision-router/settings.html#outputsettingstofile) |
| class dynamsoft::ddn::CDetectedQuadResultArray<br>class dynamsoft::ddn::CNormalizedImageResult | [`class dynamsoft::basic_structures::CCapturedResultArray`]({{ site.dcv_cpp_api }}core/basic-structures/captured-result-array.html) |

### Convert Parameter Templates

The parameter system is restructured and the template you used for v1.x can't be directly recognized by the new version. Please [download the parameter upgrading tool]() to upgrade your parameter template.