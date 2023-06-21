---
layout: default-layout
title: Dynamsoft Document Normalizer JavaScript API Reference - Main Page
description: This is the main page of Dynamsoft Document Normalizer SDK API Reference for JavaScript Language.
keywords: DocumentNormalizer, api reference, JavaScript
permalink: /programming/javascript/api-reference/index.html
---

# API Reference - JavaScript

## Primary Class

- [`CaptureVisionRouter`]({{ site.dcv_js_api }}capture-vision-router/capture-vision-router.html)

## Input

<!-- - [`DirectoryFetcher`]({{ site.dcv_js_api }}utility/directory-fetcher.html) -->
- [`CameraEnhancer`]({{ site.dce_js_api }})
- [`ImageSourceAdapter`]({{ site.dcv_js_api }}core/basic-structures/image-source-adapter.html)
<!-- - [`ProactiveImageSourceAdapter`]({{ site.dcv_js_api }}utility/proactive-image-source-adapter.html) -->

## Final Results

- [`CapturedResultReceiver`]({{ site.dcv_js_api }}core/basic-structures/captured-result-receiver.html)
- [`CapturedResultItem`]({{ site.dcv_js_api }}core/basic-structures/captured-result-item.html)
- [`CapturedResult`]({{ site.dcv_js_api }}core/basic-structures/captured-result.html)
<!-- - [`CapturedResultArray`]({{ site.dcv_js_api }}core/basic-structures/captured-result-array.html) -->
- [`DetectedQuadResultItem`]({{ site.js_api }}detected-quad-result-item.html)
- [`DetectedQuadsResult`]({{ site.js_api }}detected-quads-result.html)
<!-- - [`DetectedQuadsResultArray`]({{ site.js_api }}detected-quads-result-array.html) -->
- [`NormalizedImageResultItem`]({{ site.js_api }}normalized-image-result-item.html)
- [`NormalizedImagesResult`]({{ site.js_api }}normalized-images-result.html)
<!-- - [`NormalizedImagesResultArray`]({{ site.js_api }}normalized-images-result-array.html) -->
- [`RawImageResultItem`]({{ site.dcv_js_api }}core/basic-structures/raw-image-result-item.html)

<!-- 
## Final Results Filters

- [`CapturedResultFilter`]({{ site.dcv_js_api }}core/basic-structures/captured-result-filter.html)
- [`MultiFrameResultCrossFilter`]({{ site.dcv_js_api }}utility/multi-frame-result-cross-filter.html) -->

## Intermediate Results

- [`IntermediateResultManager`]({{ site.dcv_js_api }}core/intermediate-results/intermediate-result-manager.html)
- [`IntermediateResultReceiver`]({{ site.dcv_js_api }}core/intermediate-results/intermediate-result-receiver.html)
- [`ObservationParameters`]({{ site.dcv_js_api }}core/intermediate-results/observed-parameters.html)
- [`IntermediateResultExtraInfo`]({{ site.dcv_js_api }}core/structs/intermediate-result-extra-info.html)
- [`IntermediateResult`]({{ site.dcv_js_api }}core/intermediate-results/intermediate-result.html)
- [`IntermediateResultUnit`]({{ site.dcv_js_api }}core/intermediate-results/intermediate-result-unit.html)
- [`PredetectedRegionsUnit`]({{ site.dcv_js_api }}core/intermediate-results/predetected-regions-unit.html)
- [`DetectedQuadsUnit`]({{ site.js_api }}detected-quads-unit.html)
- [`NormalizedImagesUnit`]({{ site.js_api }}normalized-image-unit.html)
- [`RegionObjectElement`]({{ site.dcv_js_api }}core/intermediate-results/region-object-element.html)
- [`PredetectedRegionElement`]({{ site.dcv_js_api }}core/intermediate-results/predetected-region-element.html)
- [`DetectedQuadElement`]({{ site.js_api }}detected-quad-element.html)
- [`NormalizedImageElement`]({{ site.js_api }}normalized-image-element.html)
- [`BinaryImageUnit`]({{ site.dcv_js_api }}core/intermediate-results/binary-image-unit.html)
- [`CandidateQuadEdgesUnit`]({{ site.js_api }}candidate-quad-edges-unit.html)
- [`ColourImageUnit`]({{ site.dcv_js_api }}core/intermediate-results/colour-image-unit.html)
- [`ContoursUnit`]({{ site.dcv_js_api }}core/intermediate-results/contours-unit.html)
- [`CornersUnit`]({{ site.js_api }}corners-unit.html)
- [`EnhancedGrayscaleImageUnit`]({{ site.dcv_js_api }}core/intermediate-results/enhanced-grayscale-image-unit.html)
- [`GrayscaleImageUnit`]({{ site.dcv_js_api }}core/intermediate-results/grayscale-image-unit.html)
- [`LineSegmentsUnit`]({{ site.dcv_js_api }}core/intermediate-results/line-segments-unit.html)
- [`LongLinesUnit`]({{ site.js_api }}long-lines-unit.html)
- [`ScaledDownColourImageUnit`]({{ site.dcv_js_api }}core/intermediate-results/scaled-down-colour-image-unit.html)
- [`TextRemovedBinaryImageUnit`]({{ site.dcv_js_api }}core/intermediate-results/text-removed-binary-image-unit.html)
- [`TextZonesUnit`]({{ site.dcv_js_api }}core/intermediate-results/text-zones-unit.html)
- [`TextureDetectionResultUnit`]({{ site.dcv_js_api }}core/intermediate-results/texture-detection-result-unit.html)
- [`TextureRemovedBinaryImageUnit`]({{ site.dcv_js_api }}core/intermediate-results/texture-removed-binary-image-unit.html)
- [`TextureRemovedGrayscaleImageUnit`]({{ site.dcv_js_api }}core/intermediate-results/texture-removed-grayscale-image-unit.html)
- [`TransformedGrayscaleImageUnit`]({{ site.dcv_js_api }}core/intermediate-results/transformed-grayscale-image-unit.html)

## Settings

- [`SimplifiedCaptureVisionSettings`]({{ site.dcv_js_api }}capture-vision-router/structs/simplified-capture-vision-settings.html)
- [`PresetTemplate`]({{ site.dcv_js_api }}capture-vision-router/auxiliary-classes/preset-template.html)

## State Listener

- [`CaptureStateListener`]({{ site.dcv_js_api }}capture-vision-router/auxiliary-classes/capture-state-listener.html)
- [`ImageSourceStateListener`]({{ site.dcv_js_api }}capture-vision-router/auxiliary-classes/image-source-state-listener.html)

## [`CLicenseManager`]({{ site.dcv_js_api }}license/license-manager.html)

## Basic Structure

- [`Contour`]({{ site.dcv_js_api }}core/basic-structures/contour.html)
- [`Corner`]({{ site.dcv_js_api }}core/basic-structures/corner.html)
- [`Edge`]({{ site.dcv_js_api }}core/basic-structures/edge.html)
- [`FileImageTag`]({{ site.dcv_js_api }}core/basic-structures/file-image-tag.html)
- [`ImageData`]({{ site.dcv_js_api }}core/basic-structures/image-data.html)
- [`ImageTag`]({{ site.dcv_js_api }}core/basic-structures/image-tag.html)
- [`LineSegment`]({{ site.dcv_js_api }}core/basic-structures/line-segment.html)
- [`PDFReadingParameter`]({{ site.dcv_js_api }}core/basic-structures/pdf-reading-parameter.html)
- [`Point`]({{ site.dcv_js_api }}core/basic-structures/point.html)
- [`Quadrilateral`]({{ site.dcv_js_api }}core/basic-structures/quadrilateral.html)
- [`Rect`]({{ site.dcv_js_api }}core/basic-structures/rect.html)
- [`VideoFrameTag`]({{ site.dcv_js_api }}core/basic-structures/video-frame-tag.html)

## Modules

- [`CaptureVisionRouterModule`]({{ site.dcv_js_api }}capture-vision-router/auxiliary-classes/capture-vision-router-module.html)
- [`DocumentNormalizerModule`]({{ site.js_api }}document-normalizer-module.html)
- [`CoreModule`]({{ site.dcv_js_api }}core/basic-structures/core-module.html)
- [`LicenseModule`]({{ site.dcv_js_api }}license/license-module.html)
- [`UtilityModule`]({{ site.dcv_js_api }}utility/utility-module.html)
- [`ImageProcessingModule`]({{ site.dcv_js_api }}image-processing/image-processing-module.html)

## Enumerations

- [`BufferOverflowProtectionMode`]({{ site.enumerations }}core/buffer-overflow-protection-mode.html?src=cpp&&lang=cpp)
- [`CapturedResultItemType`]({{ site.enumerations }}core/captured-result-item-type.html?src=cpp&&lang=cpp)
- [`CornerType`]({{ site.enumerations }}core/corner-type.html?src=cpp&&lang=cpp)
- [`ErrorCode`]({{ site.enumerations }}core/error-code.html?src=cpp&&lang=cpp)
- [`GrayscaleTransformationMode`]({{ site.enumerations }}core/grayscale-transformation-mode.html?src=cpp&&lang=cpp)
- [`ImageCaptureDistanceMode`]({{ site.enumerations }}core/image-capture-distance-mode.html?src=cpp&&lang=cpp)
- [`ImagePixelFormat`]({{ site.enumerations }}core/image-pixel-format.html?src=cpp&&lang=cpp)
- [`ImageSourceState`]({{ site.enumerations }}core/image-source-state.html?src=cpp&&lang=cpp)
- [`ImageTagType`]({{ site.enumerations }}core/image-tag-type.html?src=cpp&&lang=cpp)
- [`IntermediateResultUnitType`]({{ site.enumerations }}core/intermediate-result-unit-type.html?src=cpp&&lang=cpp)
- [`PDFReadingMode`]({{ site.enumerations }}core/pdf-reading-mode.html?src=cpp&&lang=cpp)
- [`RegionObjectElementType`]({{ site.enumerations }}core/region-object-element-type.html?src=cpp&&lang=cpp)
- [`SectionType`]({{ site.enumerations }}core/section-type.html?src=cpp&&lang=cpp)
- [`TargetType`]({{ site.enumerations }}core/target-type.html?src=cpp&&lang=cpp)
- [`VideoFrameQuality`]({{ site.enumerations }}core/video-frame-quality.html?src=cpp&&lang=cpp)
- [`ColourChannelUsageType`]({{ site.enumerations}}core/colour-channel-usage-type.html?src=cpp&&lang=cpp)
