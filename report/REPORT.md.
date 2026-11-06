# Day 1 Lab Report – Data Overview AI/ML/DL

## Environment

- Run date: 2026-11-07
- Runtime: Google Colab – CPU
- Python: 3.13.18
- PyTorch: 2.14.1+cpu
- Ultralytics: 8.4.145
- Classification checkpoint: `yolo11n-cls.pt`
- Detection checkpoint: `yolo11n.pt`
- Segmentation checkpoint: `yolo11n-seg.pt`
- Confidence threshold: 0.35
- Changes from source notebook: No changes to the original notebook workflow.

## 1. Image Classification

- Task: Image-level classification.
- Sample: `traffic`
- Predicted class: `cab`
- Class ID: `468`
- Rank: `1`
- Confidence score: `0.510915`
- Taxonomy: `ImageNet-1K`

Classification predicts one or more labels for the entire image, rather than locating individual objects.

The confidence score represents the model's prediction confidence, not a verified ground-truth label.

## 2. Object Detection

- Task: Object detection.
- Sample: `kitchen`
- Taxonomy: `COCO-80`
- Model: `yolo11n.pt`
- Total predictions across all samples: `53`

Example prediction:

- Class: `person`
- Confidence: `0.912625`
- Bounding box (xyxy): `[385.33, 69.24, 498.92, 348.92]`
- Width: `113.58 pixels`
- Height: `279.68 pixels`

### Confidence threshold comparison – Kitchen

| Threshold | Number of predictions |
|---|---:|
| 0.20 | 17 |
| 0.35 | 11 |
| 0.60 | 6 |

A bounding box identifies an object's location using its top-left and bottom-right coordinates.

### Occlusion and truncation

- The foreground person partially occludes the oven and sink.
- Hanging bowls and pans overlap, making object boundaries difficult to distinguish.
- Some objects are truncated by image edges, including the potted plant, bowl, oven, and dining table.

### Annotation guideline

Draw bounding boxes tightly around the visible part of each object. For occluded or truncated objects, annotate only the visible extent. Escalate cases where the category cannot be identified reliably.

## 3. Instance Segmentation

- Task: Instance segmentation.
- Sample: `kitchen`
- Taxonomy: `COCO-80`
- Model: `yolo11n-seg.pt`
- Total predictions across all samples: `49`

Example prediction:

- Instance ID: `kitchen-001`
- Class: `person`
- Class ID: `0`
- Confidence: `0.899318`
- Bounding box: `[385.45, 66.44, 498.02, 348.58]`
- Polygon point count: `348`
- First five polygon points: `[[446,70], [445,71], [444,71], [443,72], [442,72]]`

A bounding box locates an object approximately, while a segmentation mask represents its pixel-level shape.

### Mask quality observations

- Large objects such as the person and dining table are generally covered.
- Small objects and overlapping boundaries are less precise.
- Under-segmentation: the spoon mask misses part of its handle.
- Over-segmentation: the dining table mask leaks into the floor and nearby objects.

### Annotation guideline

Draw masks along the visible boundaries of individual objects. Do not include background areas or neighboring objects. For overlapping objects, annotate only visible regions unless the project guideline specifies otherwise.

Escalate unclear object categories and heavily occluded objects that cannot be identified reliably.

## 4. Annotation Lifecycle and Quality Control

| Task | Ground-truth unit | Main difficulty | Reviewer checks |
|---|---|---|---|
| Classification | Image | Ambiguous image category | Correct image-level label |
| Detection | Object bounding box | Occlusion and overlapping objects | Class and box boundaries |
| Instance segmentation | Object mask | Complex boundaries and small objects | Mask accuracy and object separation |

The model predictions in this lab are not human-verified ground truth. Human annotators and reviewers are needed to validate labels and correct errors.

## 5. Data Safety

1. Avoid including personal or sensitive information in datasets unless explicitly authorized and necessary.
2. Store and share dataset files only through approved locations with appropriate access permissions.

## 6. Submission Checklist

- [ ] `REPORT.md`
- [ ] `classification_predictions.json`
- [ ] `detection_predictions.json`
- [ ] `segmentation_predictions.json`
- [ ] `IMAGE_ATTRIBUTION.md`
- [ ] `classification_top5.png`
- [ ] `detection_predictions.png`
- [ ] `segmentation_prediction.png`
- [ ] Notebook validation cell shows PASS
- [ ] No personal or sensitive data included

Submit the GitHub repository link through the LMS.
