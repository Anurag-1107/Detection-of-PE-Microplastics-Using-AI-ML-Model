# AI-Based Polyethylene Microplastic Detection

## Project Overview

This project investigates the use of deep learning for automated detection and localization of polyethylene (PE) microplastic particles in microscope images. It combines dataset preparation, annotation validation, model training, quantitative performance evaluation, and technical documentation in a reproducible workflow.

The project demonstrates practical skills in structured experimentation, data quality checks, result interpretation, and computer vision-based analysis.

## Objectives

- Prepare and validate a dataset of annotated microscope images.
- Develop a single-class object-detection model for PE particle localization.
- Train and evaluate the model using a defined experimental workflow.
- Interpret quantitative performance metrics and visual prediction outputs.
- Develop a prototype for applying the trained model to new microscope images.
- Document experimental configurations, results, and limitations.

## Methodology

### 1. Dataset preparation and validation

Prepared 496 microscope images and their corresponding YOLO-format annotation files. Checked image–label matching and converted the PE class ID from 2 to 0 to support single-class detection.

### 2. Experimental data splitting

Split the dataset into training, validation, and test subsets using a 70:15:15 ratio and random seed 42.

| Dataset subset | Images |
|---|---:|
| Training | 347 |
| Validation | 74 |
| Test | 75 |

The test subset was kept separate from model training and validation to assess performance on held-out images.

### 3. Model development

Fine-tuned a pretrained YOLOv8n model using the following recorded configuration:

- Epochs: 50
- Image size: 640 × 640
- Batch size: 16
- Optimizer: AdamW
- Initial learning rate: 0.001
- Weight decay: 0.0005
- Environment: Google Colab with a Tesla T4 GPU

### 4. Performance evaluation

Evaluated the trained model using precision, recall, F1-score, mAP@50, and mAP@50–95. Used bounding-box visualizations to examine detection outputs.

### 5. Prototype development

Developed an inference workflow that accepts a microscope image and returns predicted PE detections, bounding boxes, confidence scores, and a predicted particle count.

## Results

The recorded held-out test evaluation reported:

| Metric | Result |
|---|---:|
| Precision | 84.98% |
| Recall | 89.06% |
| F1-score | 86.97% |
| mAP@50 | 93.69% |
| mAP@50–95 | 77.13% |

These metrics describe model performance on the prepared test dataset. They do not establish chemical confirmation of detected particles or guarantee performance on images collected under different conditions.

## Skills Demonstrated

- Structured technical workflow design
- Dataset quality checking and annotation validation
- Experimental configuration and execution
- Quantitative data analysis and interpretation
- Performance evaluation using defined metrics
- Visual inspection of model outputs
- Technical reporting and reproducibility
- Python-based computer vision and machine learning

## Limitations and Future Work

The model detects one class, PE, and relies on the patterns represented in its training data. Future work could evaluate the system on independently collected images, investigate the effect of imaging conditions and confidence thresholds, and compare predictions against expert-verified annotations.

The prototype is intended for research and educational use. Its predictions should not be treated as definitive chemical identification.

## Technologies

Python | PyTorch | Ultralytics YOLOv8 | Matplotlib | Pillow | Google Colab

## Reproducibility

The notebook contains the dataset preparation, training, evaluation, and inference workflow. To reproduce the results, use the corresponding dataset, annotation files, model configuration, and compatible software environment.

Add the dataset source, relevant references, dependency versions, and checkpoint access instructions before publishing the repository.
