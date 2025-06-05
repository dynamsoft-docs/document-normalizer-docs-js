# DCV JS 3.0.4000 Requirements

- [DCV JS 3.0.4000 Requirements](#dcv-js-304000-requirements)
  - [1. Abstract](#1-abstract)
    - [1.1. Task/Section/Stage parameters design](#11-tasksectionstage-parameters-design)
    - [1.2. Support for flexible sequence combinations of sections within tasks](#12-support-for-flexible-sequence-combinations-of-sections-within-tasks)
    - [1.3. Add ROI-level deduplication of results coming from a few tasks](#13-add-roi-level-deduplication-of-results-coming-from-a-few-tasks)
    - [1.4. Add and update sections in the workflow of DDN algorithms(DDN)](#14-add-and-update-sections-in-the-workflow-of-ddn-algorithmsddn)
    - [1.5. Add EAN13 deblur algorithm based on super-resolution reconstruction models(DBR)](#15-add-ean13-deblur-algorithm-based-on-super-resolution-reconstruction-modelsdbr)
    - [1.6. Introduce text-line recognition algorithm based on Convolutional Recurrent Neural Networks(DLR)](#16-introduce-text-line-recognition-algorithm-based-on-convolutional-recurrent-neural-networksdlr)
  - [2. Parameters Design](#2-parameters-design)
    - [2.0. Overall parameters organization](#20-overall-parameters-organization)
  - [3. SDK Modules](#3-sdk-modules)
    - [3.1. Core](#31-core)
      - [3.1.1. Update enum CapturedResultItemType](#311-update-enum-capturedresultitemtype)
      - [3.1.2. Update enum IntermediateResultUnitType](#312-update-enum-intermediateresultunittype)
      - [3.1.3. Update enum RegionObjectElementType](#313-update-enum-regionobjectelementtype)
      - [3.1.4. Update enum SectionType](#314-update-enum-sectiontype)
      - [3.1.6. Update enum TransformMatrixType](#316-update-enum-transformmatrixtype)
      - [3.1.7. Update interface RegionObjectElement](#317-update-interface-regionobjectelement)
      - [3.1.8. Update interface PredetectedRegionElement](#318-update-interface-predetectedregionelement)
      - [3.1.9. Rename ScaledDownColourImageUnit to ScaledColourImageUnit](#319-rename-scaleddowncolourimageunit-to-scaledcolourimageunit)
      - [3.1.10. Update enum ErrorCode](#3110-update-enum-errorcode)
      - [3.1.11 Add enum EnumImageFileFormat](#3111-add-enum-enumimagefileformat)
      - [3.1.12. update interface Quadrilateral](#3112-update-interface-quadrilateral)
      - [3.1.15. Add interface CCapturedResultBase](#3115-add-interface-ccapturedresultbase)
      - [3.1.17. Add GEM\_END for EnumGrayscaleEnhancementMode](#3117-add-gem_end-for-enumgrayscaleenhancementmode)
      - [3.1.18. Add GTM\_END for EnumGrayscaleTransformationMode](#3118-add-gtm_end-for-enumgrayscaletransformationmode)
      - [3.1.19. Add EnumModuleName](#3119-add-enummodulename)
      - [3.1.20. Update loadWasm method](#3120-update-loadwasm-method)
      - [3.1.21. Update engineResourcePaths in CoreModule](#3121-update-engineresourcepaths-in-coremodule)
      - [3.1.22. Update isMeasuredInPercentage property optional](#3122-update-ismeasuredinpercentage-property-optional)
    - [3.2. DDN](#32-ddn)
      - [3.2.1. Rename interface NormalizedImageResultItem to DeskewedImageResultItem](#321-rename-interface-normalizedimageresultitem-to-deskewedimageresultitem)
      - [3.2.3. Add interface EnhancedImageResultItem](#323-add-interface-enhancedimageresultitem)
      - [3.2.5. Rename interface NormalizedImageElement to DeskewedImageElement](#325-rename-interface-normalizedimageelement-to-deskewedimageelement)
      - [3.2.6. Rename interface NormalizedImagesUnit to DeskewedImageUnit](#326-rename-interface-normalizedimagesunit-to-deskewedimageunit)
      - [3.2.7. Add interface EnhancedImageElement](#327-add-interface-enhancedimageelement)
      - [3.2.8. Add interface EnhancedImageUnit](#328-add-interface-enhancedimageunit)
      - [3.2.14 Add interface ProcessedDocumentResult](#3214-add-interface-processeddocumentresult)
      - [3.2.15. Remove interface DetectedQuadsResult \& NormalizedImagesResult](#3215-remove-interface-detectedquadsresult--normalizedimagesresult)
      - [3.2.16. Remove saveToFile in interface deskewedImageResultItem](#3216-remove-savetofile-in-interface-deskewedimageresultitem)
      - [3.2.17. Add property sourceLocation in DeskewedImageResultItem/DeskewedImageElement](#3217-add-property-sourcelocation-in-deskewedimageresultitemdeskewedimageelement)
    - [3.3. CVR](#33-cvr)
      - [3.3.1. Update class IntermediateResultReceiver](#331-update-class-intermediateresultreceiver)
      - [3.3.3. Update class CapturedResultReceiver](#333-update-class-capturedresultreceiver)
      - [3.3.6 Update CapturedResult to extend CapturedResultBase](#336-update-capturedresult-to-extend-capturedresultbase)
      - [3.3.7 支持StartCapturing过程中修改参数](#337-支持startcapturing过程中修改参数)
      - [3.3.8 加载模型的接口](#338-加载模型的接口)
      - [3.3.11 Update SimplifiedCaptureVisionSettings](#3311-update-simplifiedcapturevisionsettings)
      - [3.3.12 Update OutputSettings and OutputSettingsToFile API](#3312-update-outputsettings-and-outputsettingstofile-api)
      - [3.3.13 Add call back function for CaptureVisionRouter](#3313-add-call-back-function-for-capturevisionrouter)
    - [3.4. DBR](#34-dbr)
      - [3.4.1. Rename ScaledUpBarcodeImageUnit to ScaledBarcodeImageUnit](#341-rename-scaledupbarcodeimageunit-to-scaledbarcodeimageunit)
      - [3.4.2 识别流程调整，引入神经网络模型的处理](#342-识别流程调整引入神经网络模型的处理)
      - [3.4.7 Add support for new barcode types](#347-add-support-for-new-barcode-types)
      - [3.4.8 修复DPM模式下结果中的isMirrored未正确赋值的bug](#348-修复dpm模式下结果中的ismirrored未正确赋值的bug)
      - [3.4.9 Update DecodedBarcodesResult to extend CapturedResultBase](#349-update-decodedbarcodesresult-to-extend-capturedresultbase)
      - [3.4.10 修复文字行检测中的一个崩溃](#3410-修复文字行检测中的一个崩溃)
      - [3.4.11 修复Template目录不存在时Linux/Mac下命令行会输出opendir: No such file or directory的bug](#3411-修复template目录不存在时linuxmac下命令行会输出opendir-no-such-file-or-directory的bug)
      - [3.4.13 add LM\_END for EnumLocalizationMode](#3413-add-lm_end-for-enumlocalizationmode)
      - [3.4.14 add DM\_END for EnumDeblurMode](#3414-add-dm_end-for-enumdeblurmode)
      - [3.4.15 统一FormatString的格式](#3415-统一formatstring的格式)
      - [3.4.16 更新DeblurMode的默认值以移除DM\_MORPHING](#3416-更新deblurmode的默认值以移除dm_morphing)
      - [3.4.17 修复非标准的code 128不能解码的bug（来自U11566）](#3417-修复非标准的code-128不能解码的bug来自u11566)
      - [3.4.18 A bug fix](#3418-a-bug-fix)
      - [3.4.19 Add property codewords in PDF417 details](#3419-add-property-codewords-in-pdf417-details)
    - [3.5. DLR](#35-dlr)
      - [3.5.1 识别流程调整，整合文本行模型识别](#351-识别流程调整整合文本行模型识别)
      - [3.5.2 参数模板读取解析的调整](#352-参数模板读取解析的调整)
      - [3.5.3 对于模板中不认识的Key按warning处理](#353-对于模板中不认识的key按warning处理)
      - [3.5.4 新增OverlappingCharacters资源加载API（内部接口）](#354-新增overlappingcharacters资源加载api内部接口)
      - [3.5.5. Update interface RecognizedTextLinesResult to extend CapturedResultBase](#355-update-interface-recognizedtextlinesresult-to-extend-capturedresultbase)
      - [3.5.7. Update default value of SimplifiedLabelRecognizerSettings.characterModelName](#357-update-default-value-of-simplifiedlabelrecognizersettingscharactermodelname)
      - [3.5.8. Add APIs for loading non-model data files](#358-add-apis-for-loading-non-model-data-files)
    - [3.6. DCP \& DCPD](#36-dcp--dcpd)
      - [3.6.1 对于模板中不认识的Key按warning处理](#361-对于模板中不认识的key按warning处理)
      - [3.6.3 增加对 GS1 Application Identifier (AI)的支持](#363-增加对-gs1-application-identifier-ai的支持)
      - [3.6.4 DCP \& DCPD的版本号统一为 3.0.10](#364-dcp--dcpd的版本号统一为-3010)
      - [3.6.5 Update ParsedResult to extend CapturedResultBase](#365-update-parsedresult-to-extend-capturedresultbase)
    - [3.7. DIP](#37-dip)
      - [3.7.1 对于模板中不认识的Key按warning处理](#371-对于模板中不认识的key按warning处理)
    - [3.8. DNN](#38-dnn)
    - [3.9. License](#39-license)
      - [3.9.1 计费逻辑添加或调整](#391-计费逻辑添加或调整)
      - [3.9.2 修改license缓存计算哈希值方式](#392-修改license缓存计算哈希值方式)
      - [3.9.3 dls2 license string 支持附加 `?ext=XXX` 字段以更新缓存](#393-dls2-license-string-支持附加-extxxx-字段以更新缓存)
    - [3.10. Utility](#310-utility)
      - [3.10.1. Update class MultiFrameResultCrossFilter](#3101-update-class-multiframeresultcrossfilter)
      - [3.10.2. Update class ImageManager](#3102-update-class-imagemanager)
    - [3.11. dcvDATA](#311-dcvdata)
      - [3.11.1. Package structure](#3111-package-structure)
      - [3.11.2. Add readme in TFS for a new npm pkg release](#3112-add-readme-in-tfs-for-a-new-npm-pkg-release)
  - [4. Install Package](#4-install-package)
    - [4.1 wasm名改为全称,和包名一致](#41-wasm名改为全称和包名一致)
    - [4.4. 预置模板调整](#44-预置模板调整)
    - [4.5. 更新Legal.txt](#45-更新legaltxt)
  - [5. Samples](#5-samples)
    - [Update MRZScanner samples](#update-mrzscanner-samples)
  - [6. Docs](#6-docs)
  - [7. Website](#7-website)
  - [8. Discussion](#8-discussion)

## 1. Abstract

### 1.1. Task/Section/Stage parameters design

- Reorganize some parameters in DocumentNormalizerTaskSetting/LabelRecognizerTaskSetting/BarcodeReaderTaskSetting, Split them up into Task/Section/Stage levels.
- Move some parameters of ImageParameter to be configured under stages of DocumentNormalizerTaskSetting/LabelRecognizerTaskSetting/BarcodeReaderTaskSetting
- Add "SkipStages" parameter for all sections

### 1.2. Support for flexible sequence combinations of sections within tasks

### 1.3. Add ROI-level deduplication of results coming from a few tasks

### 1.4. Add and update sections in the workflow of DDN algorithms(DDN)

- Add new section type "ST_IMAGE_ENHANCING"
- Rename "ST_DOCUMENT_NORMALIZATION" to "ST_DOCUMENT_DESKEWING"

### 1.5. Add EAN13 deblur algorithm based on super-resolution reconstruction models(DBR)

### 1.6. Introduce text-line recognition algorithm based on Convolutional Recurrent Neural Networks(DLR)

1）新增DLR CRNN模型用于文本行识别
2）原有字符模型从Caffe模型切换为Onnx格式，并采用.data打包格式
3）新增TextLineRecModel Object
4）TextLineSpecification Object新增TextLineRecModelName参数
5）LabelRecognizerTaskSetting Object新增OverlappingCharactersPath参数
6）DNN模块基于onnxruntime build，替换原有opencv dnn
7）整合文本行模型和单字符模型的识别流程

## 2. Parameters Design

### 2.0. Overall parameters organization

[DCV 3.x Parameters organization](https://dynamsoft.sharepoint.com/sites/DynamsoftEnglishOnly/Shared%20Documents/Product-Team/Requirements/dcv/parameter-design/dcv3-parameters.xlsx?d=w46ffd1f01cad492cb7c61dc70c234d55&csf=1&web=1&e=33TzHG)
[DCV 3.x template example](../desktop/assets/dcv3-example.json)

>Note:
>
> - 参数根据作用范围，放置到不同的层次，包含Task/Section/Stage/Image
> - 不同Section中的同名参数支持配置成不同值，从而执行不同的算法：譬ImageParameter等
> - 如果参数的适用于多个Section，但其对于多个Section一定是相同的值，则仍保留在Task层面配置
> - Stage的类型请详细查看Excel

Detailed in [dcv-cpp-3.0.1000](../desktop/dcv-cpp-3.0.1000.md) 


## 3. SDK Modules

| Module  | Version |
|-------- |-------- |
| CVR     | **3.0.40**  |
| Core    | **4.0.40**  |
| License | **4.0.40**  |
| DIP     | **3.0.40**  |
| Utility | **2.0.40**  |
| DBR     | **11.0.40** |
| DDN     | **3.0.40**  |
| DLR     | **4.0.40**  |
| DNN     | 3.0.30      |
| DCP     | 4.0.20      |
| DCE     | 4.2.12      |
| dcvDATA | **1.0.0**   |

### 3.1. Core

#### 3.1.1. Update enum CapturedResultItemType

1) Add new enum values

- CRIT_ENHANCED_IMAGE = 64

2) Rename CRIT_NORMALIZED_IMAGE to CRIT_DESKEWED_IMAGE

```ts
enum EnumCapturedResultItemType {
    /**
     * Represents an original image captured by the system.
     * This type is used to identify the raw, unmodified image data directly obtained from the image source.
     */
    CRIT_ORIGINAL_IMAGE = 1,
    /**
     * Identifies a captured item as a barcode within the image.
     * This type signifies that the item has been recognized as a barcode and contains data extracted from the barcode.
     */
    CRIT_BARCODE = 2,
    /**
     * Identifies a captured item as a line of text within the image.
     * This type signifies that the item has been recognized as a line of text and contains the textual content.
     */
    CRIT_TEXT_LINE = 4,
    /**
     * Identifies a captured item as a quadrilateral detected within the image.
     * This type is typically used for geometric shapes or areas of interest that have been identified, often in the context of document scanning.
     */
    CRIT_DETECTED_QUAD = 8,
    /**
     * Represents an image that has been processed and deskewed based on the original image.
     * Deskewing may include adjustments such as perspective correction, etc. to standardize the image presentation.
     */
    CRIT_DESKEWED_IMAGE = 16,
    /**
     * Indicates a parsed result item.
     * This type is used for items that have undergone further interpretation by Dynamsoft Code Parser, transforming raw data into a structured format.
     */
    CRIT_PARSE_RESULT = 32,
    /**
     * Indicates a enhanced image item.
     * This type is used for items that have undergone post-processing, such as adjustments to brightness, contrast, color mode, etc.
     */
    CRIT_ENHANCED_IMAGE = 64,
}
```

#### 3.1.2. Update enum IntermediateResultUnitType

1) Rename enum values:

   - rename IRUT_NORMALIZED_IMAGES to IRUT_DESKEWED_IMAGE
   - rename IRUT_SCALED_DOWN_COLOUR_IMAGE to IRUT_SCALED_COLOUR_IMAGE
   - rename IRUT_SCALED_UP_BARCODE_IMAGE to IRUT_SCALED_BARCODE_IMAGE

2) Add new enum values:

   - IRUT_ENHANCED_IMAGE = 1LL << 30

#### 3.1.3. Update enum RegionObjectElementType

1) Rename ROET_NORMALIZED_IMAGE to ROET_DESKEWED_IMAGE
2) add ROET_ENHANCED_IMAGE

#### 3.1.4. Update enum SectionType

1) Add new enum values:
   - ST_IMAGE_ENHANCEMENT
  
2) Rename ST_DOCUMENT_NORMALIZATION to ST_DOCUMENT_DESKEWING

```ts
enum EnumSectionType
{
    /** Indicates that no specific section type has been specified. */
    ST_NULL = 0,
    /** Corresponds to results generated in the "region prediction" section. */
    ST_REGION_PREDETECTION = 1,
    /** Corresponds to results generated in the "barcode localization" section. */
    ST_BARCODE_LOCALIZATION = 2,
    /** Corresponds to results generated in the "barcode decoding" section. */
    ST_BARCODE_DECODING = 3,
    /** Corresponds to results generated in the "text line localization" section. */
    ST_TEXT_LINE_LOCALIZATION = 4,
    /** Corresponds to results generated in the "text line recognition" section. */
    ST_TEXT_LINE_RECOGNITION = 5,
    /** Corresponds to results generated in the "document detection" section. */
    ST_DOCUMENT_DETECTION = 6,
    /** Corresponds to results generated in the "document deskewing" section. */
    ST_DOCUMENT_DESKEWING = 7,
    /** Corresponds to results generated in the "document enhancement" section. */
    ST_IMAGE_ENHANCEMENT = 8
}
```

#### 3.1.6. Update enum TransformMatrixType

1) Add enum values:
   - TMT_LOCAL_TO_SECTION_IMAGE
   - TMT_SECTION_TO_LOCAL_IMAGE

```ts
enum EnumTransformMatrixType {
    /**Represents a transformation matrix that converts coordinates from the local image to thsection image.*/
    TMT_LOCAL_TO_SECTION_IMAGE = 2,
    /**Represents a transformation matrix that converts coordinates from the section image tthe local image.*/
    TMT_SECTION_TO_LOCAL_IMAGE = 3
}
```

#### 3.1.7. Update interface RegionObjectElement

1) add imageData property

```ts
interface RegionObjectElement {
    /**The image data for the `RegionObjectElement`. */
    imageData: DSImageData;
}
```
  
#### 3.1.8. Update interface PredetectedRegionElement

1）add property labelId & labelName

```ts
interface PredetectedRegionElement extends RegionObjectElement {
            /** The label id of the predetected region element. */
            labelID: number;
            /** The label name of the predetected region element. */
            labelName: string;
        }
```

补充说明：
1）非模型的预检测的Region，默认LabelId为-1，LabelName为""
2）模型检测的Region，则按照模型的检测结果进行输出

#### 3.1.9. Rename ScaledDownColourImageUnit to ScaledColourImageUnit

#### 3.1.10. Update enum ErrorCode

1) add error code：

    - EC_UNSUPPORTED_JSON_KEY_WARNING
    - EC_MODEL_FILE_NOT_FOUND
    - EC_PDF_LICENSE_NOT_FOUND
    - EC_RECT_INVALID

    ```ts
    enum EnumErrorCode {
      /**One or more unsupported JSON keys were encountered and ignored from the template.*/
      EC_UNSUPPORTED_JSON_KEY_WARNING = -10077,
      /**Model file is not found*/
      EC_MODEL_FILE_NOT_FOUND = -10078,
      /**[PDF] No license found.*/
      EC_PDF_LICENSE_NOT_FOUND = -10079,
      /**The rectangle is invalid.*/
      EC_RECT_INVALID = -10080,
    }
    ```

2) 删除以下不再使用的error code:

    - EC_RESERVED_INFO_NOT_MATCH
    - EC_REQUEST_FAILED
    - EC_LICENSE_INIT_FAILED
    - EC_LICENSE_CONTENT_INVALID
    - EC_LICENSE_KEY_INVALID
    - EC_LICENSE_DEVICE_RUNS_OUT
    - EC_QR_LICENSE_INVALID
    - EC_1D_LICENSE_INVALID
    - EC_PDF417_LICENSE_INVALID
    - EC_DATAMATRIX_LICENSE_INVALID
    - EC_AZTEC_LICENSE_INVALID
    - EC_PATCHCODE_LICENSE_INVALID
    - EC_POSTALCODE_LICENSE_INVALID
    - EC_DPM_LICENSE_INVALID
    - EC_MAXICODE_LICENSE_INVALID
    - EC_GS1_DATABAR_LICENSE_INVALID
    - EC_GS1_COMPOSITE_LICENSE_INVALID
    - EC_DOTCODE_LICENSE_INVALID
    - EC_PHARMACODE_LICENSE_INVALID
    - EC_ZA_DL_LICENSE_INVALID
    - EC_AAMVA_DL_ID_LICENSE_INVALID
    - EC_AADHAAR_LICENSE_INVALID
    - EC_MRTD_LICENSE_INVALID
    - EC_VIN_LICENSE_INVALID
    - EC_CUSTOMIZED_CODE_TYPE_LICENSE_INVALID
    - EC_HANDSHAKE_CODE_INVALID
    - EC_LICENSE_CLIENT_DLL_MISSING
    - EC_LICENSE_INIT_SEQUENCE_FAILED
    - EC_LICENSE_CACHE_USED
    - EC_FAILED_TO_REACH_DLS
    - EC_FRAME_DECODING_THREAD_EXISTS
    - EC_STOP_DECODING_THREAD_FAILED
    - EC_CHARACTER_MODEL_FILE_NOT_FOUND

3) 更新error code对应的message

    //The api does not support multi-page files. Please use CaptureMultiPages instead.
    EC_MULTI_PAGES_NOT_SUPPORTED = -10066

4) add error code

    - EC_LICENSE_AUTH_QUOTA_EXCEEDED
    - EC_LICENSE_RESULTS_LIMIT_EXCEEDED
    - EC_TEMPLATE_VERSION_INCOMPATIBLE

    ```ts
    enum ErrorCode {
        /*The template version is incompatible. Please use a compatible template.*/
        EC_TEMPLATE_VERSION_INCOMPATIBLE = -10081
        /*License authentication failed: quota exceeded.*/
        EC_LICENSE_AUTH_QUOTA_EXCEEDED = -20013,
        /**License restriction: the number of results has exceeded the allowed limit.*/
        EC_LICENSE_RESULTS_LIMIT_EXCEEDED = -20014,
    } ErrorCode;
    ```

#### 3.1.11 Add enum EnumImageFileFormat

```ts
enum EnumImageFileFormat {
    /** JPEG image format. */
    IFF_JPEG = 0,
    /** PNG image format. */
    IFF_PNG = 1,
    /** BMP (Bitmap) image format. */
    IFF_BMP = 2,
    /** PDF (Portable Document Format) format. */
    IFF_PDF = 3
}
```

#### 3.1.12. update interface Quadrilateral

```ts
CRect GetBoundingRect() const;
interface Quadrilateral {
    /** The bounding rectangle of the quadrilateral */
    boundingRect: DSRect;
}
```

#### 3.1.15. Add interface CCapturedResultBase

- 通用类，作为所有最终结果类型的基类

```ts
interface CapturedResultBase{
    /** Error code associated with the capture result. */
    readonly errorCode: number;
    /** Error string providing details about the error. */
    readonly errorString: string;
    /** The hash ID of the original image. */
    readonly originalImageHashId: string;
    /** The tag associated with the original image. */
    readonly originalImageTag: Core.ImageTag;
}
```

#### 3.1.17. Add GEM_END for EnumGrayscaleEnhancementMode

- add GEM_END=0xFFFFFFFF //Placeholder value with no functional meaning

Note:
grayscaleEnhancementModes = {GEM_GRAY_SMOOTH, GEM_SKIP, GEM_END, GEM_END, GEM_END, GEM_END, GEM_END, GEM_END};
等于在模板中的Modes同时配置了GEM_GRAY_SMOOTH和GEM_SKIP。其余添加_END的逻辑相同

#### 3.1.18. Add GTM_END for EnumGrayscaleTransformationMode

- add GTM_END=0xFFFFFFFF //Placeholder value with no functional meaning

#### 3.1.19. Add EnumModuleName
  
```ts
    enum EnumModuleName{
        MN_DYNAMSOFT_CAPTURE_VISION_ROUTER = "cvr",
        MN_DYNAMSOFT_CORE = "core",
        MN_DYNAMSOFT_LICENSE = "license",
        MN_DYNAMSOFT_IMAGE_PROCESSING = "dip",
        MN_DYNAMSOFT_UTILITY = "utility",
        MN_DYNAMSOFT_BARCODE_READER = "dbr",
        MN_DYNAMSOFT_DOCUMENT_NORMALIZER = "ddn",
        MN_DYNAMSOFT_LABEL_RECOGNIZER = "dlr",
        MN_DYNAMSOFT_CAPTURE_VISION_DATA = "dcvData",
        MN_DYNAMSOFT_NEURAL_NETWORK = "dnn",
        MN_DYNAMSOFT_CODE_PARSER = "dcp",
        MN_DYNAMSOFT_CAMERA_ENHANCER = "dce",
        MN_DYNAMSOFT_CAPTURE_VISION_STD = "std"
    }
```

#### 3.1.20. Update loadWasm method

Core中暴露模块名的枚举，可作为loadWasm()的传入参数。同时loadWasm()入参可兼容旧版字符串的写法。不传参数时只加载主模块（std+core），单wasm的情况下无需传参。

```ts
static loadWasm: (names?: Array<string> | string | EnumModuleName | Array<EnumModuleName>) => Promise<void>;
```

- [skip] 新增一个参数，用于配置引擎资源地址，是否允许使用不带版本号的资源地址。现在MRZ solution 自部署时,使用根路径设置的方式会遇到 "Can not find the element with class 'dce-video-container'."报错。

#### 3.1.21. Update engineResourcePaths in CoreModule

- Rename `dlrData` to `dcvData`
- Add `dcvBundle` & `dbrBundle`

```ts
    /** 
    * Specifies the resource path for the dynamsoft-capture-vision-data module.
    */
    "dcvData"?: string;
    /**
     * Specifies the resource path for the dynamsoft-capture-vision-bundle module.
     */
    "dcvBundle"?: string;
    /**
     * Specifies the resource path for the dynamsoft-barcode-reader-bundle module.
     */
    "dbrBundle"?: string;
```

#### 3.1.22. Update isMeasuredInPercentage property optional

```ts
interface DSRect {
    /** Indicates if the rectangle's measurements are in percentages. */
    isMeasuredInPercentage?: boolean;
}
```

### 3.2. DDN

#### 3.2.1. Rename interface NormalizedImageResultItem to DeskewedImageResultItem

```ts
interface DeskewedImageResultItem extends Core.CapturedResultItem{
    // update comments as well
}
```

补充说明：
1）所有输出到CRR中的结果坐标，均采用Original Image Coordinate System
2）CDeskewedImageResultItem和CEnhancedImageResultItem记录了从Original Image Coordinate System到Local Image Coordinate System的转换矩阵；如果用户需要得到在Deskewed Image/Enhanced Image上的坐标，则用结果坐标*转换矩阵即可

#### 3.2.3. Add interface EnhancedImageResultItem

```ts
interface EnhancedImageResultItem extends Core.CapturedResultItem {
    /** The image data for the enhanced image result. */
    imageData: Core.DSImageData;
    /** Converts the enhanced image data into an HTMLCanvasElement for display or further manipulation in web applications. */
    toCanvas: () => HTMLCanvasElement;
    /** Converts the enhanced image data into an HTMLImageElement of a specified MIME type ('image/png' or 'image/jpeg'). */
    toImage: (MIMEType: "image/png" | "image/jpeg") => HTMLImageElement;
    /** Converts the enhanced image data into a Blob object of a specified MIME type ('image/png' or 'image/jpeg'). */
    toBlob: (MIMEType: "image/png" | "image/jpeg") => Promise<Blob>;
}
```

#### 3.2.5. Rename interface NormalizedImageElement to DeskewedImageElement

```ts
interface DeskewedImageElement extends Core.RegionObjectElement {
    /** The image data for the deskewed image. */
    imageData: Core.DSImageData;
}
```

#### 3.2.6. Rename interface NormalizedImagesUnit to DeskewedImageUnit

```ts
interface DeskewedImageUnit extends Core.IntermediateResultUnit {
    /** `DeskewedImageElement` object, representing a piece of the original image after deskewing. */
    deskewedImage: DeskewedImageElement;
}
```

#### 3.2.7. Add interface EnhancedImageElement

```ts
interface EnhancedImageElement extends Core.RegionObjectElement {
    /** The image data for the enhanced image. */
    imageData: Core.DSImageData;
}
```

#### 3.2.8. Add interface EnhancedImageUnit

```ts
interface EnhancedImageUnit extends Core.IntermediateResultUnit {
    /** `EnhancedImageElement` object, representing a piece of the original image after enhancement. */
    enhancedImage: EnhancedImageElement;
}        
```

#### 3.2.14 Add interface ProcessedDocumentResult

```ts
export interface ProcessedDocumentResult extends Core.CapturedResultBase{
    /** An array of `DetectedQuadResultItem` objects, each representing a quadrilateral after document detection. */
    readonly detectedQuadResultItems: Array<DetectedQuadResultItem>;
    /** An array of `DeskewedImageResultItem` objects, each representing a piece of the original image after deskewing. */
    readonly deskewedImageResultItems: Array<DeskewedImageResultItem>;
    /** An array of `EnhancedImageResultItem` objects, each representing a piece of the original image after enhancement. */
    readonly enhancedImageResultItems: Array<EnhancedImageResultItem>;
};
```

#### 3.2.15. Remove interface DetectedQuadsResult & NormalizedImagesResult

Use `ProcessedDocumentResult` holds all the DDN captured results instead.

#### 3.2.16. Remove saveToFile in interface deskewedImageResultItem

Use `saveToFile()` in `Utility.imageIO` class instead.

#### 3.2.17. Add property sourceLocation in DeskewedImageResultItem/DeskewedImageElement

location基于deskew section的输入图, sourceLocation基于task的原始输入图（和以前的location等效）

```ts
/** The location where the deskewed image was extracted from within the original image, represented as a quadrilateral. */
sourceLocation: Core.Quadrilateral;
```

### 3.3. CVR

#### 3.3.1. Update class IntermediateResultReceiver

1) Rename call back function OnNormalizedImagesReceived to OnDeskewedImageReceived

```ts
/**
 * Event triggered when deskewed images are received.
 * @param result The result unit that contains the deskewed images, of type `DeskewedImageUnit`.
 * @param info Additional information about the result, of type `IntermediateResultExtraInfo`.
 */
onDeskewedImagesReceived?: (result: DDN.DeskewedImageUnit, info: Core.IntermediateResultExtraInfo) => void;
```

2) Add new call back functions

```ts
/**
 * Event triggered when enhanced images are received.
 * @param result The result unit that contains the enhanced images, of type `EnhancedImageUnit`.
 * @param info Additional information about the result, of type `IntermediateResultExtraInfo`.
 */
onEnhancedImagesReceived?: (result: DDN.EnhancedImageUnit, info: Core.IntermediateResultExtraInfo) => void;

/**
* Event triggered when when all tasks for the target ROI are completed and the results are deduplicated.
* @param result The IntermediateResult object that contains the result.
* @param info Additional information about the result, of type `IntermediateResultExtraInfo`.
*/
OnTargetROIResultsReceived?: (result: Core.IntermediateResultUnit, info: Core.IntermediateResultExtraInfo) => void;
```

3) Rename call back function OnScaledDownColourImageUnitReceived to OnScaledColourImageUnitReceived

```ts
/**
 * Event triggered when a scaled color image unit is received.
 * @param result The result unit that contains the scaled color image, of type `ScaledColourImageUnit`.
 * @param info Additional information about the result, of type `IntermediateResultExtraInfo`.
 */
onScaledColourImageUnitReceived?: (result: Core.ScaledColourImageUnit, info: Core.IntermediateResultExtraInfo) => void;
```

4) Rename call back function OnScaledUpBarcodeImageUnitReceived to OnScaledBarcodeImageUnitReceived

```ts
/**
 * Event triggered when a scaled barcode image is received.
 * @param result The result unit that contains the scaled barcode image, of type `ScaledBarcodeImageUnit`.
 * @param info Additional information about the result, of type `IntermediateResultExtraInfo`.
 */
onScaledBarcodeImageUnitReceived?: (result: DBR.ScaledBarcodeImageUnit, info: Core.IntermediateResultExtraInfo) => void;
```

5) Rename call back function OnRawTextLinesReceived to OnRawTextLinesUnitReceived

```ts
/**
* Event triggered when raw text lines are available, occurring each time an image finishes its processing.
* This event is used to handle the text before validation by Dynamsoft Label Recognizer.
* @param result The raw text lines result, an instance of `RawTextLinesUnit`.
* @param info Additional information about the result, of type `IntermediateResultExtraInfo`.
*/
onRawTextLinesUnitReceived?: (result: DLR.RawTextLinesUnit, info: Core.IntermediateResultExtraInfo) => void;
```

6) Rename call back function  onLogicLinesReceived to OnLogicLinesUnitReceived

```ts
/**
 * Event triggered when a logic lines unit is received.
 * @param result The result unit that contains the logic lines, of type `LogicLinesUnit`.
 * @param info Additional information about the result, of type `IntermediateResultExtraInfo`.
 */
onLogicLinesUnitReceived?: (result: DDN.LogicLinesUnit, info: Core.IntermediateResultExtraInfo) => void;
```

---

#### 3.3.3. Update class CapturedResultReceiver

Add call back function onProcessedDocumentResultReceived. CProcessedDocumentResult is a container of DDN items, including DetectedQuadItem、DeskewedImageItem、EnhancedImageItem in this version.

```ts
/**
 * Event triggered when processed documents are available, occurring each time an image finishes its processing.
 * This event is used to handle the results from document normalizer task, including DetectedQuadItem、DeskewedImageItem、EnhancedImageItem.
 * @param result The processed document result, an instance of `ProcessedDocumentResult`.
 */
onProcessedDocumentResultReceived?: (result: DDN.ProcessedDocumentResult) => void;
```

#### 3.3.6 Update CapturedResult to extend CapturedResultBase

```ts
interface CapturedResult extends CapturedResultBase
{
    //删掉在CapturedResultBase中实现的函数
};
```

```ts
interface CapturedResult extends CapturedResultBase
{
    // 更新DDN结果的结构
    /**
     * An array of `BarcodeResultItem` objects, each representing a decoded barcode within the original image. 
     */
    readonly processedDocumentResult?: ProcessedDocumentResult;
};
```

#### 3.3.7 支持StartCapturing过程中修改参数

[skip,JS已经支持] 目前需要支持UpdateSettings接口，InitSettings/ResetSettings维持现有逻辑

#### 3.3.8 加载模型的接口

```ts
class CaptureVisionRouter{
    /**
     * Loads a specific data file containing recognition information. This file typically comprises a Convolutional Neural Networks (CNN) model.
     * @param dataName Specifies the name of the data.
     * @param dataPath [Optional] Specifies the path to find the data file. If not specified, the default path points to the package "dynamsoft-capture-vision-data" which has the same root path as the packag"dynamsoft-capture-vision-router".
     * 
     * @returns A promise that resolves once the recognition data file is successfully loaded. It does not provide any value upon resolution.
     */
    static appendModelBuffer: (dataName: string, dataPath?: string) => Promise<void>;
    /**
     * An event that fires during the loading of a recognition data file (.data).
     * @param filePath The path of the recognition data file.
     * @param tag Indicates the ongoing status of the file download ("starting", "in progress", "completed").
     * @param progress An object indicating the progress of the download, with `loaded` and `total` bytes.
     */
    static onDataLoadProgressChanged: (filePath: string, tag: "starting"| "in progress" | "completed", progress: { loaded: number, total: number }) => void;
}
```

#### 3.3.11 Update SimplifiedCaptureVisionSettings

1) 删除 capturedResultItemTypes
2) 增加 outputOriginalImage

```ts
interface SimplifiedCaptureVisionSettings {
    //capturedResultItemTypes: Core.EnumCapturedResultItemType;
    outputOriginalImage: boolean;
}
```

#### 3.3.12 Update OutputSettings and OutputSettingsToFile API

```ts
/**
 * Returns an object that contains settings for the specified `CaptureVisionTemplate`.
 * @param templateName Specifies a `CaptureVisionTemplate` by its name. If passed "*", treturned object will contain all templates.
 * @param includeDefaultValues Boolean that specifies whether to include default values the output.Default to False.
 * 
 * @returns A promise that resolves with the object that contains settings for tspecified template or all templates.
 */
outputSettings: (templateName: string, includeDefaultValues?: boolean) => Promise<any>;
/**
 * Generates a Blob object or initiates a JSON file download containing the settings fthe specified `CaptureVisionTemplate`.
 * @param templateName Specifies a `CaptureVisionTemplate` by its name. If passed "*", treturned object will contain all templates.
 * @param fileName Specifies the name of the file.
 * @param download Boolean that specifies whether to initiates a file download.
 * @param includeDefaultValues Boolean that specifies whether to include default values the output. Default to False.
 * 
 * @returns A promise that resolves with the Blob object that contains settings for tspecified template or all templates.
 */
outputSettingsToFile: (templateName: string, fileName: string, download?: boolean, includeDefaultValues?: boolean) => Promise<Blob>;
```

#### 3.3.13 Add call back function for CaptureVisionRouter

```ts
/**
 * An event that fires when an error occurs from the start of capturing process.
 * @param error The error object that contains the error code and error string.
 */
onCaptureError: (error: Error) => void;
```

补充说明：
1) Name, Mode, Stage, Section等重要参数，无论includeDefaultValues是true还是false，一律导出

### 3.4. DBR

#### 3.4.1. Rename ScaledUpBarcodeImageUnit to ScaledBarcodeImageUnit

```ts
interface ScaledBarcodeImageUnit extends Core.IntermediateResultUnit {
    //..
}
```

#### 3.4.2 识别流程调整，引入神经网络模型的处理

- 通过增加一个DeblurMode `DM_NEURAL_NETWORK`实现，细节黑盒
- 更新 DeblurMode 枚举

```ts
enum EnumDeblurMode{
    // added in v11.0.10
    /**Performs deblur process by utilizing a neural network model. */
    DM_NEURAL_NETWORK = 0x200,
}
```

#### 3.4.7 Add support for new barcode types

增加以下新码型的支持：
CODE_32, MATRIX_25, KIX, TELEPEN

1) update enum BarcodeFormat

```ts
enum EnumBarcodeFormat{
    /**Code 32*/
    BF_CODE_32 = 0x1000000,
    /*Matrix 25*/
    BF_MATRIX_25 = 0x1000000000,
    /**KIX.*/
    BF_KIX = 0x200000000000000,
    /**Telepen*/
    BF_TELEPEN = 0x2000000000,
    /**Telepen Numeric. A variation of the Telepen format optimized for encoding numeric data only.*/
    BF_TELEPEN_NUMERIC = 0x4000000000,
    /**Combined value of BF2_USPSINTELLIGENTMAIL, BF2_POSTNET, BF2_PLANET, BF2_AUSTRALIANPOST, BF2_RM4SCC, BF_KIX.*/
    BF_POSTALCODE = 0x3F0000000000000,
}
```

2) BF_CODE_32和BF_MATRIX_25的license控制在OneD module上；BF2_KIX的license控制在postal codes module上；BF_TELEPEN和BF_TELEPEN_NUMERIC的license控制在OneD module上;

#### 3.4.8 修复DPM模式下结果中的isMirrored未正确赋值的bug

来自U-11490

#### 3.4.9 Update DecodedBarcodesResult to extend CapturedResultBase

```ts
interface DecodedBarcodesResult extends CapturedResultBase
{
    //删掉在CapturedResultBase中实现的函数
};
```

#### 3.4.10 修复文字行检测中的一个崩溃

来自U-11501，在图片的边界有前景色的比较大的噪点或污染（这些污染的外包矩形的四个点有两个在图片的边界上）的情况下，在文字行检测就可能会发生崩溃

#### 3.4.11 修复Template目录不存在时Linux/Mac下命令行会输出opendir: No such file or directory的bug

#### 3.4.13 add LM_END for EnumLocalizationMode

- LM_END=0xFFFFFFFF //Placeholder value with no functional meaning

#### 3.4.14 add DM_END for EnumDeblurMode

- DM_END=0xFFFFFFFF //Placeholder value with no functional meaning

#### 3.4.15 统一FormatString的格式

barcode的FormatString字符串格式统一成 c++ BarcodeFormat 枚举项去掉 `BF_`后的内容，如
BF_CODE_39 对应的FormatString为 `CODE_39`,
BF_GS1_DATABAR_OMNIDIRECTIONAL 对应的FormatString为 `GS1_DATABAR_OMNIDIRECTIONAL`

#### 3.4.16 更新DeblurMode的默认值以移除DM_MORPHING

#### 3.4.17 修复非标准的code 128不能解码的bug（来自U11566）

#### 3.4.18 A bug fix

- A missing property in SimplifiedBarcodeReaderSettings

    ```ts
    interface SimplifiedBarcodeReaderSettings {
        scaleDownThreshold: number;
    }
    ```

#### 3.4.19 Add property codewords in PDF417 details

```ts
interface PDF417Details extends BarcodeDetails {
    /** The codewords array of the PDF417 Code. */
    codewords: Array<String>;
}
```

### 3.5. DLR

#### 3.5.1 识别流程调整，整合文本行模型识别

根据TextLineSpecification里模型引用配置：
a）仅配置CharacterModelName：完全依赖单字符识别，老流程
b）仅配置TextLineRecModelName：完全依赖文本行识别，不额外进行特征判断、单字符识别、纠错，但会执行正则纠错
c）TextLineRecModelName和CharacterModelName都配置：两者都依赖，也就是目前mrz采用的识别流程（文本行识别+单字符逻辑特征判断+单字符模型识别+易错字符纠错+Overlapping+正则纠错）

#### 3.5.2 参数模板读取解析的调整

1) TextLineSpecification Object新增TextLineRecModelName
2) LabelRecognizerTaskSetting新增OverlappingCharactersPath解析
3) LabelRecognizerTaskSetting新增EnableRegexForceCorrection解析

#### 3.5.3 对于模板中不认识的Key按warning处理

细节参考 [3.7.1 对于模板中不认识的Key按warning处理](#371-对于模板中不认识的key按warning处理)

#### 3.5.4 新增OverlappingCharacters资源加载API（内部接口）

```c
DLR_AppendOverlappingCharactersBuffer(const char* dataName, const char* dataBuffer, int dataLength);
```

#### 3.5.5. Update interface RecognizedTextLinesResult to extend CapturedResultBase

```ts
interface RecognizedTextLinesResult extends Core.CapturedResultBase{
    //删掉在CCapturedResultBase中实现的函数
};
```

#### 3.5.7. Update default value of SimplifiedLabelRecognizerSettings.characterModelName

根据模型新命名规则，characterModelName 默认值由 NumberLetter 改为 NumberLetterCharRecognition

#### 3.5.8. Add APIs for loading non-model data files

```ts
class LabelRecognizerModule{
    static loadConfusableCharsData:(dataName: string, dataPath?: string) => Promise<void>;
    static loadOverlappingCharsData:(dataName: string, dataPath?: string) => Promise<void>;
}
```

### 3.6. DCP & DCPD

#### 3.6.1 对于模板中不认识的Key按warning处理

细节参考 [3.7.1 对于模板中不认识的Key按warning处理](#371-对于模板中不认识的key按warning处理)

#### 3.6.3 增加对 GS1 Application Identifier (AI)的支持

1) license module ：
| ModuleId | ModuleName                 | ModuleCode |
| 9007     | GS1 Application Identifier | GS1_AI     |

2) 模板和mapping文件参考c++版本
   GS1_AI.data;  GS1_AI_Map.txt

#### 3.6.4 DCP & DCPD的版本号统一为 3.0.10

#### 3.6.5 Update ParsedResult to extend CapturedResultBase

```ts
interface ParsedResult extends CapturedResultBase
{
    //删掉在CCapturedResultBase中实现的函数
};
```

### 3.7. DIP

1）DMMatrix增加支持3通道图像初始化

#### 3.7.1 对于模板中不认识的Key按warning处理

1）InitSettings/InitSettingsFromFile/Capture/StartCapturing 统一按照Warning对待，不影响模板正常使用
2）函数返回 EC_UNSUPPORTED_JSON_KEY_WARNING
3）errorMsgBuffer返回如下格式内容：Skipped unsupported keys: key1, key2,..., keyN，每一个key使用带层次结构信息的全路径，使用 ‘.’ 表示嵌套的层级，如果遇到数组，使用 [index] 表示数组的索引，如：
ImageSourceOptions[0].RegionPredetectionModes

### 3.8. DNN

1）合并原有DNN模块中的自研code + onnxruntime裁剪版进行融合，基于vs2022 build
2）CVR采用动态方式加载DNN模块
3) 同时提供加载非加密ort模型和加密ort模型的API

### 3.9. License

#### 3.9.1 计费逻辑添加或调整

- OnDeskewedImageReceived
- OnEnhancedImageReceived
- OnTargetROIResultsReceived
- OnScaledColourImageUnitReceived
- OnScaledBarcodeImageUnitReceived

#### 3.9.2 修改license缓存计算哈希值方式

#### 3.9.3 dls2 license string 支持附加 `?ext=XXX` 字段以更新缓存

### 3.10. Utility

#### 3.10.1. Update class MultiFrameResultCrossFilter

1) Add call back function onProcessedDocumentResultReceived. remove other DDN call back functions.

```ts
class MultiFrameResultCrossFilter implements CVR.CapturedResultFilter {
onProcessedDocumentResultReceived?: (result: any) => void;
}
```

#### 3.10.2. Update class ImageManager

1) Refactor ImageManager class, split into 3 classes. Add new functions in `ImageIO` & `ImageProcessor`.

- `ImageIO` class handles image reading and writing (from/to files and memory).
- `ImageProcessor` class handles image cropping, transformation and format conversions.
- `ImageDrawer` class handles IRR drawing shapes on images.

```ts
class ImageIO {
    /**
     * This method reads an image from a file. The file format is automatically detected based on the file extensioor content.
     * 
     * @param file The file to read, as a Blob object.
     * 
     * @returns A promise that resolves with the loaded image of type `DSImageData`.
     */
    readFromFile: (file: Blob) => Promise<Core.DSImageData>;
    /**
     * This method saves an image in either PNG or JPG format. The desired file format is inferred from the filextension provided in the 'name' parameter. Should the specified file format be omitted or unsupported, the data will default to being exported in PNG format.
     * 
     * @param image The image to be saved, of type `DSImageData`.
     * @param name The name of the file, as a string, under which the image will be saved.
     * @param download An optional boolean flag that, when set to true, triggers the download of the file.
     * 
     * @returns A promise that resolves with the saved File object.
     */
    saveToFile: (image: Core.DSImageData, name: string, download?: boolean) => Promise<File>;
    /**
     * Reads image data from memory using the specified ID.
     * 
     * @param id - The memory ID referencing a previously stored image.
     * 
     * @returns A Promise that resolves to the `DSImageData` object.
     */
    readFromMemory: (id: number) => Promise<Core.DSImageData>;
    /**
     * This method saves an image to memory. The desired file format is inferred from the 'format' parameter. Should the specified file format be omitted or unsupported, the data will default to being exported in PNG format.
     * 
     * @param image A `Blob` representing the image to be saved.
     * @param format The desired image format.
     * 
     * @returns A Promise that resolves to a memory ID which can later be used to retrieve the image via readFromMemory.
     */
    saveToMemory: (image: Blob, format: Core.EnumImageFileFormat) => Promise<number>;
};
```

```ts
class ImageDrawer {
    /**
     * This method draws various shapes on an image, and save it in PNG format.
     * 
     * @param image The image to be saved.
     * @param drawingItem An array of different shapes to draw on the image.
     * @param type The type of drawing shapes.
     * @param color The color to use for drawing. Defaults to 0xFFFF0000 (red).
     * @param thickness The thickness of the lines to draw. Defaults to 1.
     * @param download An optional boolean flag that, when set to true, triggers the download of the file.
     * 
     * @returns A promise that resolves with the saved File object.
     */
    drawOnimage:(image: Blob | string | Core.DSImageData,
                 drawingItem: Array<Core.Quadrilateral> | Core.Quadrilateral | Array<Core.LineSegment> | Core.LineSegment | Array<Core.Contour> | Core.Contour | Array<Core.Corner> | Core.Corner | Array<Core.Edge> | Core.Edge, 
                 type: "quads" | "lines" | "contours" | "edges",
                 color: number,
                 thickness: number,
                 download?: boolean
                ) => Promise<File>;
};
```

```ts
class ImageProcessor {
    /**
     * Crops an image using a rectangle or quadrilateral.
     * @param image The image data to be cropped.
     * @param roi The rectangle or quadrilateral to be cropped.
     * 
     * @returns A promise that resolves with the cropped image data.
     */
    cropImage:(image: Core.DSImageData, roi:Core.DSRect | Core.Quadrilateral) => Promise<Core.DSImageData>;
    
    /**
     * Adjusts the brightness of the image.
     * @param imageData The image data to be adjusted.
     * @param brightness Brightness adjustment value (range: [-100, 100]).
     * 
     * @returns A promise that resolves with the adjusted image data.
     */
    adjustBrightness:(image: Core.DSImageData, brightness: number) => Promise<Core.DSImageData>;
    
    /**
     * Adjusts the contrast of the image.
     * @param imageData The image data to be adjusted.
     * @param contrast Contrast adjustment value (range: [-100, 100]).
     * 
     * @returns A promise that resolves with the adjusted image data.
     */
    adjustContrast:(image: Core.DSImageData, contrast: number) => Promise<Core.DSImageData>;
    
    /**
     * Applies a specified image filter to an input image.
     * @param imageData The image data to be filtered.
     * @param filterType The type of filter to apply.
     * @returns A promise that resolves with the filtered image data.
     */
    filterImage:(image: Core.DSImageData, filterType: EnumFilterType) => Promise<Core.DSImageData>;
    
    /**
     * Converts a colour image to grayscale.
     * @param imageData The image data to be converted.
     * @param R [R=0.3] - Weight for the red channel.
     * @param G [G=0.59] - Weight for the green channel.
     * @param B [B=0.11] - Weight for the blue channel.
     * @returns A promise that resolves with the grayscale image data.
     */
    convertToGray:(image: Core.DSImageData, R:number, G:number, B:number) => Promise<Core.DSImageData>;
    
    /**
     * Converts a grayscale image to a binary image using a global threshold.
     * @param imageData The grayscale image data.
     * @param threshold [threshold=-1] Global threshold for binarization (-1 for automatic calculation).
     * @param invert [invert=false] Whether to invert the binary image.
     * @returns A promise that resolves with the binary image data.
     */
    convertToBinaryGlobal:(image: Core.DSImageData, threshold :number, invert :boolean) => Promise<Core.DSImageData>;
    
    /**
     * Converts a grayscale image to a binary image using local (adaptive) binarization.
     * @param imageData The grayscale image data.
     * @param blockSize [blockSize=0] Size of the block for local binarization.
     * @param compensation [compensation=0] Adjustment value to modify the threshold.
     * @param invert [invert=false] Whether to invert the binary image.
     * @returns A promise that resolves with the binary image data.
     */
    convertToBinaryLocal:(image: Core.DSImageData, blockSize : number, compensation : number, invert : boolean) => Promise<Core.DSImageData>;
};
```

2) update SaveToFile to delete PDF Multi-Page merging feature, return EC_FILE_ALREADY_EXISTS if the pdf file exists and overwrite = false

3) add enum for DDS visual effect filters.

```ts
enum EnumFilterType{
   /**High-pass filter: Enhances edges and fine details by attenuating low-frequency components.*/
   FT_HIGH_PASS,
   /**Sharpen filter: Increases contrast along edges to make the image appear more defined.*/
   FT_SHARPEN,
   /**Smooth (blur) filter: Reduces noise and detail by averaging pixel values, creating a softening effect.*/
   FT_SMOOTH
}
```

### 3.11. dcvDATA

#### 3.11.1. Package structure

1. 停用dlrData, 新建dcvDATA用于托管所有机器学习模型，以及非模型的识别依赖资源
2. 新增OverlappingChars.data文件
3. 模型文件和其他资源文件同层,DLR模型文件名相比上版本有调整，需更新
4. 新增DCP相关的.data以及映射.txt资源
5. 新增预置ui

- 📁 dynamsoft-capture-vision-data/              ---> models & char-resources under ftp://192.168.8.20/Release/Classification/DCV3_Models/Models/
  - 📁 models/
    - 📄 NumberCharRecognition.data
    - 📄 NumberLetterCharRecognition.data
    - 📄 NumberUppercaseCharRecognition.data
    - 📄 NumberLowercaseCharRecognition.data
    - 📄 LetterCharRecognition.data
    - 📄 UppercaseCharRecognition.data
    - 📄 LowercaseCharRecognition.data
    - 📄 VINCharRecognition.data
    - 📄 MRZCharRecognition.data
    - 📄 MRZTextLineRecognition.data
    - 📄 OneDDeblur.data                         ---> new add, DBR oneD super-resolution model
  - 📁 char-resources/                           ---> OCR enhancement .data
    - 📄 OverlappingChars.data
    - 📄 ConfusableChars.data
  - 📁 parser-resources/                         --->DCP resources, mapping files
    - 📄 ...
    - 📄 ...
    - 📄 ...
    - 📄 ...
  - 📁 templates/                             --->Preset-templates
    - 📄 DBR-PresetTemplates.json
    - 📄 DDN-PresetTemplates.json
    - 📄 DLR-PresetTemplates.json
  - 📁 ui/                                    --->Prebuilt-UI files
    - 📄 dce.ui.xml
    - 📄 dce.mobile-native.ui.xml
  - 📄 LEGAL.txt
  - 📄 LICENSE
  - 📄 README.md
  - 📄 package.json

#### 3.11.2. Add readme in TFS for a new npm pkg release

## 4. Install Package

### 4.1 wasm名改为全称,和包名一致

  e.g.   dcv-bundle package --> dynamsoft-capture-vision-bundle.wasm

### 4.4. 预置模板调整

[DBR-PresetTemplates.json](../desktop/templates/dcv-cpp-3.0.1000/DBR-PresetTemplates.json)
[DDN-PresetTemplates.json](../desktop/templates/dcv-cpp-3.0.1000/DDN-PresetTemplates.json)
[DLR-PresetTemplates.json](../desktop/templates/dcv-cpp-3.0.1000/DLR-PresetTemplates.json)
[DriverLicenseScanner.json](../desktop/templates/dcv-cpp-3.0.1000/DriverLicenseScanner.json)
[MRZScanner.json](../desktop/templates/dcv-cpp-3.0.1000/MRZScanner.json)
[VINScanner.json](../desktop/templates/dcv-cpp-3.0.1000/VINScanner.json)

### 4.5. 更新Legal.txt

## 5. Samples

### Update MRZScanner samples

## 6. Docs

## 7. Website

## 8. Discussion

- 2025/04/18
  - Based on C++ v3.0.4000 for the first DCV3 JS release
  - packaging strategy
    ![packaging-strategy](./assets/packaging-strategy.png)

- 2025/04/30
  - 原本sub-modules的专属资源(比如DDN,DBR,DLR各自的模板集合，dce的dce.ui.html等),统一在dcv-data packages中托管。
  - 在engineResourcePath中新增dcvBundle, dbrBundle字段

- 2025/05/08
  - 为了能捕获到startCapturing流程中capture的错误，给cvr加一个错误回调.应用场景是在RTU中，视频流识别下如果有错误，可以在这个错误回调里reject launch().
  - DCE 中新增removePowerBy接口，和BarcodeScanner v10.5.3000 中的属性removePowerBy 功能一致,可控制"power by dynamsoft" message 的显隐。DBR v11 中的BarcodeScanner-RTU 使用该新加的接口来实现. see[dce v4.1.x requirement](../../modules/dce/js/dce-js-4.1.x.md)

- 2025/05/12
  - 更新Utility中ImageIO, ImageDrawer下函数的入参类型，`readFromFile()`接收Blob, 支持更多元的传入; `drawOnimage()`扩展支持 DSImageData类型。其他函数的入参对齐C++ edition，接收ImageData类型。[chat-history](https://teams.microsoft.com/l/message/19:5324030d1ed6479fb8435eb98f145cd1@thread.v2/1747036837652?context=%7B%22contextType%22%3A%22chat%22%7D)
  - 