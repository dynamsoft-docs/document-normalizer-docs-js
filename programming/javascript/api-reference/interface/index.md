---
layout: default-layout
title: Dynamsoft Document Normalizer JavaScript API Reference - Main Page
description: This is the main page of Dynamsoft Document Normalizer for JavaScript SDK API Reference.
keywords: DocumentNormalizer, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
breadcrumbText: API Reference
noTitleIndex: true
permalink: /programming/javascript/api-reference/index.html
---

# API Reference - JavaScript

The primary class of the library is `DocumentNormalizer`. The following code snippets shows the basic usage. 

* Detect and normalize a still image

```js
let normalizer = await Dynamsoft.DDN.DocumentNormalizer.createInstance();
let quads = await normalizer.detectQuad(imagePath);
let normalizedImageResult = await normalizer.normalize(imagePath, { quad: quads[0].location });
if(normalizedImageResult) {
    // Show the normalized image in a Canvas
    const cvs = normalizedImageResult.image.toCanvas();
    document.querySelector("#normalized-result").appendChild(cvs);
}
// Download the normalized image
let img = await normalizedImageResult.saveToFile("example.png", true);
```

* Detect and normalize continuous video frames

```js
(async function() {
    cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
    normalizer = await Dynamsoft.DDN.DocumentNormalizer.createInstance();
    await normalizer.setImageSource(cameraEnhancer, { resultsHighlightBaseShapes: Dynamsoft.DCE.DrawingItem });

    await document.getElementById('div-ui-container').append(cameraEnhancer.getUIElement());
    
    // Triggered when a quadrilateral is detected from a video frame.
    normalizer.onQuadDetected = (quadResults, sourceImage) => {
        console.log(quadResults);
    };

    // Click the button to pause the video and edit a quadrilateral.
    document.getElementById('confirmQuadForNormalization').addEventListener("click", () => {
        normalizer.confirmQuadForNormalization();
    });

    // Click the button to normalize with the selected/adjusted quadrilateral.
    document.getElementById('normalizeWithConfirmedQuad').addEventListener("click", async () => {
        const normalizedImageResult = await normalizer.normalizeWithConfirmedQuad();
        if(normalizedImageResult) {
        // Show the normalized image in a Canvas
        const cvs = normalizedImageResult.image.toCanvas();
        document.querySelector("#normalized-result").appendChild(cvs);
        console.log(normalizedImageResult);
        }
    });
    // Start scanning document boundaries.
    await normalizer.startScanning(true);
})();
```

The APIs for this class include

## Initialization Control

| Method               | Description |
|----------------------|-------------|
| [license()]({{ site.js_api }}initialize.html#license) | Uses an alphanumeric string to specify the license. |
| [createInstance()]({{ site.js_api }}initialize.html#createinstance) | Creates a `DocumentNormalizer` instance. |
| [dispose()]({{ site.js_api }}initialize.html#dispose) | Dispose the DocumentNormalizer instance. |
| [disposed()](initialize.html#disposed) | Returns whether the instance has been disposed. |
| [engineResourcePath()](initialize.html#engineresourcepath) | Specifies the path from where the engine and models, etc. can be loaded. |
| [loadWasm()]({{ site.js_api }}initialize.html#loadwasm) | Loads the engine. |
| [isWasmLoaded()]({{ site.js_api }}initialize.html#iswasmloaded) | Returns whether the engine has been loaded. |
| [getVersion()]({{ site.js_api }}initialize.html#getversion) | Returns the version of the library. |

## Video Detecting Methods

| Method               | Description |
|----------------------|-------------|
| [setImageSource()]({{ site.js_api }}normalize.html#setimagesource) | Sets an image source for continous scanning. |
| [onQuadDetected()]({{ site.js_api }}normalize.html#onquaddetected) | This event is triggered when a new quadrilateral is detected. |
| [setQuadResultFilter()]({{ site.js_api }}normalize.html#setquadresultfilter) | Sets a function to filter a detected quadrilateral. |
| [confirmQuadForNormalization()]({{ site.js_api }}normalize.html#confirmquadfornormalization) | Confirms which quadrilateral will be referred for later normalization. |
| [normalizeWithConfirmedQuad()]({{ site.js_api }}normalize.html#normalizewithconfirmedquad) | Normalizes the image whith a selected quadrilateral. |
| [startScanning()]({{ site.js_api }}normalize.html#startscanning) | Opens the camera and starts continuous scanning of incoming images. |
| [pauseScanning()]({{ site.js_api }}normalize.html#pausescanning) | Pauses continuous scanning but keep the video stream. |
| [resumeScanning()]({{ site.js_api }}normalize.html#resumescanning) | Resumes continuous scanning. |
| [stopScanning()]({{ site.js_api }}normalize.html#stopscanning) | Stops continuous scanning and closes the video stream. |

## Detect and Normalize Methods

| Method               | Description |
|----------------------|-------------|
| [detectQuad()]({{ site.js_api }}normalize.html#detectquad) | Detects quadrilaterals from an image. |
| [normalize()]({{ site.js_api }}normalize.html#normalize) | Normalizes the source image based on the settings in options. |

## Scan Settings Methods

| Method               | Description |
|----------------------|-------------|
| [getScanSettings()]({{ site.js_api }}settings.html#getscansettings) | Returns the current [`ScanSettings`]({{ site.js_api }}interfaces/scansettings.html). |
| [updateScanSettings()]({{ site.js_api }}settings.html#updatescansettings) | Updates scan settings with the object passed in. |

## Runtime Settings Methods

| Method               | Description |
|----------------------|-------------|
| [getRuntimeSettings()]({{ site.js_api }}settings.html#getruntimesettings) | Gets runtime settings with a template represented by a JSON object. |
| [setRuntimeSettings()]({{ site.js_api }}settings.html#setputruntimesettings) | Sets runtime settings with a JSON object. |
| [resetRuntimeSettings()]({{ site.js_api }}settings.html#resetputruntimesettings) | Resets all parameters to default values. |

## Interfaces

* [`DetectedQuadResult`]({{ site.js_api }}interfaces/detected-quad-result.html)
* [`NormalizedImageResult`]({{ site.js_api }}interfaces/normalized-image-result.html)
* [`ScanSettings`]({{ site.js_api }}interfaces/scansettings.html)
* [`Quadrilateral`]({{ site.js_api }}interfaces/quadrilateral.html)
* [`Point`]({{ site.js_api }}interfaces/point.html)
* [`ImageSource`]({{ site.js_api }}interfaces/imagesource.html)
* [`DDNImage`]({{ site.js_api }}interfaces/ddn-image.html)
* [`DSImage`]({{ site.js_api }}interfaces/dsimage.html)

<!-- ## Enumerations

- [`EnumImagePixelFormat`]({{ site.enumerations }}image-pixel-format.html?src=android)

## Others

View the [Error Codes]({{ site.enumerations }}error-code.html) -->
