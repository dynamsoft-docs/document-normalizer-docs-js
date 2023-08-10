---
layout: default-layout
title: Dynamsoft Document Normalizer for JavaScript SDK - Release Notes
description: This is the release notes page of Dynamsoft Document Normalizer for JavaScript SDK v2.0.0.
keywords: release notes, javascript, version 2
needAutoGenerateSidebar: true
needGenerateH3Content: false
noTitleIndex: true
---

# Release Notes for Dynamsoft Document Normalizer JavaScript SDK

## 2.0.10 (08/  /2023)

### Changelog

`DynamsoftDocumentNormalizer` SDK has been refactored to integrate with `DynamsoftCaptureVision (DCV)` architecture, which is newly established to aggregate the features of functional products powered by Dynamsoft. The features are designed to be pluggable, customizable and interactable. In addition, the functional products share the computation so that their processing speed is much higher than working individually.

* Class `CaptureVisionRouter` is added to replace class `DocumentNormalizer`. The `DocumentNormalizer` as a functional products are pluggable and passively called by CVR when they are required. The APIs can be migrated as following mapping:

| v1.x API                                                                                                            | v2.x API                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| ------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| class `Dynamsoft.DDN.DocumentNormalizer`                                                                            | class `Dynamsoft.CVR.CaptureVisionRouter`                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| DetectQuad()<br>Normalize()                                                                                         | [`Capture()`]({{ site.dcv_js_api }}capture-vision-router/single-file-processing.md#capture)                                                                                                                                                                                                                                                                                                                                                                                                               |
| getScanSettings()<br>updateScanSettings()<br>getRuntimeSettings()<br>setRuntimeSettings()<br>resetRuntimeSettings() | [`initSettings()`]({{ site.dcv_js_api }}capture-vision-router/settings.html#initsettings)<br>[`outputSettings()`]({{ site.dcv_js_api }}capture-vision-router/settings.html#outputsettings)<br>[`getSimplifiedSettings()`]({{ site.dcv_js_api }}capture-vision-router/settings.html#getsimplifiedsettings)<br>[`updateSettings()`]({{ site.dcv_js_api }}capture-vision-router/settings.html#updatesettings)<br>[`resetSettings()`]({{ site.dcv_js_api }}capture-vision-router/settings.html#resetsettings) |

* `ImageSourceAdapter(ISA)` is added as the standard input interface to convert image data from different sources into the standard input image data. In addition, `DynamsoftCameraEnhancer(DCE)` has been Refactored to be compliant with the ImageSourceAdapter interface so that you can easily integrate `DCE` as the input.

* `CapturedResultReceiver (CRR)` is added to receive the `CapturedResults` that output when the processing on an image is finalized. You can also implement `IntermediateResultReceiver (IRR)` to get timely results from different stages of the workflow.

* The parameter template system has been comprehensively upgraded.
  * Extended the feature of the ROI system.
  * The image processing parameters are separated from the task parameters so that the template settings become more clear and concise.
