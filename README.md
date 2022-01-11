# Automated_RCC_detection

This package provides trained models for automated Renal cell carcinoma (RCC) detection and segmentation in contrast-enhanced CT. 
In order to improve the detection of small RCCs, two models are used. One is a 2D U-Net model for kidney segmentation, and the other is 3D U-Net model for RCC segmentation. These models were trained from scratch with the images from 6 institutions in Japan.

### Requirements
numpy==1.17.1
Pillow==6.1.0
pydicom==1.3.0
scikit_image==0.15.0
scipy==1.3.1
SimpleITK==1.2.4
tensorflow==1.14.0
Keras==2.2.5

### Input
The input should be a set of 2D DICOM files in order.
Nephrogenic images or 

The example of the output is shown.
![case001_r](https://user-images.githubusercontent.com/87745605/148885263-f9183ee7-145b-4f39-9627-5c0f850ee1de.png)
