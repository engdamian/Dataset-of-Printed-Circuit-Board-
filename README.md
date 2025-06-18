# DATASET OF PRINTED CIRCUI BOARD
This repository is dedicated to the creation of a collaborative, open-source image dataset of Printed Circuit Boards (PCBs). The primary objective is to gather a wide variety of PCB images to train Artificial Intelligence (AI) models capable of accurately recognizing tantalum capacitors.

# Project Purpose
Tantalum capacitors are electronic components containing tantalum, a critical raw material (CRM) of significant value. The precise identification and selective extraction of these capacitors from end-of-life PCBs are fundamental steps for their efficient recycling and for promoting a circular economy in the electronics sector. As highlighted in the TREASURE project, the recovery of such materials is crucial for a more sustainable supply chain. This dataset aims to provide the necessary visual resources to develop computer vision and AI systems that can automate or semi-automate this recognition process.
## 1. Image Acquisition
The printed circuit boards (PCBs) were photographed using a high-resolution digital camera positioned at a fixed height of 270 millimeters above the PCB surface. This setup was chosen to optimize the pixel resolution across the entire board, especially in the case of larger PCBs, allowing for clear visibility of fine details on surface-mounted components.

Each image was captured with a consistent top-down orientation, under uniform lighting conditions to reduce reflections and shadows, which can interfere with visual component recognition and annotation.

## 2. Component Annotation with CVAT
The captured images were uploaded into CVAT (Computer Vision Annotation Tool) for manual annotation.

Using the bounding box tool in CVAT, each tantalum capacitor visible in the images was enclosed in a rectangle. Annotations were conducted manually and consistently across all images, allowing for high accuracy in component labeling and localization.

## 3. Classification Criteria
Three specific types of tantalum capacitors were identified and annotated, based on their color and shape:

  - Orange Rectangular Capacitor:
    Usually surface-mounted and easily distinguishable by its blocky, rectangular shape and bright orange        color.

  - Black Rectangular Capacitor:
    Also surface-mounted, typically darker in color, but similar in shape to the orange rectangular type.

  - Orange Ellipsoidal Capacitor:
    Characterized by its elliptical shape and orange casing, these are often through-hole components.

These labels were predefined in CVAT and applied consistently during annotation.

## 4. Annotation Structure
Each annotation file is associated with a single image and contains one row per labeled object. The data is structured as follows:
                           <class_id> <x_center> <y_center> <width> <height>
Where:
  •	class_id denotes the numeric identifier of the object class.
  •	x_center and y_center represent the normalized coordinates of the bounding box center, relative to the       image width and height.
  •	width and height indicate the normalized dimensions of the bounding box.
  
All coordinate values are normalized within the range [0, 1], thereby ensuring the annotations remain resolution-independent and compatible with multi-scale training processes.
Class Mapping

The dataset encompasses three capacitor categories, each corresponding to a distinct class ID. The mapping between numerical identifiers and semantic class labels is defined as follows:
Class ID	Object Class Description:
  0 -->	Orange rectangular capacitor
  1	--> Black rectangular capacitor
  2	--> Orange ellipsoidal capacitor
This mapping is explicitly declared in the accompanying data.yaml file, which is used by YOLO-based training pipelines to resolve class identifiers into human-readable class names during both training and inference.


![image](https://github.com/user-attachments/assets/9c6b6fca-2e62-472d-967d-632ec790e8e9)

# How to Contribute
You are invited to contribute to this dataset by uploading your PCB images. Images clearly showing tantalum capacitors in different contexts (various board types, component densities, lighting conditions, different angles) are particularly valuable. Ideally, images should be:

- Well-lit, in focus and at a correct distance (270 mm).
- Of sufficient resolution to distinguish component details.
- Accompanied, if possible, by annotations or metadata (e.g., Type of
tantalum capacitors).
