# Deep Learning for Cardiac MRI Segmentation

## Acknowledgement

I sincerely thank **Dr. Vidivelli S** for her guidance, encouragement, and continuous support throughout this project. I also acknowledge **SASTRA Deemed University** for providing the resources and academic environment that made this work possible.

This work was carried out as a collaborative team project. I gratefully acknowledge the contributions of my teammates, **Giresh Aditya R** and **Rajasree S**, whose efforts and support were invaluable throughout the development of this project.

## Project Overview

Cardiac Magnetic Resonance Imaging (MRI) is a non-invasive imaging modality widely used for the assessment of cardiac anatomy and cardiovascular diseases. Accurate whole-heart segmentation enables quantitative analysis of cardiac structures, supporting clinical diagnosis, treatment planning, and disease monitoring. However, the complex anatomy of the heart, variations across patients, and the limited availability of annotated medical imaging datasets make automated segmentation a challenging task.

This project explores deep learning approaches for automated whole-heart segmentation from cardiac MRI images. It presents a complete workflow comprising data preprocessing, dataset augmentation, slice-based (2D) and volumetric (3D) baseline segmentation models, followed by a context-enhanced model developed to improve segmentation performance by incorporating additional anatomical information. The models were implemented using PyTorch and MONAI and developed and evaluated using the HVSMR dataset.

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
