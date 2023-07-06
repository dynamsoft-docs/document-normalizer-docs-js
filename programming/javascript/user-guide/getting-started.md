---
layout: default-layout
title: User Guide Index - Dynamsoft Capture Vision JavaScript Edition
description: This is the index page for Dynamsoft Capture Vision User Guide.
keywords: CaptureVision, Capture, User Guide, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: User Guide
---

# JavaScript User Guide

In this guide, you will learn step by step on how to build a document normalizer application with Dynamsoft Capture Vision SDK using JavaScript language.

> Read more on [Dynamsoft Capture Vision Features]({{site.introduction}})

<span style="font-size:20px">Table of Contents</span>

- [User Guide - JavaScript](#javascript-user-guide)
  - [Example Usage](#example-usage)
    - [Check the code](#check-the-code)
      - [About the code](#about-the-code)
    - [Test the code](#test-the-code)
  - [Building your own page](#building-your-own-page)
    - [Include the SDK](#include-the-sdk)
      - [Use a CDN](#use-a-cdn)
      - [Host the SDK yourself](#host-the-sdk-yourself)
    - [Configure the SDK with license](#configure-the-sdk-with-license)
    - [Interact with the SDK](#interact-with-the-sdk)
      - [Create a `CaptureVisionRouter` object](#create-a-capturevisionrouter-object)
      - [Create a `CameraEnhancer` object and bind it as input to cvr](#create-a-cameraenhancer-object-and-bind-it-as-input-to-cvr)
      - [Start the detection and normalization](#start-the-detection-and-normalization)
  - [API Documentation](#api-documentation)
  - [System Requirements](#system-requirements)
  - [Release Notes](#release-notes)
  - [Next Steps](#next-steps)

## Example Usage

Let's start by testing an example of the SDK which demonstrates how to detect quadrilaterals (document boundaries) from a live video stream and use a selected quadrilateral to obtain a normalized image of the document. To run the example, the following are required

1. Internet connection
2. [A supported browser](#system-requirements)
3. An accessible Camera

### Check the code

The complete code of the example is shown below:

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <script src="https://npm.scannerproxy.com/cdn/@scannerproxy/dynamsoft-camera-enhancer@4.0.0-dev-20230621180020/dist/dce.js"></script>
  <script src="https://npm.scannerproxy.com/cdn/@scannerproxy/cvrjs@0.20230705144027.0/dist/cvr.js"></script>
</head>
<body>
  <h1>Detect A Document Boundary</h1>
  <button onclick="start()">start capturing</button>
  <div id="uiNormalize"></div>
  <div id="uiContainer" style="width: 100vw; height: 60vh; margin-top: 10px;display: none;"></div>

  <script>
    const uiContainer = document.querySelector("#uiContainer");
    const uiNormalize = document.querySelector("#uiNormalize");
    Dynamsoft.CVR.LicenseManager.initLicense("DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9");
    Dynamsoft.CVR.CaptureVisionRouter.preloadModule(["DDN"]);

    let dce;
    let cvr;
    
    async function createInstance() {
      cvr = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
      console.log(Dynamsoft.CVR.CaptureVisionRouterModule.getVersion());
    }
    createInstance();
    async function start() {
      if (dce) return;
      uiContainer.style.display = "block";
      let view = await Dynamsoft.DCE.CameraView.createInstance();
      dce = await Dynamsoft.DCE.CameraEnhancer.createInstance(view);
      dce.setResolution({ width: 1920, height: 1080 });
      uiContainer.append(view.getUIElement());
      cvr.setInput(dce);
      await dce.open();
      await cvr.startCapturing("detect-document-boundaries");
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

#### About the code

- `Dynamsoft.CVR.LicenseManager.initLicense()`: This method is used to initialize the license using a license key string.

- `Dynamsoft.CVR.CaptureVisionRouter.preloadModule(["DDN"])`: This method is called to preload the `DocumentNormalizer` module of the CaptureVisionRouter library, Preparing for document border detection and image normalization.

- `createInstance()`: This method is called to initialize the cvr variable by creating an instance of the `CaptureVisionRouter` class. The version of the `CaptureVisionRouterModule` is logged to the console.

- `start()` : This method is defined, which performs the following tasks:
    - Checks if dce is already initialized and returns if it is (prevents reinitialization).
    - Makes the `uiContainer` visible by changing its display style property to "block."
    - Creates an instance of the `CameraView`, sets its resolution to 1920x1080, and appends its UI element to the `uiContainer`.
    - Initializes the dce variable by creating an instance of the `CameraEnhancer` with the previously created view.
    - Sets the input for the `CaptureVisionRouter` (cvr) to be the dce instance.
    - Opens the camera feed using `dce.open()`.
    - Starts capturing and detecting document boundaries using `cvr.startCapturing()`, and default template "detect-document-boundaries" is used.

### Test the code

Create a text file with the name "Detect-Boundary-From-Video-Frames.html", fill it with the code above and save. After that, open the example page in a browser, allow the page to access your camera and the video will show up on the page. After that, you can point the camera at something with a quadrilateral border to detect it.

> You can also just test it at [https://jsfiddle.net/DynamsoftTeam/]()

Please note:

- Although the page should work properly when opened directly as a file ("file:///"), it's recommended that you deploy it to a web server and access it via HTTPS.
- On first use, you need to wait a few seconds for the SDK to initialize.
- The license "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9" used in this sample is an online license and requires network connection to work.

If the test doesn't go as expected, you can [contact us](https://www.dynamsoft.com/company/customer-service/#contact).

## Building your own page

In this section, we'll break down and show all the steps required to build a web page for document capturing with DDN-JS.

### Include the SDK

#### Use a CDN

The simplest way to include the SDK is to use either the [jsDelivr](https://jsdelivr.com/) or [UNPKG](https://unpkg.com/) CDN. The "hello world" example above uses **jsDelivr**. We should also include the SDK Dynamsoft Camera Enhancer which provides camera support.

- jsDelivr

  ```html
  <script src=""></script>
  <script src=""></script>
  ```

- UNPKG

  ```html
  <script src=""></script>
  <script src=""></script>
  ```

#### Host the SDK yourself

Besides using the CDN, you can also download the SDK and host its files on your own website / server before including it in your application.

> Also read [how to do the same for Dynamsoft Camera Enhancer](https://www.dynamsoft.com/camera-enhancer/docs/programming/javascript/user-guide/index.html?ver=latest#host-the-sdk-yourself).

To download the SDK:

- yarn

  ```cmd
  yarn add 
  ```

- npm

  ```cmd
  npm install 
  ```

Depending on how you downloaded the SDK and where you put it, you can typically include it like this:

  ```html
  <script src="/dynamsoft-capture-vision-router-js-2.0.0/dist/cvr.js"></script>
  ```

or

  ```html
  <script src="/node_modules/dynamsoft-capture-vision-router/dist/cvr.js"></script>
  ```

or

  ```ts
  import { CaptureVisionRouter } from 'dynamsoft-capture-vision-router';
  ```

### Configure the SDK with license

The SDK requires a license to work, use the Dynamsoft.CVR.LicenseManager.initLicense() to specify a license key.

```javascript
Dynamsoft.CVR.LicenseManager.initLicense("YOUR-LICENSE-KEY");
```

To test the SDK, you can request a 30-day trial license via the [customer portal](https://www.dynamsoft.com/customer/license/trialLicense?utm_source=guide&product=ddn&package=js).


### Interact with the SDK

#### Create a `CaptureVisionRouter` object



#### Create a `CameraEnhancer` object and bind it as input to cvr



#### Start the detection and normalization



## API Documentation

You can check out the detailed documentation about the APIs of the SDK at
[https://www.dynamsoft.com/document-normalizer/docs/programming/javascript/api-reference/?ver=latest](https://www.dynamsoft.com/document-normalizer/docs/programming/javascript/api-reference/?ver=latest).

## System Requirements

DDN-JS SDK requires the following features to work:

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

  Browser Name | Version
  :-: | :-:
  Chrome | v85+ on desktop, v94+ on Android
  Firefox | v99+ on desktop and Android
  Safari | v15+ on iOS

Apart from the browsers, the operating systems may impose some limitations of their own that could restrict the use of the SDK.

## Release Notes

Learn about what are included in each release at [https://www.dynamsoft.com/document-normalizer/docs/programming/javascript/release-notes/?ver=latest](https://www.dynamsoft.com/document-normalizer/docs/programming/javascript/release-notes/?ver=latest).

## Next Steps


Now that you have got the SDK integrated, you can choose to move forward in the following directions

1. Check out the [official samples]().
2. Learn about the available [APIs]().