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

### Key Features

- Custom Dataset: Images of sensitive objects sourced and annotated from COCO and RoboFlow datasets.

- Flexible Blurring: Users can selectively blur detected objects, blending original and blurred image layers using Gaussian filters.

- Augmentation: Dataset augmented with flipped and additional class examples for better generalization.

### Results

The fine-tuned Mask R-CNN delivered robust performance:

- Average Precision (AP50): 77%

- Average Recall (AR, large): 74%

## Future Work

- Expand the custom dataset to include more sensitive labels and diverse contexts.

- Optimize model inference speed and memory requirements for real-world deployment.

- Explore lightweight architectures for mobile and edge-device compatibility.

## References

[1] Chen, L. C., Hermans, A., Papandreou, G., Schroff, F., Wang, P., & Adam, H. (2018). Masklab: Instance segmentation by refining object detection with semantic and direction features. In Proceedings of the IEEE conference on computer vision and pattern recognition (pp. 4013-4022).

[2] He, K., Gkioxari, G., Dollár, P., & Girshick, R. (2017). Mask r-cnn. In Proceedings of the IEEE international conference on computer vision (pp. 2961-2969).

[3] Girshick, R. (2015). Fast r-cnn. In Proceedings of the IEEE international conference on computer vision (pp. 1440-1448).

[4] Ren,S.,He,K.,Girshick,R.,&Sun,J.(2015).Fasterr-cnn:Towardsreal-timeobjectdetectionwith region proposal networks. Advances in neural information processing systems, 28.

[5] Lin, T. Y., Maire, M., Belongie, S., Hays, J., Perona, P., Ramanan, D., ... & Zitnick, C. L. (2014). Microsoft coco: Common objects in context. In Computer Vision–ECCV 2014: 13th European Conference, Zurich, Switzerland, September 6-12, 2014, Proceedings, Part V 13 (pp. 740-755). Springer International Publishing.

[6] Ronneberger, O., Fischer, P., & Brox, T. (2015). U-net: Convolutional networks for biomedical image segmentation. In Medical Image Computing and Computer-Assisted Intervention–MICCAI 2015: 18th International Conference, Munich, Germany, October 5-9, 2015, Proceedings, Part III 18 (pp. 234-241). Springer International Publishing.

[7] AIMeta.Detectron2.https://ai.meta.com/tools/detectron2/

[8] Roboflow.WhiteboardDetection.https://universe.roboflow.com/biit/whiteboard-detection

