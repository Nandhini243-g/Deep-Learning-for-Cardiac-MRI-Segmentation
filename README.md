# Deep Learning for Cardiac MRI Segmentation

A deep learning-based medical image segmentation project for automated whole-heart segmentation from cardiac MRI images using preprocessing, data augmentation, baseline 2D and 3D segmentation models, and a proposed context-enhanced segmentation model.

## Acknowledgement

I sincerely thank **Dr. Vidivelli S** for her guidance, encouragement, and continuous support throughout this project. I also acknowledge **SASTRA Deemed University** for providing the resources and academic environment that made this work possible.

This work was carried out as a collaborative team project. I gratefully acknowledge the contributions of my teammates, **Giresh Aditya R** and **Rajasree S**, whose efforts and support were invaluable throughout the development of this project.

## Project Overview

Cardiac Magnetic Resonance Imaging (MRI) is a non-invasive imaging modality widely used for the assessment of cardiac anatomy and cardiovascular diseases. Accurate whole-heart segmentation enables quantitative analysis of cardiac structures, supporting clinical diagnosis, treatment planning, and disease monitoring. However, the complex anatomy of the heart, variations across patients, and the limited availability of annotated medical imaging datasets make automated segmentation a challenging task.

This project explores deep learning approaches for automated whole-heart segmentation from cardiac MRI images. It presents a complete workflow comprising data preprocessing, dataset augmentation, slice-based (2D) and volumetric (3D) baseline segmentation models, followed by a context-enhanced model developed to improve segmentation performance by incorporating additional anatomical information. The models were implemented using PyTorch and MONAI and evaluated using the HVSMR dataset.

## Objective

The primary objective of this project is to develop deep learning models capable of accurately segmenting whole-heart structures from cardiac MRI images.

The project also aims to compare slice-based and volumetric segmentation approaches, investigate the effectiveness of contextual information in improving segmentation performance, and evaluate robust preprocessing and augmentation techniques for medical image analysis.

## Dataset

This project utilizes the **HVSMR (Whole Heart Segmentation from 3D Cardiovascular MRI)** dataset, a publicly available benchmark dataset developed for automated whole-heart segmentation. The dataset contains 3D cardiac MRI volumes together with expert-annotated segmentation masks representing major cardiac structures, providing a challenging benchmark for developing and evaluating deep learning-based medical image segmentation methods.

### Dataset Source

**HVSMR-2.0: A 3D Cardiovascular MR Dataset for Whole-Heart Segmentation in Congenital Heart Disease**

🔗 https://doi.org/10.6084/m9.figshare.c.7074755

### Dataset Overview

- **Imaging Modality:** 3D Cardiac Magnetic Resonance Imaging (MRI)
- **Task:** Automated whole-heart segmentation
- **Dataset:** HVSMR
- **Input Format:** NIfTI (.nii/.nii.gz)
- **Ground Truth:** Expert-annotated segmentation masks
- **Application:** Segmentation of cardiac anatomical structures for medical image analysis

## Base Research Papers

The following publications were referred to during the literature review to understand existing approaches for cardiac MRI segmentation and the characteristics of the HVSMR dataset. These studies provided valuable background knowledge and helped establish the foundation for this project. However, the implementation presented in this repository was developed independently using **PyTorch** and **MONAI** and is not a direct reproduction of any of the following works.

### 1. Deep Learning for Cardiac Image Segmentation: A Review

**Authors:** Chen, C., Qin, C., Qiu, H., Tarroni, G., Duan, J., Bai, W., & Rueckert, D.

This review paper provides a comprehensive overview of deep learning techniques for cardiac image segmentation, discussing commonly used network architectures, publicly available datasets, evaluation metrics, and current challenges in the field. It served as a reference for understanding existing segmentation methodologies and recent developments in cardiac image analysis.

### 2. HVSMR-2.0: A 3D Cardiovascular MR Dataset for Whole-Heart Segmentation in Congenital Heart Disease

**Authors:** Pace, D. F., Contreras, H. T. M., Romanowicz, J., et al.

This publication introduces the HVSMR-2.0 dataset, describing its acquisition, expert annotations, and its role as a benchmark for automated whole-heart segmentation. It served as the primary reference for understanding the dataset used throughout this project.

## Project Workflow

The project follows a structured workflow for automated whole-heart segmentation from cardiac MRI images. The pipeline begins with preprocessing the raw MRI volumes and corresponding segmentation masks to ensure consistent data quality. Data augmentation techniques are then applied to improve dataset diversity and enhance the robustness of the segmentation models.

Following data preparation, baseline segmentation models are developed using both slice-based (2D) and volumetric (3D) approaches to establish reference performance. A context-enhanced segmentation model is subsequently implemented to investigate the incorporation of additional contextual information for whole-heart segmentation. Finally, the models are evaluated using standard segmentation metrics on the HVSMR dataset.

The overall workflow of the project is summarized below:

```text
HVSMR Dataset
      │
      ▼
Data Preprocessing
      │
      ▼
Data Augmentation
      │
      ├──────────────┐
      ▼              ▼
2D Baseline      3D Baseline
      │              │
      └──────┬───────┘
             ▼
 Context-Enhanced Model
             │
             ▼
        Model Evaluation
```
## Data Preprocessing

Prior to model development, the cardiac MRI volumes and corresponding segmentation masks were preprocessed to ensure consistency across the dataset and improve the quality of the input data. Medical image preprocessing is an essential step in segmentation tasks, as it reduces variations arising from differences in image acquisition and prepares the data for efficient model training.

The preprocessing pipeline implemented in this project includes the following steps:

- **Image Loading:** Cardiac MRI volumes and corresponding segmentation masks were loaded from NIfTI (`.nii`/`.nii.gz`) files.
- **Intensity Normalization:** Image intensities were normalized to reduce variations across MRI scans and improve training stability.
- **Spatial Resampling:** MRI volumes were resampled to achieve consistent voxel spacing across the dataset.
- **Region of Interest Extraction:** Relevant cardiac regions were identified and prepared for model training.
- **Data Formatting:** The processed images and segmentation masks were converted into formats compatible with the deep learning pipeline implemented using PyTorch and MONAI.

These preprocessing steps ensured that the input data maintained consistent spatial characteristics while preserving important anatomical information required for accurate whole-heart segmentation.

## Data Augmentation

To improve the diversity of the training data and enhance the generalization capability of the segmentation models, data augmentation techniques were applied to the preprocessed cardiac MRI volumes and their corresponding segmentation masks. Augmentation helps expose the models to a wider range of anatomical variations and imaging conditions, thereby reducing the risk of overfitting and improving robustness during training.

The augmentation pipeline implemented in this project includes the following transformations:

- **Random Rotation:** Introduces rotational variations to improve robustness against orientation changes.
- **Random Flipping:** Applies random flips along different spatial axes to increase data diversity.
- **Random Translation:** Introduces small spatial shifts to improve invariance to positional changes.
- **Random Scaling:** Applies scaling transformations while preserving anatomical consistency.
- **Gaussian Noise:** Adds controlled noise to improve robustness against imaging variations.

These augmentation techniques increase the diversity of the training data while preserving the anatomical correspondence between the cardiac MRI volumes and their associated segmentation masks, enabling the segmentation models to learn more robust and generalized feature representations.
## Baseline Models

To establish reference performance for whole-heart segmentation, baseline models were developed using both two-dimensional (2D) and three-dimensional (3D) segmentation approaches. These models provide a basis for evaluating different learning strategies before investigating the proposed context-enhanced segmentation model.

The 2D baseline processes individual MRI slices independently, offering lower computational complexity and faster training. In contrast, the 3D baseline operates directly on volumetric MRI data, enabling the model to learn spatial relationships across adjacent slices and capture richer anatomical information.

### 2D Baseline Model

The 2D baseline model performs slice-wise segmentation by processing individual cardiac MRI slices independently. This approach reduces computational requirements while providing an effective baseline for evaluating segmentation performance on two-dimensional medical images.

The model was implemented using the PyTorch and MONAI frameworks and trained using preprocessed and augmented MRI slices together with their corresponding segmentation masks.

### 3D Baseline Model

The 3D baseline model performs volumetric segmentation by processing complete three-dimensional MRI volumes instead of individual slices. By learning spatial relationships across multiple slices simultaneously, the model captures richer anatomical context, making it well suited for whole-heart segmentation tasks.

The model was implemented using PyTorch and MONAI and trained on the preprocessed and augmented HVSMR dataset to establish a volumetric baseline for comparison with the proposed model.
## Proposed Model

Building upon the baseline segmentation models, a context-enhanced segmentation model was developed to investigate the incorporation of additional contextual information into the whole-heart segmentation pipeline. The motivation behind this approach was to explore whether leveraging richer spatial and anatomical context could improve the segmentation of complex cardiac structures in MRI images.

The proposed model was implemented using **PyTorch** and **MONAI** and trained using the same preprocessed and augmented HVSMR dataset. Its performance was evaluated alongside the baseline 2D and 3D models to assess its effectiveness for automated whole-heart segmentation.

The development of the proposed model represents an ongoing effort to investigate context-aware segmentation strategies for cardiac MRI analysis and serves as an extension of the baseline approaches explored in this project.

## Model Evaluation

The developed segmentation models were evaluated on the HVSMR dataset to assess their ability to accurately identify whole-heart anatomical structures from cardiac MRI volumes. Model performance was assessed by comparing the predicted segmentation masks with the corresponding expert-annotated ground truth masks.

The evaluation focused on analyzing the segmentation quality of the baseline 2D model, the baseline 3D model, and the proposed context-enhanced model. Both quantitative evaluation metrics and qualitative visual inspection of the predicted segmentation outputs were used to compare model performance.

The evaluation aimed to investigate:

- Segmentation accuracy of the baseline models.
- The effectiveness of volumetric (3D) learning compared to slice-based (2D) segmentation.
- The contribution of contextual information in improving whole-heart segmentation performance.
- The robustness of the proposed model on the HVSMR dataset.

The experimental results obtained from these evaluations provide insights into the strengths and limitations of each segmentation approach for automated cardiac MRI analysis.

