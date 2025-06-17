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

Orange Rectangular Capacitor
Usually surface-mounted and easily distinguishable by its blocky, rectangular shape and bright orange color.

Black Rectangular Capacitor
Also surface-mounted, typically darker in color, but similar in shape to the orange rectangular type.

Orange Ellipsoidal Capacitor
Characterized by its elliptical shape and orange casing, these are often through-hole components.

These labels were predefined in CVAT and applied consistently during annotation.

## 4. Exporting Annotations
Once the annotation process was completed, the labeled dataset was exported in CVAT’s XML format (CVAT for images 1.1). This format contains all the necessary metadata about the images, including bounding box coordinates, labels, and image dimensions.

## 5. Processing Annotations via Python
A custom Python script was developed to convert the XML annotations into a more accessible format for further processing.

For each image, a corresponding .txt file was generated containing a list of all annotated components with the following fields:

css
Copy code
x_center y_center width height rotation label
x_center, y_center: the center coordinates of the bounding box (in pixels)

width, height: dimensions of the bounding box

rotation: set to 0.0 (as CVAT does not store rotation by default)

label: the assigned class name of the capacitor

The output was structured to match the requirements of downstream tools such as WPCB-EFA and can be easily adapted for training object detection models (e.g., YOLO) or used in area-based component estimation workflows.

Each image generated its own .txt file named after the original image, e.g., PCB1_REC1.txt.


# How to Contribute
You are invited to contribute to this dataset by uploading your PCB images. Images clearly showing tantalum capacitors in different contexts (various board types, component densities, lighting conditions, different angles) are particularly valuable. Ideally, images should be:

- Well-lit and in focus.
- Of sufficient resolution to distinguish component details.
- Accompanied, if possible, by annotations or metadata (e.g., PCB type, confirmed presence of
tantalum capacitors).
