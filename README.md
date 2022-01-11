# Automated_RCC_detection

This package provides trained models for automated Renal cell carcinoma (RCC) detection and segmentation in contrast-enhanced CT. <br>
In order to improve the detection of small RCCs, two models are used. One is a 2D U-Net model for kidney segmentation, and the other is 3D U-Net model for tumor segmentation. These models were trained from scratch with the images from 6 institutions in Japan. <br>

### Requirements  
numpy==1.17.1 <br>
Pillow==6.1.0 <br>
pydicom==1.3.0 <br>
scikit_image==0.15.0 <br>
scipy==1.3.1 <br>
SimpleITK==1.2.4 <br>
tensorflow==1.14.0 <br>
Keras==2.2.5 <br>

### Input 
The input is a set of directories in the directory named "cases_example". Each directory should contain 2D abdominal images of one patient in DICOM format. The images should be listed in order. Nephrogenic images or single-phase postcontrast images are recommended.

### Preprocessing
First, each DICOM image is converted to numpy format. From each 2Dimage, regions that corresponded to non-tissue areas are masked. Window level and window width are set to be 40 HU and 400 HU, respectively. Then, the intensity level is rescaled between 0 and 255, and the images are normalized so that the pixel values are between 0 and 1. After intensity scaling, the image is downsampled to 2×2 mm resolutions to reduce the computational complexity. Finally, the images are cropped to 160×160 pixels. 

### Tumor segmentation and the output
First, both kidneys were segmented by the 2D U-Net model. Images are separated into the left and right sides. For each side, when the sum of the segmented pixel count of the kidney is higher than the threshold (default is 1000), the kidney area is extracted. Otherwise, the algorithm concludes that the area has no kidney. For kidney extraction, the slice with the maximum segmented pixel count is calculated. The central point of the kidney in the slice is estimated from the segmentation result. A 64×64 pixel region around the point is extracted with 40 slices around the slice. These extracted areas are concatenated into 40×64×64 voxels.<br> 
From each kidney area, the tumor is segmented using the 3D U-Net model. If the segmented voxel count is higher than the threshold (default is 50), it is concluded that an RCC-suspected lesion is detected. In this package, the most segmented axial slice and the bounding box around the lesion is saved  as PNG format in the directory named "save_example".<br>
<br>
An example of the output is below. <br>
![case001_r](https://user-images.githubusercontent.com/87745605/148885263-f9183ee7-145b-4f39-9627-5c0f850ee1de.png)
