# Automated_RCC_detection

This package provides trained models for automated Renal cell carcinoma (RCC) detection and segmentation in contrast-enhanced CT. <br> 
In order to improve the detection of small RCCs, two models are used. One is a 2D U-Net model for kidney segmentation, and the other is 3D U-Net model for RCC segmentation. These models were trained from scratch with the images from 6 institutions in Japan. <br>

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
The input should be a set of 2D DICOM files in order. <br>
Nephrogenic images or 

The example of the output is shown. <br>
![case001_r](https://user-images.githubusercontent.com/87745605/148885263-f9183ee7-145b-4f39-9627-5c0f850ee1de.png)
