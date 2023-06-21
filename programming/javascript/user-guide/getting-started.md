---
layout: default-layout
title: User Guide for JavaScript Language
keywords: user guide, hello world
description: Dynamsoft Document Normalizer - User Guide for JavaScript Language
---

# Document Normalizer in JavaScript - User Guide

In this guide, you will learn step by step on how to build a document normalization application with Dynamsoft Document Normalizer SDK using JavaScript language.

> Read more on [Dynamsoft Document Normalizer Features](https://www.dynamsoft.com/document-normalizer/docs/core/introduction/index.html)

- [Document Normalizer in JavaScript - User Guide](#document-normalizer-in-c---user-guide)
  - [Installation](#installation)
  - [Build Your First Application](#build-your-first-application)
    - [Create a New Project](#create-a-new-project)
    - [Include the Library](#include-the-library)
    - [Initialize a Capture Vision Router Instance](#initialize-a-capture-vision-router-instance)
    - [Detect and Save the Normalized Document](#detect-and-save-the-normalized-document)
    - [Build and Run the Project](#build-and-run-the-project)
  - [Process Multiple Images](#process-multiple-images)
    - [Preparation Steps](#preparation-steps)
    - [Add an Image Source as the Input](#add-an-image-source-as-the-input)
    - [Add a Result Receiver as the Output](#add-a-result-receiver-as-the-output)
    - [Start the Process](#start-the-process)
    - [Release Allocated Memory](#release-allocated-memory)
    - [Build and Run the Project Again](#build-and-run-the-project-again)

## Installation

If you haven't downloaded the SDK yet, <a href="https://download2.dynamsoft.com/ddn/dynamsoft-document-normalizer-cpp-2.0.0.zip">download the `JavaScript Package`</a> now and unpack the package into a directory of your choice.

> For this tutorial, we unpack it to a pseudo directory `[INSTALLATION FOLDER]`, change it to your unpacking path for the following content.

> To find out whether your environment is supported, read the [System Requirements](https://www.dynamsoft.com/document-normalizer/docs/server/programming/javascript/#system-requirements).

## Build Your First Application

Let's start by creating a console application which demonstrates how to use the minimum code to detect and normalize a document from an picture of it.

> You can <a href="https://github.com/Dynamsoft/document-normalizer-c-cpp-samples/tree/main/Samples/HelloWorld/NormalizeAnImage" target="_blank">download the entire source code from here</a>.

### Create a New Project

- For Windows

1. Open Visual Studio. Go to "File > New > Project..." or click "Create a new project" on the starting page, choose "Console App", create a new Empty Project and set the Project name as `NormalizeAnImage`.

2. Add a new source file named `NormalizeAnImage.cpp` into the project.

- For Linux

1. Create a new source file named `NormalizeAnImage.cpp` and place it into the folder `[INSTALLATION FOLDER]/Resources/DocumentNormalizer/Samples/HelloWorld/NormalizeAnImage`.

### Include the Library

1. Add headers and libs in `NormalizeAnImage.cpp`.

    ```cpp
    #include <iostream>
    #include <string>
    #include "[INSTALLATION FOLDER]/Include/DynamsoftCaptureVisionRouter.h"

    using namespace std;
    using namespace dynamsoft::license;
    using namespace dynamsoft::cvr;
    using namespace dynamsoft::ddn;

    #if defined(_WIN64) || defined(_WIN32)
        #ifdef _WIN64
            #pragma comment(lib, "[INSTALLATION FOLDER]/Lib/Windows/x64/DynamsoftCaptureVisionRouterx64.lib")
            #pragma comment(lib, "[INSTALLATION FOLDER]/Lib/Windows/x64/DynamsoftCorex64.lib")
            #pragma comment(lib, "[INSTALLATION FOLDER]/Lib/Windows/x64/DynamsoftLicensex64.lib")
            #pragma comment(lib, "[INSTALLATION FOLDER]/Lib/Windows/x64/DynamsoftUtilityx64.lib")
        #else
            #pragma comment(lib, "[INSTALLATION FOLDER]/Lib/Windows/x86/DynamsoftCaptureVisionRouterx86.lib")
            #pragma comment(lib, "[INSTALLATION FOLDER]/Lib/Windows/x86/DynamsoftCorex86.lib")
            #pragma comment(lib, "[INSTALLATION FOLDER]/Lib/Windows/x86/DynamsoftLicensex86.lib")
            #pragma comment(lib, "[INSTALLATION FOLDER]/Lib/Windows/x86/DynamsoftUtilityx86.lib")
        #endif
    #endif
    ```

### Initialize a Capture Vision Router Instance

1. Initialize the license key.

    ```cpp
    char errorMsg[256] = {0};
    CLicenseManager::InitLicense("DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9", errorMsg, 256);
    ```

    > The string "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9" here is a free public trial license. Note that network connection is required for this license to work. When it expires, you can request a 30-day free trial license from the <a href="https://www.dynamsoft.com/customer/license/trialLicense?utm_source=guide&product=ddn&package=desktop" target="_blank">Customer Portal</a>.

2. Create an instance of Capture Vision Router.

    ```cpp
    CCaptureVisionRouter *router = new CCaptureVisionRouter;
    ```

### Detect and Save the Normalized Document

1. Apply normalization for an image file.

    ```cpp
    CCapturedResultArray* results = router->Capture("[INSTALLATION FOLDER]/Resources/DocumentNormalizer/Images/sample-image.png", CPresetTemplate::PT_DETECT_AND_NORMALIZE_DOCUMENT);
    ```

    > Note:
    >
    > Please change all `[INSTALLATION FOLDER]` in above code snippet to your unpacking path.

2. Save the normalized result as an image file.

    ```cpp
    cout << "File: " << imageFile << endl;

    /*
    * results is an Array of CCapturedResult objects, each object is the result of an image.
    */
    for (int arrayIndex = 0; arrayIndex < results->GetCount(); arrayIndex++)
    {
        const CCapturedResult* result = results->GetResult(arrayIndex);

        if (result->GetErrorCode() != 0) {
            cout << "Error: " << result->GetErrorCode() << "," << result->GetErrorString() << endl;
            continue;
        }

        /*
        * There can be multiple types of result items per image.
        * We check each of these items until we find the normalized image.
        */
        int count = result->GetCount();
        cout << "Normalized " << count << " documents" << endl;
        for (int i = 0; i < count; i++) {
            const CCapturedResultItem* item = result->GetItem(i);

            CapturedResultItemType type = item->GetType();
            if (type == CapturedResultItemType::CRIT_NORMALIZED_IMAGE) {
                const CNormalizedImageResultItem* normalizedImage = dynamic_cast<const CNormalizedImageResultItem*>(item);

                string outPath = "normalizedResult_";
                outPath += to_string(i) + ".png";

                CImageManager manager;

                // 4.Save normalized iamge to file.
                errorcode = manager.SaveToFile(normalizedImage->GetImageData(), outPath.c_str());
                if (errorcode == 0) {
                    cout << "Document " << i << " file: " << outPath << endl;
                }
            }
        }
    } 
    ```

### Build and Run the Project

- For Windows

1. In Visual Studio, set the solution to build as Release\|x64.

2. Build the project to generate program `NormalizeAnImage.exe`.

3. Copy **ALL** `*.dll` files under `[INSTALLATION FOLDER]\Lib\Windows\x64` to the same folder as the `NormalizeAnImage.exe`

4. Run the program `NormalizeAnImage.exe`.

> The SDK supports both x86 and x64, please set the platform based on your needs.

- For Linux

1. Open a terminal and change to the target directory where `NormalizeAnImage.cpp` is located. Build the sample:

    ```bash
    g++ -o NormalizeAnImage NormalizeAnImage.cpp -lDynamsoftCore -lDynamsoftLicense -lDynamsoftUtility -lDynamsoftCaptureVisionRouter -L ../../../Lib/Linux/x64 -Wl,-rpath=../../../Lib/Linux/x64 -std=c++11
    ```

2. Run the program `NormalizeAnImage`.

    ```bash
    ./NormalizeAnImage
    ```

## Process Multiple Images

If you need to process multiple images at once instead of one image, you can follow these steps:

### Preparation Steps

1. [Create a new project](#create-a-new-project) named `NormalizeMultipleImages`.
2. [Initialize a Capture Vision Router Instance](#initialize-a-capture-vision-router-instance).
3. [Include the Library](#include-the-library).

>You can download the complete source code from [here](https://github.com/Dynamsoft/document-normalizer-c-cpp-samples/tree/main/samples/HelloWorld/NormalizeMultipleImages).

### Add an Image Source as the Input

The class `CDirectoryFetcher` is capable of converting a local directory to an image source. We will use it to connect multiple images to the image-processing engine.

1. Setting up a directory fetcher to retrieve image data sources from a directory.

    ```cpp
    CDirectoryFetcher *dirFetcher = new CDirectoryFetcher;
    dirFetcher->SetDirectory("[Your Image Path]");

    router->SetInput(dirFetcher);
    ```

2. Create a class `MyImageSourceStateListener` to implement the `CImageSourceStateListenter` interface, and call `StopCapturing` in the callback function.

    ```cpp
    class MyImageSourceStateListener : public CImageSourceStateListener
    {
    private:
        CCaptureVisionRouter* m_router;

    public:
        MyImageSourceStateListener(CCaptureVisionRouter* router) {
            m_router = router;
        }

        virtual void OnImageSourceStateReceived(ImageSourceState state)
        {
            if (state == ISS_EXHAUSTED)
                m_router->StopCapturing();
        }
    };
    ```

3. Register the `MyImageSourceStateListener` object to monitor the status of the image source.

    ```cpp
    CImageSourceStateListener *listener = new MyImageSourceStateListener(router);
    router->AddImageSourceStateListener(listener);
    ```

### Add a Result Receiver as the Output

1. Define the receiver class.

    ```cpp
    class MyResultReceiver : public CCapturedResultReceiver
    {
    public:
        virtual void OnNormalizedImagesReceived(const CNormalizedImagesResult* pResult)
        {
            const CFileImageTag *tag = dynamic_cast<const CFileImageTag*>(pResult->GetSourceImageTag());

            cout << "File: " << tag->GetFilePath() << endl;

            if (pResult->GetErrorCode() != EC_OK)
            {
                cout << "Error: " << pResult->GetErrorString() << endl;
            }
            else
            {
                CImageManager manager;
                int lCount = pResult->GetCount();
                cout << "Normalized " << lCount << " documents" << endl;
                for (int li = 0; li < lCount; ++li)
                {
                    const CNormalizedImageResultItem* item = pResult->GetItem(li);
                    
                    string outPath = "normalizeImage_";
                    outPath += to_string(li) + ".png";

                    manager.SaveToFile(item->GetImageData(), outPath.c_str());

                    cout << "Document " << li << " file: " << outPath << endl;
                }
            }

            cout << endl;
        }
    };
    ```

    >For the error handling mechanism, the SDK returns Error Code in the `CNormalizedImagesResult` object. You can add error handling code as needed. See [Error Code]({{site.dcv_enumerations}}core/error-code.html) for a full list of supported error codes.

2. Create a receiver object and set it as the output.

    ```cpp
    CCapturedResultReceiver *recv = new MyResultReceiver;
    router->AddResultReceiver(recv);
    ```

### Start the Process

1. Call the method `StartCapturing()` to start processing all the images in the specified folder.

    ```cpp
    router->StartCapturing(CPresetTemplate::PT_DETECT_AND_NORMALIZE_DOCUMENT, true);        
    ```

    >During the process, the callback function `OnNormalizedImagesReceived()` is triggered each time an image finishes processing. After all images are processed, the listener function `OnImageSourceStateReceived()` will return the image source state as `ISS_EXHAUSTED` and the process is stopped with the method `StopCapturing()`.

### Release Allocated Memory

```cpp
delete router, router = NULL;
delete dirFetcher, dirFetcher = NULL;
delete listener, listener = NULL;
delete recv, recv = NULL;
```

### Build and Run the Project Again

Please refer to [Build and Run the Project](#build-and-run-the-project).
