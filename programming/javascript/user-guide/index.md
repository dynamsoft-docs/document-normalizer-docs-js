---
layout: default-layout
title: User Guide - Dynamsoft Document Normalizer JavaScript Edition
description: This is the User Guide page for Dynamsoft Document Normalizer.
keywords: CaptureVision, Dynamsoft Document, User Guide, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: User Guide
---

# Dynamsoft Document Normalizer JavaScript Edition User Guide

With Dynamsoft Document Normalizer JavaScript edition, you can add to your website the ability to take pictures of documents with your camera and normalize them to obtain high-quality images for further processing or archiving purposes.

> Dynamsoft Document Normalizer v2.0.10 and above is based on Dynamsoft Capture Vision Architecture. To learn more, read [Introduction to Dynamsoft Capture Vision]({{site.dcv_introduction}}).

In this guide, you'll learn step-by-step how to build such a simple solution in a web page.

<span style="font-size:20px">Table of Contents</span>

- [Dynamsoft Document Normalizer JavaScript Edition User Guide](#dynamsoft-document-normalizer-javascript-edition-user-guide)
  - [Getting started](#getting-started)
    - [About the code](#about-the-code)
    - [Test the code](#test-the-code)
  - [Building your own page](#building-your-own-page)
    - [Include the SDK](#include-the-sdk)
      - [Use a CDN](#use-a-cdn)
      - [Host the SDK yourself](#host-the-sdk-yourself)
    - [Define necessary HTML elements](#define-necessary-html-elements)
    - [Prepare the SDK for the task](#prepare-the-sdk-for-the-task)
    - [Define the functions](#define-the-functions)
      - [Start the detection](#start-the-detection)
      - [Review and adjust a found boundary](#review-and-adjust-a-found-boundary)
      - [Normalize a document based on its adjusted boundary](#normalize-a-document-based-on-its-adjusted-boundary)
  - [System requirements](#system-requirements)
  - [Release notes](#release-notes)
  - [Next steps](#next-steps)

## Getting started

The solution consists of two steps

1. Detect the document boundaries
2. Normalize the document based on the detected boundaries

The following sample code sets up the SDK and implements boundary detection on a web page, which is just the first step in capturing a normalized image of your document. We'll cover the second step later in [Building Your Own Page](#building-your-own-page).

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <script src="https://cdn.jsdelivr.net/npm/dynamsoft-core@3.0.10/dist/core.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/dynamsoft-utility@1.0.10/dist/utility.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/dynamsoft-document-normalizer@2.0.10/dist/ddn.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/dynamsoft-capture-vision-router@2.0.10/dist/cvr.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/dynamsoft-camera-enhancer@4.0.0/dist/dce.js"></script>
</head>

<body>
    <h1>Detect the Boundary of the Document</h1>
    <button onclick="startDetecting()">Start Detecting</button>
    <div id="cameraViewContainer" style="width: 50vw; height: 45vh; margin-top: 10px; display: none"></div>

    <script>
        const cameraViewContainer = document.querySelector(
            "#cameraViewContainer"
        );
        let router;
        let cameraEnhancer;

        (async function() {
            Dynamsoft.License.LicenseManager.initLicense(
                "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9"
            );
            Dynamsoft.CVR.CaptureVisionRouter.preloadModule(["DDN"]);
            router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
            let view = await Dynamsoft.DCE.CameraView.createInstance();
            cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance(
                view
            );
            cameraViewContainer.append(view.getUIElement());
            router.setInput(cameraEnhancer);
        })();
        async function startDetecting() {
            cameraViewContainer.style.display = "block";
            await cameraEnhancer.open();
            await router.startCapturing("detect-document-boundaries");
        }
    </script>
</body>

</html>
```

<!--
<p align="center" style="text-align:center; white-space: normal; ">
  <a target="_blank" href="https://jsfiddle.net/DynamsoftTeam/5vgh7rdx/" title="Run via JSFiddle">
    <img src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/jsfiddle.svg" alt="Run via JSFiddle" width="20" height="20" style="width:20px;height:20px;">
  </a>
</p>
-->

-----

### About the code

- `Dynamsoft.CVR.LicenseManager.initLicense()`: initializes the license using a license key string.

- `Dynamsoft.CVR.CaptureVisionRouter.preloadModule(["DDN"])`: preloads the `DocumentNormalizer` module, saving time in preparing for document border detection and image normalization.

- `Dynamsoft.CVR.CaptureVisionRouter.createInstance()`: initializes the `router` variable by creating an instance of the `CaptureVisionRouter` class. An instance of `CaptureVisionRouter` is the core of any solution based on Dynamsoft Capture Vision architecture.

  > Read more on [what is CaptureVisionRouter](https://www.dynamsoft.com/capture-vision/docs/core/architecture/#capture-vision-router)

- `Dynamsoft.DCE.CameraEnhancer.createInstance(view)`: initializes the `cameraEnhancer` variable by creating an instance of the `CameraEnhancer` class.

- `setInput()`: sets `cameraEnhancer` as the image source to `router`.

  > In some cases, a different camera might be required instead of the default one. Also, a different resolution might work better. To change the camera or the resolution, use the `CameraEnhancer` instance `cameraEnhancer`. Learn more [here](https://www.dynamsoft.com/camera-enhancer/docs/programming/javascript/api-reference/camera-control.html?ver=4.0.0&utm_source=guide&product=ddn&package=js).

- `startCapturing("detect-document-boundaries")` : starts to run images through a pre-defined process which, in the case of "detect-document-boundaries", tries to find the boundary of a document present in the image(s).

### Test the code

Create a text file called "Detect-A-Document-Boundary.html", fill it with the code above and save it. After that, open the example page in your browser, allow the page to access your camera, and the video will be displayed on the page. Afterwards, you will see the detected boundaries displayed on the video in real time. 

> NOTE:
> 
> The sample code requires the following to run:
> 
> 1. Internet connection
> 2. [A supported browser](#system-requirements)
> 3. An accessible Camera

Please note:

- Although the page should work properly when opened directly as a file ("file:///"), it's recommended that you deploy it to a web server and access it via HTTPS.
- On first use, you need to wait a few seconds for the SDK to initialize.
- The license "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9" used in this sample is an online license good for 24 hours and requires network connection to work. To test the SDK further, you can request a 30-day trial license via the [customer portal](https://www.dynamsoft.com/customer/license/trialLicense?utm_source=guide&architecture=dcv&product=ddn&package=js).

<!-- You can also just test it at [https://jsfiddle.net/DynamsoftTeam/]()-->

If the test doesn't go as expected, you can [contact us](https://www.dynamsoft.com/company/customer-service/#contact).

## Building your own page

In this section, we'll break down and show all the steps needed to build the solution in a web page.

### Include the SDK

To build the solution, we need to include five packages

1. `dynamsoft-core`: includes basic classes, interfaces, and enumerations that are shared between all Dynamsoft SDKs.
2. `dynamsoft-utility`: defines auxiliary classes shared between all Dynamsoft SDKs.
3. `dynamsoft-document-normalizer`: provides functions to detect boundaries or perform normalization.
4. `dynamsoft-capture-vision-router`: defines the class `CaptureVisionRouter`, which controls the whole process.
5. `dynamsoft-camera-enhancer`: supplies image frames captured from video input.

#### Use a CDN

The simplest way to include the SDK is to use either the [jsDelivr](https://jsdelivr.com/) or [UNPKG](https://unpkg.com/) CDN.

- jsDelivr

  ```html
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-core@3.0.10/dist/core.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-utility@1.0.10/dist/utility.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-document-normalizer@2.0.10/dist/ddn.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-capture-vision-router@2.0.10/dist/cvr.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-camera-enhancer@4.0.0/dist/dce.js"></script>
  ```

- UNPKG

  ```html
  <script src="https://unpkg.com/dynamsoft-core@3.0.10/dist/core.js"></script>
  <script src="https://unpkg.com/dynamsoft-utility@1.0.10/dist/utility.js"></script>
  <script src="https://unpkg.com/dynamsoft-document-normalizer@2.0.10/dist/ddn.js"></script>
  <script src="https://unpkg.com/dynamsoft-capture-vision-router@2.0.10/dist/cvr.js"></script>
  <script src="https://unpkg.com/dynamsoft-camera-enhancer@4.0.0/dist/dce.js"></script>
  ```

#### Host the SDK yourself

Besides using the CDN, you can also download the SDK and host its files on your own website / server before including it in your application.

> Also read [how to do the same for Dynamsoft Camera Enhancer](https://www.dynamsoft.com/camera-enhancer/docs/programming/javascript/user-guide/index.html?ver=latest#host-the-sdk-yourself).

To download the SDK:

- yarn

  ```cmd
  yarn add dynamsoft-document-normalizer@2.0.10
  ```

- npm

  ```cmd
  npm install dynamsoft-document-normalizer@2.0.10
  ```

Depending on how you downloaded the SDK and where you put it, you can typically include it like this:

  ```html
  <script src="/dynamsoft-core-js-3.0.10/dist/core.js"></script>
  <script src="/dynamsoft-utility-js-1.0.10/dist/utility.js"></script>
  <script src="/dynamsoft-document-normalizer-js-2.0.10/dist/ddn.js"></script>
  <script src="/dynamsoft-capture-vision-router-js-2.0.10/dist/cvr.js"></script>
  <script src="/dynamsoft-camera-enhancer-js-4.0.0/dist/dce.js"></script>
  ```

or

  ```html
  <script src="/node_modules/dynamsoft-core-js-3.0.10/dist/core.js"></script>
  <script src="/node_modules/dynamsoft-utility-js-1.0.10/dist/utility.js"></script>
  <script src="/node_modules/dynamsoft-document-normalizer-js-2.0.10/dist/ddn.js"></script>
  <script src="/node_modules/dynamsoft-capture-vision-router-js-2.0.10/dist/cvr.js"></script>
  <script src="/node_modules/dynamsoft-camera-enhancer-js-4.0.0/dist/dce.js"></script>
  ```

or

  ```ts
  import { Core } from 'dynamsoft-core';
  import { Utility } from 'dynamsoft-utility';
  import { DocumentNormalizer } from 'dynamsoft-document-normalizer';
  import { CaptureVisionRouter } from 'dynamsoft-capture-vision-router';
  import { CameraEnhancer } from 'dynamsoft-camera-enhancer';
  ```

### Define necessary HTML elements

For this solution, we define two buttons and three `<div>` elements.

```html
<button onclick="startDetecting()">Start Detecting</button>
<button onclick="normalizeImage()">Normalize Image</button>
<div id="cameraViewContainer" style="width: 50vw; height: 45vh; margin-top: 10px; display: none"></div>
<div id="imageEditorViewContainer" style="width: 80vw; height: 50vh"></div>
<div id="normalizedImageContainer"></div>
```

```js
const cameraViewContainer = document.querySelector(
    "#cameraViewContainer"
);
const imageEditorViewContainer = document.querySelector(
    "#imageEditorViewContainer"
);
const normalizedImageContainer = document.querySelector(
    "#normalizedImageContainer"
);
```

### Prepare the SDK for the task

The following function executes as soon as the page loads to get the SDK prepared:

```js
let router;
let cameraEnhancer;
let imageEditorView;
(async function() {
    Dynamsoft.License.LicenseManager.initLicense(
        "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9"
    );
    Dynamsoft.CVR.CaptureVisionRouter.preloadModule(["DDN"]);
    router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
    let view = await Dynamsoft.DCE.CameraView.createInstance();
    cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance(
        view
    );
    cameraEnhancer.setResolution({
        width: 1920,
        height: 1080,
    });
    cameraViewContainer.append(view.getUIElement());
    router.setInput(cameraEnhancer);
})();
```

The code was explained earlier. Please refer to [About the Code](#about-the-code).

### Define the functions

#### Start the detection

Before we start the detection process with `startDetecting()`, we need to define a callback function to accept the detected document boundaries. The callback function is defined based on the `CapturedResultReceiver` interface.

> Read more on [`CapturedResultReceiver`]({{ site.dcv_js_api }}core/basic-structures/captured-result-receiver.html)

```js
let crr = {
    onDetectedQuadsReceived(pResult) {
        items = pResult.quadsResultItems;
        console.log(items);
    }
};
```

And we define the function like this:

```js
async function startDetecting() {
    // Show the cameraView
    cameraViewContainer.style.display = "block";
    // Specifiy the result receiver
    router.addResultReceiver(crr);
    // Start streaming the video
    await cameraEnhancer.open();
    // Use the built-in template "detect-document-boundaries" to start a boundary detecting task
    await router.startDetecting("detect-document-boundaries");
}
```

The steps of the workflow is as follows

1. `cameraEnhancer` streams the video, captures live video frames and stores them in a buffer.
2. `router` gets the video frames from `cameraEnhancer` and passes them to be processed by an internal `DocumentNormalizer` instance.
3. The internal `DocumentNormalizer` instance returns the found document boundaries, known as `quadsResultItems`, to `router`.
4. `router` outputs the `quadsResultItems` via the callback function `onDetectedQuadsReceived`.

> Also note that the `quadsResultItems` are drawn over the video automatically to show the detection in action.

#### Review and adjust a found boundary

The SDK tries to find the boundary of the document in each and every image processed. This happens very fast and we don't always get the perfect boundary for normalization. Therefore, we can draw the image and the boundary in the `ImageEditorView` and let the user adjust the boundary before proceed to normalization.

To do this, we define the function `editBoundary()` like this

```js
async function editBoundary(imageData, points) {
    // Stop the previous detecting task since we assume we have found a good boundary
    router.stopCapturing();
    // Create an ImageEditorView inside the div "imageEditorViewContainer"
    if (imageEditorView == undefined) {
        imageEditorView = await Dynamsoft.DCE.ImageEditorView.createInstance(
            imageEditorViewContainer
        );
    }
    // Create a drawinglayer to draw the quad
    let layer;
    if (imageEditorView.getAllDrawingLayers().length > 0)
        layer = imageEditorView.getAllDrawingLayers()[0];
    else layer = imageEditorView.createDrawingLayer();
    // Hide the cameraView and show the imageEditorView
    cameraViewContainer.style.display = "none";
    imageEditorViewContainer.style.display = "block";
    // Draw the image in the imageEditorView first
    imageEditorView.setOriginalImage(imageData);
    // Draw the quad
    const quad = new Dynamsoft.DCE.DrawingItem.QuadDrawingItem({
        points,
    });
    layer.setDrawingItems([quad]);
}
```

Since we will need the original image returned, we update `startDetecting()` like this:

```js
async function startDetecting() {
    cameraViewContainer.style.display = "block";
    router.addResultReceiver(crr);
    await cameraEnhancer.open();
    // Update the settings for "detect-document-boundaries" to return the original image
    let settings = await router.getSimplifiedSettings(
        "detect-document-boundaries"
    );
    settings.capturedResultItemTypes +=
        Dynamsoft.Core.EnumCapturedResultItemType.CRIT_ORIGINAL_IMAGE;
    await router.updateSettings("detect-document-boundaries", settings);
    await router.startCapturing("detect-document-boundaries");
}
```

Then we update the callback function to do 2 things:

1. Detect whether a found boundary is good by checking its property `confidenceAsDocumentBoundary`
2. If a good boundray is found, carry on to invoke the function `editBoundary()`
  > Note that in order to get both the boundary result and the original image, we use the callback function `onCapturedResultReceived` instead

```js
let crr = {
    onCapturedResultReceived: (result) => {
        let confidentBoundaryPoints = null;
        let readyToAdjustBoundary = false;
        if (result.items && result.items.length > 0) {
            for (let i = 0; i < result.items.length; i++) {
                let resultItem = result.items[i];
                if (
                    resultItem.type ==
                    Dynamsoft.Core.EnumCapturedResultItemType.CRIT_DETECTED_QUAD
                ) {
                    // Check the confidence score of the found boundary
                    if (resultItem.confidenceAsDocumentBoundary > 75) {
                        readyToAdjustBoundary = true;
                        confidentBoundaryPoints = resultItem.location.points;
                    }
                }
            }
        }
        if (result.items && result.items.length > 0) {
            for (let i = 0; i < result.items.length; i++) {
                let resultItem = result.items[i];
                if (
                    resultItem.type ==
                    Dynamsoft.Core.EnumCapturedResultItemType.CRIT_ORIGINAL_IMAGE
                ) {
                    if (readyToAdjustBoundary && confidentBoundaryPoints) {
                        // When the boundary is good, carry on to invoke editBoundary()
                        editBoundary(resultItem.imageData, confidentBoundaryPoints);
                    }
                }
            }
        }
    },
};
```

Now, the behavior will be

1. The page constantly detect the boundary of the document in the video
2. When the found boundary has a confidence score of 75 or more, the page hides the video stream and draw both the image and the boundary in the "imageEditorViewer"
3. The user can adjust the boundary to be more precise

#### Normalize a document based on its adjusted boundary

After the user has adjusted the boundary or determined that the found boundary is good enough, he can press the button "Normaize Image" to carry out the normalization as the last step of the solution.

The function `normalizeImage()` is defined like this:

```js
async function normalizeImage() {
    // Hide the imageEditorView
    imageEditorViewContainer.style.display = "none";
    // Remove the old normalized image if any
    normalizedImageContainer.innerHTML = "";
    // Get the boundary from the imageEditorView
    let boundaryQuad = null;
    let seletedItems = imageEditorView.getSelectedDrawingItems();
    if (seletedItems.length == 0) {
        let layer = imageEditorView.getAllDrawingLayers()[0];
        boundaryQuad = layer.getDrawingItems()[0];
    } else {
        boundaryQuad = seletedItems[0];
    }
    // Get the original image to normalize
    let originalImage = imageEditorView.getOriginalImage();
    await router.resetSettings();
    let quad = boundaryQuad.getQuad();
    // Update the template "normalize-document" with the boundary
    let newSettings = await router.getSimplifiedSettings(
        "normalize-document"
    );
    newSettings.roi.points = quad.points;
    newSettings.roiMeasuredInPercentage = 0;
    await router.updateSettings("normalize-document", newSettings);
    // Normalize and show the result image
    let normalizeResult = await router.capture(originalImage, "normalize-document");
    normalizedImageContainer.append(normalizeResult.items[0].toCanvas());
}
```

The added behavior is

1. The user hits "Normalize Image"
2. The page gets the boundary normzlie the image based on it
3. The normalized image shows up on the page

## System requirements

The SDK requires the following features to work:

- Secure context (HTTPS deployment)

  When deploying your application / website for production, make sure to serve it via a secure HTTPS connection. This is required for two reasons
  
  - Access to the camera video stream is only granted in a security context. Most browsers impose this restriction.
  > Some browsers like Chrome may grant the access for `http://127.0.0.1` and `http://localhost` or even for pages opened directly from the local disk (`file:///...`). This can be helpful for temporary development and test.
  
  - Dynamsoft License requires a secure context to work.

- `WebAssembly`, `Blob`, `URL`/`createObjectURL`, `Web Workers`

  The above four features are required for the SDK to work.

- `MediaDevices`/`getUserMedia`

  This API is only required for in-browser video streaming.

- `getSettings`

  This API inspects the video input which is a `MediaStreamTrack` object about its constrainable properties.

The following table is a list of supported browsers based on the above requirements:

  | Browser Name |             Version              |
  | :----------: | :------------------------------: |
  |    Chrome    | v85+ on desktop, v94+ on Android |
  |   Firefox    |   v99+ on desktop and Android    |
  |    Safari    |           v15+ on iOS            |

Apart from the browsers, the operating systems may impose some limitations of their own that could restrict the use of the SDK.

## Release notes

Learn what are included in each release at [https://www.dynamsoft.com/document-normalizer/docs/programming/javascript/release-notes/?ver=latest](https://www.dynamsoft.com/document-normalizer/docs/programming/javascript/release-notes/?ver=latest).

## Next steps

Now that you have got the SDK integrated, you can choose to move forward in the following directions

1. Check out the [official samples](https://github.com/Dynamsoft/document-normalizer-javascript-samples).
2. Learn about the available [APIs](https://www.dynamsoft.com/document-normalizer/docs/web/programming/javascript/api-reference/?ver=latest).
