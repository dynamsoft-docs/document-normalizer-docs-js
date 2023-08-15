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
    - [Configure the license](#configure-the-license)
    - [Use the SDK](#use-the-sdk)
      - [Create a CaptureVisionRouter instance](#create-a-capturevisionrouter-instance)
      - [Create a CameraEnhancer instance as the input](#create-a-cameraenhancer-instance-as-the-input)
      - [Start the detection](#start-the-detection)
      - [Review and adjust a found boundary](#review-and-adjust-a-found-boundary)
      - [Normalize a document based on its adjusted boundary](#normalize-a-document-based-on-its-adjusted-boundary)
  - [System Requirements](#system-requirements)
  - [Release Notes](#release-notes)
  - [Next Steps](#next-steps)

## Getting started

The solution consists of two steps

1. Detect the document boundaries
2. Normalize the document based on the detected boundaries

The following sample code sets up the SDK and implements boundary detection on a web page, which is just the first step in capturing a normalized image of your document. We'll cover the second step later in [Building Your Own Page](#building-your-own-page).

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <script src="https://npm.scannerproxy.com/cdn/@scannerproxy/dynamsoft-core@3.0.10/dist/core.js"></script>
    <script src="https://npm.scannerproxy.com/cdn/@scannerproxy/dynamsoft-utility@1.0.10/dist/utility.js"></script>
    <script src="https://npm.scannerproxy.com/cdn/@scannerproxy/dynamsoft-document-normalizer@2.0.10/dist/ddn.js"></script>
    <script src="https://npm.scannerproxy.com/cdn/@scannerproxy/dynamsoft-capture-vision-router@2.0.10/dist/cvr.js"></script>
    <script src="https://npm.scannerproxy.com/cdn/@scannerproxy/dynamsoft-camera-enhancer@4.0.0/dist/dce.js"></script>
</head>
<body>
    <h1>Detect the Boundary of the Document</h1>
    <button onclick="start()">Start Capturing</button>
    <div id="uiNormalize"></div>
    <div id="uiContainer" style="width: 50vw; height: 45vh; margin-top: 10px; display: none;"></div>

    <script>
        const uiContainer = document.querySelector("#uiContainer");
        const uiNormalize = document.querySelector("#uiNormalize");
        let cameraEnhancer;
        let router;

        (async function() {
            Dynamsoft.CVR.LicenseManager.initLicense("DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9");
            Dynamsoft.CVR.CaptureVisionRouter.preloadModule(["DDN"]);
            router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
            let view = await Dynamsoft.DCE.CameraView.createInstance();
            cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance(view);
            cameraEnhancer.setResolution({
                width: 1920,
                height: 1080
            });
            uiContainer.append(view.getUIElement());
            router.setInput(cameraEnhancer);
        })();
        async function start() {
            uiContainer.style.display = "block";
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

- `Dynamsoft.CVR.CaptureVisionRouter.createInstance()`: initializes the `router` variable by creating an instance of the `CaptureVisionRouter` class.

- `Dynamsoft.DCE.CameraEnhancer.createInstance(view)`: initializes the `cameraEnhancer` variable by creating an instance of the `CameraEnhancer` class.

- `setInput()`: sets `cameraEnhancer` as the image source to `router`.

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
- The license "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9" used in this sample is an online license and requires network connection to work.

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

### Configure the license

The SDK requires a license to work, use `Dynamsoft.License.LicenseManager.initLicense()` to specify a license key.

```javascript
Dynamsoft.License.LicenseManager.initLicense("YOUR-LICENSE-KEY");
```

To test the SDK, you can request a 30-day trial license via the [customer portal](https://www.dynamsoft.com/customer/license/trialLicense?utm_source=guide&architecture=dcv&product=ddn&package=js).

### Use the SDK

#### Create a CaptureVisionRouter instance

Create an instance of `CaptureVisionRouter`.

```js
let router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
```

#### Create a CameraEnhancer instance as the input

The `CameraEnhancer` instance is necessary to access the camera to display the video stream and draw the found document boundary.

```html
<div id="uiContainer" style="width: 50vw; height: 45vh; margin-top: 10px; display: none;"></div>
```

```js
// Create a CameraView to host the UI element such as the HTMLVideoElement
let view = await Dynamsoft.DCE.CameraView.createInstance();
// Establish the connection to the CameraView elements
cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance(view);
// Append the CameraView UI to the DOM
const uiContainer = document.querySelector("#uiContainer");
uiContainer.append(view.getUIElement());
// Set the CameraEnhancer instance as the input to router
router.setInput(cameraEnhancer);
```

In some cases, a different camera might be required instead of the default one. Also, a different resolution might work better. To change the camera or the resolution, we use the `CameraEnhancer` instance (`cameraEnhancer` in our case). Learn more [here](https://www.dynamsoft.com/camera-enhancer/docs/programming/javascript/api-reference/camera-control.html?ver=4.0.0&utm_source=guide&product=ddn&package=js).

#### Start the detection

Define a callback function to accept the detected document boundaries. Then, as the last step, call the method `startCapturing()` to start the process.

> Read more on [`CapturedResultReceiver`]({{ site.dcv_js_api }}core/basic-structures/captured-result-receiver.html)

```js
let crr = {
    onDetectedQuadsReceived(pResult) {
        items = pResult.quadsResultItems;
    }
};
router.addResultReceiver(crr);
cameraEnhancer.open();
router.startCapturing("detect-document-boundary");
```

The steps of the workflow is as follows

1. `cameraEnhancer` streams the video, captures live video frames and stores them in a buffer.
2. `router` gets the video frames from `cameraEnhancer` and passes them to be processed by an internal `DocumentNormalizer` instance.
3. The internal `DocumentNormalizer` instance returns the found document boundaries, known as `quadsResultItems`, to `router`.
4. `router` outputs the `quadsResultItems` via the callback function `onDetectedQuadsReceived`.

#### Review and adjust a found boundary

```html
<button onclick="editBoundary()">Edit Boundary</button>
<div id="div-image-container" style="width: 80vw; height: 70vh">
    <div class="dce-image-container" style="width: 100%; height: 100%"></div></div>
</div>
```

```js
const imageContainer = document.querySelector("#div-image-container");
let items;
async function editBoundary() {
    imageEditorView = await Dynamsoft.DCE.ImageEditorView.createInstance(imageContainer);
    layer = imageEditorView.createDrawingLayer();
    uiContainer.style.display = "none";
    imageContainer.style.display = "block";
    image = cameraEnhancer.fetchImage();
    imageEditorView.setOriginalImage(image);
    quads = [];
    for (let i = 0; i < items.length; i++) {
        const points = items[i].location.points;
        const quad = new Dynamsoft.DCE.DrawingItem.QuadDrawingItem({ points });
        quads.push(quad);
        layer.addDrawingItems(quads);
    }
    router.stopCapturing();
}
```

The steps of manually correction of boundary are

1. Creates an instance of `imageEditorView` and attaches it to the imageContainer element.
2. Fetches the captured image using `fetchImage()` and sets it as the original image.
3. Edit the boundaries, then save the new quadrilateral information to `quads`.

#### Normalize a document based on its adjusted boundary

```html
<button onclick="normalizeImage()">Normalize Image</button>
```

```js
let image;
async function normalizeImage() {
    imageContainer.style.display = "none";
    uiNormalize.innerHTML = "";
    let seletedItems = imageEditorView.getSelectedDrawingItems();
    for (let i = 0; i < seletedItems.length; i++) {
        await router.resetSettings();
        let quad = seletedItems[i].getQuad();
        let newSettings = await router.getSimplifiedSettings("normalize-document");
        newSettings.roi.points = quad.points;
        newSettings.roiMeasuredInPercentage = 0;
        await router.updateSettings("normalize-document", newSettings);
        let norRes = await router.capture(image, "normalize-document");
        uiNormalize.append(norRes.items[0].toCanvas());
    }
}
```

The last steps of Image Normalization are:

1. Using `getQuad()` to retrieve the boundary quad of the current selected item.
2. Retrieves `simplifiedSettings` for normalization, updates the `quad` as the region of interest(ROI).
3. Do only normalize process by using preset template "normalize-document".

<!-- 
There is a slight difference between the way you handle individual images and video streams. The code snippet shown here does border detection and normalization on a static image. We use method capture() to accomplish this process.

```js
let imagefilepath = "YOUR-IMAGE-FILE-PATH";
const uiNormalize = document.querySelector("#uiNormalize");
results = await router.capture(imagefilepath, "detect-and-normalize-document");
results.items.forEach(async (item) => {
  // Or it could be written like this -> item.type === EnumCapturedResultItemType.CRIT_NORMALIZED_IMAGE
  if (item.type === 16) {
      uiNormalize.innerHTML = "";
      uiNormalize.appendChild(item.toImage());
      console.log(await item.saveToFile("sample.jpeg"));
  }
})
```

Please note: Method `capture()` only process an image or single page file.
 -->

## System Requirements

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

## Release Notes

Learn what are included in each release at [https://www.dynamsoft.com/document-normalizer/docs/programming/javascript/release-notes/?ver=latest](https://www.dynamsoft.com/document-normalizer/docs/programming/javascript/release-notes/?ver=latest).

## Next Steps

Now that you have got the SDK integrated, you can choose to move forward in the following directions

1. Check out the [official samples](https://github.com/Dynamsoft/document-normalizer-javascript-samples).
2. Learn about the available [APIs](https://www.dynamsoft.com/document-normalizer/docs/web/programming/javascript/api-reference/?ver=latest).
