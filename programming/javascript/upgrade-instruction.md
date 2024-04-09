---
title: Upgrade Instructions - Dynamsoft Document Normalizer JavaScript Edition
keywords: JavaScript, JS, upgrade
description: This page introduces how to upgrade Dynamsoft Document Normalizer
needAutoGenerateSidebar: false
permalink: /programming/javascript/upgrade-instruction.html
---

# How to Upgrade

## From version 2.0.11 to 2.x latest

In version 2.0.20 and beyond, some of the functional modules and certain API have been relocated to other modules.

To upgrade, here are some of the main actions you may take:

### Update the Included Packages

Due to changes in the SDK architecture, adjustments are necessary in your code for including the packages. If you utilize a **CDN**, you can seamlessly replace your existing code with the following snippet.

- jsDelivr

  ```html
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-core@3.2.10/dist/core.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-license@3.2.10/dist/license.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-utility@1.0.20/dist/utility.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-document-normalizer@2.2.10/dist/ddn.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-capture-vision-router@2.2.10/dist/cvr.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-camera-enhancer@4.0.2/dist/dce.js"></script>
  ```

- UNPKG
  ```html
  <script src="https://unpkg.com/dynamsoft-core@3.2.10/dist/core.js"></script>
  <script src="https://unpkg.com/dynamsoft-license@3.2.10/dist/license.js"></script>
  <script src="https://unpkg.com/dynamsoft-utility@1.0.20/dist/utility.js"></script>
  <script src="https://unpkg.com/dynamsoft-document-normalizer@2.2.10/dist/ddn.js"></script>
  <script src="https://unpkg.com/dynamsoft-capture-vision-router@2.2.10/dist/cvr.js"></script>
  <script src="https://unpkg.com/dynamsoft-camera-enhancer@4.0.2/dist/dce.js"></script>
  ```

or

- [Download the JavaScript ZIP package](https://www.dynamsoft.com/document-normalizer/downloads/?utm_source=guide) and [host the SDK yourself](user-guide/index.md#host-the-sdk-yourself).

### Update the resource paths

* If you utilized `engineResourcePath` to designate the paths of engine files (*.worker.js, *.wasm.js, *.wasm, etc.) in version 2.0.11, the updated approach requires using `Dynamsoft.Core.CoreModule.engineResourcePaths` to define them. More details can be found in the [user guide](https://officecn.dynamsoft.com:808/document-normalizer/docs/web/programming/javascript/user-guide/index.html#specify-the-location-of-the-engine-files-optional).

* The API for preloading resources has also been refactored. Instead of `Dynamsoft.CVR.CaptureVisionRouter.preloadModule()`, please use use `Dynamsoft.Core.CoreModule.loadWasm()`.

| v2.0.11 API             | v2.0.20+ API                                                                        |
| ---------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| Dynamsoft.CVR.CaptureVisionRouter.engineResourcePath               | Dynamsoft.Core.CoreModule.engineResourcePaths                                                                               |
| Dynamsoft.CVR.CaptureVisionRouter.preloadModule()                       | Dynamsoft.Core.CoreModule.loadWasm()                                                                                      |

### Update the preset template names

We have made the following adjustments to the naming of the preset templates:

| v2.0.11 Preset Templates           | v2.0.20+ Preset Templates                                                                         |
| ---------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| detect-document-boundaries               | DetectDocumentBoundaries_Default                                                                               |
| normalize-document                       | NormalizeDocument_Default                                                                                      |
| detect-and-normalize-document            | DetectAndNormalizeDocument_Default                                                                             |

While we have ensured compatibility of the 2.0.11 template names in the new version, please note that maintenance and upgrades for the preset templates will exclusively apply to the newly named templates. Consequently, we strongly recommend that you modify the code to use the updated names to ensure updated references to the preset templates.

## From version 1.x to 2.x latest

`DynamsoftDocumentNormalizer` SDK has been revamped to integrate with `DynamsoftCaptureVision (DCV)` architecture. To upgrade from version 1.x to 2.x, we recommend you to follow the [`User Guide`](user-guide/getting-started.md) and re-write your codes.

Here are some of the main actions you may take:

### Update the Included Headers and Linked Libraries

Since the SDK architecture is changed, you have to change your code for including the packages. You can use the following code to replace your previous code.

- jsDelivr

  ```html
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-core@3.2.10/dist/core.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-license@3.2.10/dist/license.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-utility@1.0.20/dist/utility.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-document-normalizer@2.2.10/dist/ddn.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-capture-vision-router@2.2.10/dist/cvr.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-camera-enhancer@4.0.2/dist/dce.js"></script>
  ```

- UNPKG
  ```html
  <script src="https://unpkg.com/dynamsoft-core@3.2.10/dist/core.js"></script>
  <script src="https://unpkg.com/dynamsoft-license@3.2.10/dist/license.js"></script>
  <script src="https://unpkg.com/dynamsoft-utility@1.0.20/dist/utility.js"></script>
  <script src="https://unpkg.com/dynamsoft-document-normalizer@2.2.10/dist/ddn.js"></script>
  <script src="https://unpkg.com/dynamsoft-capture-vision-router@2.2.10/dist/cvr.js"></script>
  <script src="https://unpkg.com/dynamsoft-camera-enhancer@4.0.2/dist/dce.js"></script>
  ```

or

- [Download the JavaScript ZIP package](https://www.dynamsoft.com/document-normalizer/downloads/?utm_source=guide) and host the SDK yourself

### Migrate from Class CDocumentNormalizer to Class CCaptureVisionRouter

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

* License-related functions are handled by class [`Dynamsoft.License.LicenseManager`]({{ site.dcv_js_api }}license/license-manager.html#initLicense) now.

* This version of `DocumentNormalizer` only accepts `DynamsoftCameraEnhancer(DCE)` version 4.0 and above, which has been refactored to be compliant with the [`ImageSourceAdapter` (ISA) interface](https://www.dynamsoft.com/capture-vision/docs/core/architecture/input.html#image-source-adapter), as a valid image source.

* Detected document boundaries and normalized document images are returned via the [`CapturedResultReceiver` (CRR) interface](https://www.dynamsoft.com/capture-vision/docs/core/architecture/output.html#captured-result-receiver).

### Convert Parameter Templates

The parameter system is restructured and the template you used for v1.x can't be directly recognized by the new version. Please <a href="https://download2.dynamsoft.com/dcv/TemplateConverter.zip" target="_blank">download the TemplateConverter tool</a> or <a href="https://www.dynamsoft.com/company/customer-service/#contact" target="_blank">contact us</a> to upgrade your template.