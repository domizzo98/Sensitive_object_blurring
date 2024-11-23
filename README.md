# Sensitive Object Detection and Blurring with Mask R-CNN

## Overview

This project focuses on detecting and blurring sensitive objects (e.g., monitors, laptops, whiteboards) in images from office settings using instance segmentation. We explored implementing and fine-tuning a Mask R-CNN model, combining both low-level architecture building and high-level application leveraging state-of-the-art frameworks.

### Problem

Data protection policies often require sensitive objects, such as screens or whiteboards, to be hidden in shared office images. Our goal was to create a tool to automate this task, identifying sensitive objects and blurring them while maintaining flexibility for users to customize which objects are blurred. This functionality can be extended for corporate or individual use in securing visual data.

## Approach

We approached the problem with three models to balance complexity, performance, and practical application:

- Custom Mask R-CNN Implementation: We initially built a Mask R-CNN from scratch, starting with a Region Proposal Network (RPN) using MobileNetV2 as the backbone. However, due to dataset limitations and challenges in convergence, we pivoted from this approach.

- U-Net for Semantic Segmentation: We implemented a U-Net for semantic segmentation as an intermediate step. While it generated promising masks and visual results, it lacked the flexibility to distinguish instances within the same class, limiting user control.

- Fine-Tuned Mask R-CNN with Detectron2: To achieve our target, we fine-tuned a pre-trained Mask R-CNN using the Detectron2 framework. We augmented the dataset with flipped images and included an additional sensitive class (whiteboards). This model reached an average precision (AP50) of ~77% and demonstrated high accuracy in blurring sensitive objects.

## Key Features

- Custom Dataset: Images of sensitive objects sourced and annotated from COCO and RoboFlow datasets.

- Flexible Blurring: Users can selectively blur detected objects, blending original and blurred image layers using Gaussian filters.

- Augmentation: Dataset augmented with flipped and additional class examples for better generalization.

## Results

The fine-tuned Mask R-CNN delivered robust performance:

- Average Precision (AP50): 77%

- Average Recall (AR, large): 74%

## Future Work

- Expand the custom dataset to include more sensitive labels and diverse contexts.

- Optimize model inference speed and memory requirements for real-world deployment.

- Explore lightweight architectures for mobile and edge-device compatibility.

