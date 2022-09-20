---
layout: default-layout
title: Dynamsoft Document Normalizer for JavaScript - User Guide
description: This is the user guide of Dynamsoft Document Normalizer for JavaScript SDK.
keywords: user guide, javascript
needAutoGenerateSidebar: true
needGenerateH4Content: true
noTitleIndex: true
---

# Dynamsoft Document Normalizer for Your Website

Common normalizations include：Border crop, Deskew, Perspective correction, Colour mode, Brightness and Contrast.

<!-- ![version](https://img.shields.io/npm/v/dynamsoft-document-normalizer.svg)
![downloads](https://img.shields.io/npm/dm/dynamsoft-document-normalizer.svg)
![jsdelivr](https://img.shields.io/jsdelivr/npm/hm/dynamsoft-document-normalizer.svg)
![vulnerabilities](https://img.shields.io/snyk/vulnerabilities/npm/dynamsoft-document-normalizer.svg) -->

Once integrated, your users can open your website in a browser, access their cameras, and detect and normalize the images directly from the video input.

In this guide, you will learn step by step on how to integrate this SDK into your website.

<span style="font-size:20px">Table of Contents</span>

* [Example Usage - Normalize Video Frames](#example-usage---normalize-video-frames)
* [Building your own page](#building-your-own-page)
  * [Include the SDK](#include-the-sdk)
  * [Configure the SDK](#configure-the-sdk)
  * [Interact with the SDK](#interact-with-the-sdk)
* [API Documentation](#api-documentation)
* [System Requirements](#system-requirements)
* [Release Notes](#release-notes)
* [Next Step](#next-steps)

## Example Usage - Normalize Video Frames

Let's start by testing an example of the SDK which demonstrates how to detect quadrilaterals from a video stream and normalize frame with one of those quadrilaterals. 

* Basic Requirements
  * Internet connection  
  * [A supported browser](#system-requirements)
  * An accessible Camera

### Check the code

The complete code of normalizing video frames' example is shown below

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <script src="https://cdn.jsdelivr.net/npm/dynamsoft-camera-enhancer@3.0.1/dist/dce.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/dynamsoft-document-normalizer@1.0.0/dist/ddn.js"></script>
</head>

<body>
    <div id="div-ui-container" style="width:100%;height:100%;">
        <div class="dce-video-container" style="position:relative;width:100%;height:500px;"></div>
    </div>
    <button class="edit-quad">select and edit one quad</button> <!-- The button for pausing the video and selecting, editing a quad. -->
    <button class="normalize-with-the-quad">normalize with the selected quad</button> <!-- The button for normalizing with the confirmed quad. -->
    <div class="normalized-result-canvas"></div> <!-- The container for holding the normalized image result. -->

    <script>
      // The following line specifies a license good for 24 hours, you can visit https://www.dynamsoft.com/customer/license/trialLicense?utm_source=guide&product=dlr&package=js to get your own trial license good for 30 days.
        Dynamsoft.DDN.DocumentNormalizer.license = 'DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9';

        // The following code initializes and uses the SDK.
        (async () => {
            let cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
            await cameraEnhancer.open();
            document.getElementById("div-ui-container").appendChild(cameraEnhancer.getUIElement());

            let normalizer = await Dynamsoft.DDN.DocumentNormalizer.createInstance();
            let options = {
                resultsHighlightBaseShapes: Dynamsoft.DCE.DrawingItem
            };
            normalizer.onQuadDetected = async (results, sourceImage) => {
                for (let result of results) {
                  console.log("detected quad: ", result);
                }
            };
            await normalizer.setImageSource(cameraEnhancer, options);
            normalizer.startScanning(true);
        })();

        document.querySelector('.edit-quad').addEventListener('click', () => {
            if (!cameraEnhancer) return;
            normalizer.confirmQuadForNormalization();
        })

        document.querySelector('.normalize-with-the-quad').addEventListener('click', async () => {
            if (!cameraEnhancer) return;
            let res = await normalizer.normalizeWithConfirmedQuad();
            console.log("normalized image result: ", res);
            if (res) {
                document.querySelector('.normalized-result-canvas').appendChild(res.image.toCanvas());
            }
        })
    </script>
</body>

</html>
```

<p align="center" style="text-align:center; white-space: normal; ">
  <a target="_blank" href="https://jsfiddle.net/DynamsoftTeam/kc35htxd/" title="Run via JSFiddle">
    <img src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/jsfiddle.svg" alt="Run via JSFiddle" width="20" height="20" style="width:20px;height:20px;">
  </a>
</p>

-----

#### About the code

* `DocumentNormalizer.createInstance()`: this method creates a `DocumentNormalizer` object called `normalizer`.

* `CameraEnhancer.createInstance()`: this method creates a `CameraEnhancer` object called `cameraEnhancer`, which is used to control the camera as well as the default user interface. Once `CameraEnhancer` is bound to `normalizer` via `setImageSource()`, it can send video frames from the camera to `normalizer` for detection and normalization in the video feed.

* `onQuadDetected`: this event is triggered every time the SDK finishes detecting a new quadrilateral. The `results` object contains all the quadrilaterals that the SDK has found on this frame. In this example, we print the results to the browser console.

* `startScanning(true)`: starts continuous video frame scanning. The return value is a `Promise` which resovles when the camera is opened, the video shows up on the page and the scanning begins (which means `cameraEnhancer` has started feeding `normalizer` with frames to process).

* `confirmQuadForNormalization()`: pauses the video stream and enter "editor mode" where the quads in current frame are selectable and editable. Then you can select the quad that contains the content you want and edit it to a desirable shape to be normalized.

* `normalizeWithConfirmedQuad()`: normalizes the image whith one confirmed quadrilateral. This method requires that the user selects only one quad out of many or there is only one quad. Only return one normalized image.

### Test the code

Create a text file with the name "Normalize-Video-Frames.html", fill it with the code above and save. After that, open the example page in a browser, allow the page to access your camera and the video will show up on the page. After that, you can point the camera at something with a quadrilateral border to detect it.

> You can also just test it at [https://jsfiddle.net/DynamsoftTeam/kc35htxd/](https://jsfiddle.net/DynamsoftTeam/kc35htxd/)

Remember to open the browser console to check the resulting text.

*Note*:

* Although the page should work properly when opened directly as a file ("file:///"), it's recommended that you deploy it to a web server before accessing it. Also, most browsers require a secure connection (HTTPS) to access the cameras, so deploying the page to a HTTPS website is the best choice.
* On first use, you need to wait a few seconds for the SDK to initialize and download the necessary model file.
* The license "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9" used in this sample is an online license and requires network connection to work.

If the test doesn't go as expected, you can [contact us](https://www.dynamsoft.com/company/contact/?utm_source=guide).

<!-- ### Check out the official sample for MRZ reading

You can also try the official sample for MRZ reading ([test in Github](https://dynamsoft.github.io/document-normalizer-javascript-samples/use-case/mrz-read-and-parse/) or [check the code](https://github.com/Dynamsoft/document-normalizer-javascript-samples/tree/main/use-case/mrz-read-and-parse)). This sample also demonstrates how to parse the MRZ text into meaningful fields. -->

## Building your own page

In this section, we'll break down and show all the steps required to build a web page that normalizes quadrilaterals from video stream.

### Include the SDK

#### Use a CDN

The simplest way to include the SDK is to use either the [jsDelivr](https://jsdelivr.com/) or [UNPKG](https://unpkg.com/) CDN. The "hello world" example above uses **jsDelivr**. Since the recognition is mostly on a video input, we should also include the supporting SDK Dynamsoft Camera Enhancer.

* jsDelivr

  ```html
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-document-normalizer@1.0.0/dist/dlr.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-camera-enhancer@3.0.1/dist/dce.js"></script>
  ```

* UNPKG  

  ```html
  <script src="https://unpkg.com/dynamsoft-document-normalizer@1.0.0/dist/dlr.js"></script>
  <script src="https://unpkg.com/dynamsoft-camera-enhancer@3.0.1/dist/dce.js"></script>
  ```

#### Host the SDK yourself

Besides using the CDN, you can also download the SDK and host its files on your own website / server before including it in your application.

To download the SDK:

* yarn

  ```cmd
  yarn add dynamsoft-document-normalizer@1.0.0
  yarn add dynamsoft-camera-enhancer@3.0.1
  ```

* npm

  ```cmd
  npm install dynamsoft-document-normalizer@1.0.0
  npm install dynamsoft-camera-enhancer@3.0.1
  ```

Depending on how you downloaded the SDK and where you put it, you can typically include it like this:

  ```html
  <script src="/ddn-js-1.0.0/dist/ddn.js"></script>
  <script src="/ddn-js-1.0.0/dce/dist/dce.js"></script>
  ```

or

  ```html
  <script src="/node_modules/dynamsoft-document-normalizer/dist/ddn.js"></script>
  <script src="/node_modules/dynamsoft-camera-enhancer/dist/dce.js"></script>
  ```

or

  ```ts
  import { DocumentNormalizer } from 'dynamsoft-document-normalizer';
  import { CameraEnhancer, DrawingItem } from 'dynamsoft-camera-enhancer';
  ```

### Configure the SDK

Before using the SDK, you need to configure a few things.

#### Specify the license

The SDK requires a license to work, use the API `license` to specify a license key.

```javascript
Dynamsoft.DDN.DocumentNormalizer.license = "YOUR-LICENSE-KEY";
```

To test the SDK, you can request a 30-day trial license via the [customer portal](https://www.dynamsoft.com/customer/license/trialLicense?utm_source=guide&product=ddn&package=js).

#### Specify the location of the "engine" files

If the engine files (\*.worker.js, \*.wasm.js and \*.wasm, etc.) are not in the same location with the main SDK file (dlr.js), you can use the API `engineResourcePath` to specify the engine path, for example:

```javascript
// The following code uses the jsDelivr CDN, feel free to change it to your own location of these files.
Dynamsoft.DDN.DocumentNormalizer.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-document-normalizer@1.0.0/dist/";
Dynamsoft.DCE.CameraEnhancer.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-camera-enhancer@3.0.1/dist/";
```

### Interact with the SDK

#### Create a `DocumentNormalizer` object

To use the SDK, we first create a `DocumentNormalizer` object.

```javascript
let normalizer = null;
try {
    normalizer = await Dynamsoft.DDN.DocumentNormalizer.createInstance();
} catch (ex) {
    console.error(ex);
}
```

#### Create a `CameraEnhancer` object and bind it to the `DocumentNormalizer` object

A `CameraEnhancer` object is required for video processing.

```javascript
let cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
let options = {
    resultsHighlightBaseShapes: Dynamsoft.DCE.DrawingItem
};
await normalizer.setImageSource(cameraEnhancer, options);
```

#### Change the camera settings if necessary

In some cases, a different camera might be required instead of the default one. Also, a different resolution might work better. To change the camera or the resolution, we use the `CameraEnhancer` object. Learn more [here](https://www.dynamsoft.com/camera-enhancer/docs/programming/javascript/api-reference/camera-control.html?ver=3.0.1&utm_source=guide&product=dlr&package=js).

```javascript
// The following lines set which camera and what resolution to use.
let allCameras = await cameraEnhancer.getAllCameras();
await cameraEnhancer.selectCamera(allCameras[0]);
await cameraEnhancer.setResolution(1280, 720);
```

#### Set up the detection process

Check out the following code:

```javascript
// Sets up the scanner behavior
let scanSettings = await normalizer.getScanSettings();
// Sets a scan interval in milliseconds so the SDK may release the CPU from time to time.
// (setting this value larger is a simple way to save battery power and reduce device heating).
scanSettings.intervalTime = 100; // The default is 0.
await normalizer.updateScanSettings(scanSettings);

let runtimeSettings = await normalizer.getRuntimeSettings();
await normalizer.setRuntimeSettings('lowcontrast');
await normalizer.resetRuntimeSettings('default');
```

As you can see from the above code snippets, there are two types of configurations:

* `get/updateScanSettings`: Configures the behavior of the normalizer which includes `duplicateForgetTime` and `intervalTime`, etc.

* `get/set/resetRuntimeSettings`: Configures the normalizer engine with a built-in template or a template represented by a JSON string. This will override the previous RuntimeSettings. 

#### Customize the UI

The built-in UI of the `DocumentNormalizer` object is defined in the file `dist/dlr.ui.html` . There are a 4 ways to customize it:

1. Modify the file `ddn.ui.html` directly.

  This option is only possible when you host this file on your own web server instead of using a CDN. Note that this file is put in the **dist** directory of the **dynamsoft-camera-enhancer** package.

2. Copy the file `ddn.ui.html` to your application, modify it and pass its URL to the API `setUIElement` to set it as the default UI.

  ```javascript
  await cameraEnhancer.setUIElement("THE-URL-TO-THE-FILE");
  ```

3. Append the default UI element to your page, customize it before showing it.

  ```html
  <div id="camera-container"></div>
  ```

  ```javascript
  await cameraEnhancer.open();
  document.getElementById('camera-container').appendChild(cameraEnhancer.getUIElement());
  document.getElementsByClassName('dce-btn-close')[0].hidden = true; // Hide the close button
  ```

4. Build the UI element into your own web page and specify it with the API `setUIElement(HTMLElement)`.

  * Embed the video

    ```html
    <div id="div-ui-container" style="width:100%;height:100%;">
        <div class="dce-video-container" style="position:relative;width:100%;height:500px;"></div>
    </div>
    <script>
        (async () => {
            let cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance();
            await cameraEnhancer.setUIElement(document.getElementById('div-ui-container'));
            let normalizer = await Dynamsoft.DDN.DocumentNormalizer.createInstance();
            let options = {
                resultsHighlightBaseShapes: Dynamsoft.DCE.DrawingItem
            };
            await normalizer.setImageSource(cameraEnhancer, options);
            await normalizer.startScanning(true);
        })();
    </script>
    ```

    > The video element will be created and appended to the DIV element with the class `dce-video-container` , make sure the class name is the correct. Also note that the CSS property `position` of the DIV element must be either `relative` , `absolute` , `fixed` , or `sticky` .

  * Add the camera list and resolution list

    If the class names for these lists match the default ones, `dce-sel-camera` and `dce-sel-resolution` , the SDK will automatically populate the lists and handle the camera/resolution switching.

    ```html
    <div id="div-ui-container">
        <select class="dce-sel-camera"></select>
        <select class="dce-sel-resolution"></select>
        <br>
        <div class="dce-video-container" style="position:relative;width:100%;height:500px;"></div>
    </div>
    ```

    > By default, only 3 hard-coded resolutions (3840 x 2160, 1920 x 1080, 1280 x 720), are populated as options. You can show a customized set of options by hardcoding them.

    ```html
    <select class="dce-sel-resolution">
        <option class="dce-opt-gotResolution" value="got"></option>
        <option data-width="1280" data-height="720">1280x720</option>
        <option data-width="1920" data-height="1080">1920x1080</option>
    </select>
    ```

    > Generally, you need to provide a resolution that the camera supports. However, in case a camera does not support the specified resolution, it usually uses the cloest supported resolution. As a result, the selected resolution may not be the actual resolution. In this case, add an option with the class name `dce-opt-gotResolution` (as shown above) and the SDK will then use it to show the **actual resolution**.

#### Starts the detection and normalization

The last step is to attach event handlers to the events `onQuadDetected` before calling `startScanning(true)` to starts the detection process. And attach click event listener to two buttons, one for selecting a quad, another for normalizing the quad.

```javascript
normalizer.onQuadDetected = async (results, sourceImage) => {
  for (let result of results) {
      console.log("detected quad: ", result);
  }
};
await recognizer.startScanning(true);

// Once this button been clicked, the video will be paused and the quad(s) drawn on the current frame can be selected and edited.
document.querySelector('.edit-quad').addEventListener('click', () => {
  if (!enhancer) return;
  normalizer.confirmQuadForNormalization();
})

// Once this button been clicked, the selected quad from the current frame will be normalized and shown in the div named after normalized-result-canvas.
document.querySelector('.normalize-with-the-quad').addEventListener('click', async () => {
  if (!enhancer) return;
  let res = await normalizer.normalizeWithConfirmedQuad();
  console.log("normalized image result: ", res);
  if (res) {
      document.querySelector('.normalized-result-canvas').appendChild(res.image.toCanvas());
  }
})
```

## API Documentation

You can check out the detailed documentation about the APIs of the SDK at
[https://www.dynamsoft.com/document-normalizer/docs/programming/javascript/api-reference/?ver=latest](https://www.dynamsoft.com/document-normalizer/docs/programming/javascript/api-reference/?ver=latest).

## System Requirements

DLR requires the following features to work:

* Secure context (HTTPS deployment)

  When deploying your application / website for production, make sure to serve it via a secure HTTPS connection. This is required for two reasons
  
  * Access to the camera video stream is only granted in a security context. Most browsers impose this restriction.
  > Some browsers like Chrome may grant the access for `http://127.0.0.1` and `http://localhost` or even for pages opened directly from the local disk (`file:///...`). This can be helpful for temporary development and test.
  
  * Dynamsoft License requires a secure context to work.

* `WebAssembly`, `Blob`, `URL`/`createObjectURL`, `Web Workers`

  The above four features are required for the SDK to work.

* `MediaDevices`/`getUserMedia`

  This API is only required for in-browser video streaming.

* `getSettings`

  This API inspects the video input which is a `MediaStreamTrack` object about its constrainable properties.

The following table is a list of supported browsers based on the above requirements:

  Browser Name | Version
  :-: | :-:
  Chrome | v61+<sup>1</sup>
  Firefox | v52+ (v55+ on Android/iOS<sup>1</sup>)
  Edge<sup>2</sup> | v16+
  Safari<sup>3</sup> | v11+

  <sup>1</sup> iOS 14.3+ is required for camera video streaming in Chrome and Firefox or Apps using webviews.

  <sup>2</sup> On Edge, due to strict Same-origin policy, you must host the SDK files on the same domain as your web page.
  
  <sup>3</sup> Safari v11.x already has the required features, but it has many other issues, so we recommend v12+.

Apart from the browsers, the operating systems may impose some limitations of their own that could restrict the use of the SDK. Browser compatibility ultimately depends on whether the browser on that particular operating system supports the features listed above.

## Release Notes

Learn about what are included in each release at [https://www.dynamsoft.com/document-normalizer/docs/programming/javascript/release-notes/?ver=latest](https://www.dynamsoft.com/document-normalizer/docs/programming/javascript/release-notes/?ver=latest).

## Next Steps

Now that you have got the SDK integrated, you can choose to move forward in the following directions

1. Check out the [official samples](https://github.com/Dynamsoft/document-normalizer-javascript-samples).
2. Learn about the available [APIs](https://www.dynamsoft.com/document-normalizer/docs/programming/javascript/api-reference/?ver=latest).