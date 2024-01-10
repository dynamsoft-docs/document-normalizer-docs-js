---
layout: default-layout
title: Dynamsoft Document Normalizer for JavaScript SDK - V2.x  Release Notes
description: This is the release notes page of Dynamsoft Document Normalizer for JavaScript SDK v2.0.11.
keywords: release notes, javascript, version 2
needAutoGenerateSidebar: true
needGenerateH3Content: false
noTitleIndex: true
---

# Release Notes for Dynamsoft Document Normalizer JavaScript SDK

## 2.0.20 (01/11/2024)

### Added

* Added the following preset templates.
  * Default
  * ReadBarcodes_Default
  * ReadSingleBarcode
  * ReadBarcodes_SpeedFirst
  * ReadBarcodes_ReadRateFirst
  * ReadBarcodes_Balance
  * ReadDenseBarcodes
  * ReadDistantBarcodes
  * DetectDocumentBoundaries_Default
  * DetectAndNormalizeDocument_Default
  * NormalizeDocument_Default
  * RecognizeTextLines_Default
  * RecognizeNumbers
  * RecognizeLetters
  * RecognizeNumbersAndLetters
  * RecognizeNumbersAndUppercaseLetters
  * RecognizeUppercaseLetters
* Added the following static methods and properties in `CoreModule` Class.
  * CoreModule.detectEnvironment()
  * CoreModule.onWarning
  * CoreModule.engineResourcePaths
  * CoreModule.loadWasm()
  * CoreModule.loadModel()
  * CoreModule.enableLogging()
  * CoreModule.disableLogging()
* Added the property `minImageCaptureInterval` in `SimplifiedCaptureVisionSettings`.

### Changed

* Removed the class `IntermediateResultManager` in Core module. The substitute is the same class on the CaptureVisionRouter module.
* Removed the interface `CapturedResultReceiver` in Core module. The substitute is the same interface on the CaptureVisionRouter module.
* Removed the interface `IntermediateResultReceiver` in Core module. The substitute is the same interface on the CaptureVisionRouter module.
* Removed the static property `engineResourcePath` in CaptureVisionRouter module. The substitute is `CoreModule.engineResourcePaths`.
* Removed the static method `detectEnvironment()` in CaptureVisionRouter module. The substitute is `CoreModule.detectEnvironment()`.
* Removed the static property `onWarning` in CaptureVisionRouter module. The substitute is `CoreModule.onWarning`.
* Removed the static method `preLoadModule()` in CaptureVisionRouter module. The substitute is `CoreModule.loadWasm()`.
* Removed the static method `isModuleLoaded()` in CaptureVisionRouter module.

## 2.0.11 (08/24/2023)

### Changelog

In this version, the `DynamsoftDocumentNormalizer` SDK has been refactored under the `DynamsoftCaptureVision` (DCV) architecture. To learn more about the architecture, please see [Architecture of Dynamsoft Capture Vision](https://www.dynamsoft.com/capture-vision/docs/core/architecture/). The following highlights the major changes:

* The class `DocumentNormalizer` is removed and its functionalities are now incorporated into the newly added Class `CaptureVisionRouter`. Old APIs can be migrated according to the following mappings:

| v1.x API                                 | v2.x API                                                                                                       |
| ---------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| class `Dynamsoft.DDN.DocumentNormalizer` | class `Dynamsoft.CVR.CaptureVisionRouter`                                                                      |
| setImageSource()                         | [`setInput()`]({{ site.dcv_js_api }}capture-vision-router/multiple-image-processing.html#setinput)             |
| detectQuad()<br>Normalize()              | [`capture()`]({{ site.dcv_js_api }}capture-vision-router/single-image-processing.html#capture)                 |
| startScanning()                          | [`startCapturing()`]({{ site.dcv_js_api }}capture-vision-router/multiple-image-processing.html#startcapturing) |
| stopScanning()                           | [`stopCapturing()`]({{ site.dcv_js_api }}capture-vision-router/multiple-image-processing.html#stopcapturing)   |
| getRuntimeSettings()                     | [`getSimplifiedSettings()`]({{ site.dcv_js_api }}capture-vision-router/settings.html#getsimplifiedsettings)    |
| setRuntimeSettings()                     | [`updateSettings()`]({{ site.dcv_js_api }}capture-vision-router/settings.html#updatesettings)                  |
| resetRuntimeSettings()                   | [`resetSettings()`]({{ site.dcv_js_api }}capture-vision-router/settings.html#resetsettings)                    |

* License-related functions are handled by class [`Dynamsoft.License.LicenseManager`]({{ site.dcv_js_api }}license/license-manager.html#initLicense).

* This version of `DocumentNormalizer` only accepts `DynamsoftCameraEnhancer(DCE)` version 4.0 and above, which has been refactored to be compliant with the [`ImageSourceAdapter` (ISA) interface](https://www.dynamsoft.com/capture-vision/docs/core/architecture/input.html#image-source-adapter), as a valid image source.

* Detected document boundaries and normalized document images are returned via the [`CapturedResultReceiver` (CRR) interface](https://www.dynamsoft.com/capture-vision/docs/core/architecture/output.html#captured-result-receiver).
