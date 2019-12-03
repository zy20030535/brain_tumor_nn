# **Brain Tumor Segmentation & Classification**

## **Problem Statement**
This project aims to utilize 3D convolutional neural networks to classify high-grade gliomas (HGG) and low-grade gliomas (LGG), also known as brain tumors, from 3D MRI scans acquired from the BraTS2019 competition.

## **Requirements**  
- `antspyx == 0.2.2`
- `fslpy == 2.7.0`
- `Keras == 2.3.1`
- `nibabel == 2.5.1`
- `nilearn == 0.5.2`
- `nipype == 1.3.1`
- `numpy == 1.17.2`
- `pandas == 0.25.1`
- `scikit-learn == 0.21.3`
- `tensorflow == 1.15.0`

## Data  
Data was acquired through the Multimodal Brain Tumor Segmentation Challenge 2019 also known as BraTS2019 [1][2][3][4][5].  

[`Detailed Data Description from BraTS2019`](https://www.med.upenn.edu/cbica/brats2019/data.html)   

[`Click here for data`](https://drive.google.com/drive/folders/1R7udpyjkkBFZc5pjddGasphkjcRYg4YQ?usp=sharing)  
```
Capstone Data   
│
└───Training Data (Used to train model)
│   │
│   └───HGG
│   │    └───259 Folders indicating 1 brain each
│   │        Each folder containing 5 types of MRI scans
│   │        │   %flair.nii.gz
│   │        │   %seg.nii.gz
│   │        │   %t1.nii.gz
│   │        │   %t1ce.nii.gz
│   │        │   %t2.nii.gz
│   │
│   └───LGG
│        └───76 Folders indicating 1 brain each
│            Each folder containing 5 types of MRI scans
│            │   %flair.nii.gz
│            │   %seg.nii.gz
│            │   %t1.nii.gz
│            │   %t1ce.nii.gz
│            │   %t2.nii.gz
│   
└───Validation Data (Data the model has never seen)
    │
    └───125 Folders indicating 1 brain each
            Each folder containing 4 types of MRI scans
            │   %flair.nii.gz
            │   %t1.nii.gz
            │   %t1ce.nii.gz
            │   %t2.nii.gz
```


## **Repository Contents**
- `README.md`
- `assets`: Folder containing `.png` contents required for `README.md`
- `pickles`: various `.h5` files from different models that were fitted (too large to be pushed up to GitHub, unsure of what to do)
-  [`01 - Image Data & Preprocessing.ipynb`](https://github.com/aejsong/brain_tumor_nn/blob/master/01%20-%20Image%20Data%20%26%20Preprocessing.ipynb)
-  [`02 - Modeling.ipynb`](https://github.com/aejsong/brain_tumor_nn/blob/master/02%20-%20Modeling.ipynb)

## **Preprocessing**  
### N4 Bias Field Correction
Various MRI scanners have various intensities. BraTS2019 data description explicitly states that the scans were acquired from various scanners from 19 different institutions. The possibility of varying intensities for all MRI scans needs to be accounted for. Correcting bias field will alter the intensities of each MRI scan and ensure each respective part of the brain is represented by the same intensity.


![](assets/README-bbc81d2a.png)  
The image above shoes and original MRI image of a brain.
<br>
<br>
![](assets/README-04ac4114.png)  
The image above shoes the same original MRI image after bias-field correction.

### Skull Stripping  
After Bias Field Correction, Skull Stripping was performed on every image. Since we are detecting brain tumors, we only need to focus on the brain and will therefore remove the skull from MRI images. Doing this will help eliminate noise in our model.  

<img src="assets/README-8c2d4b24.png" width="600" height="250"/>  
The image above shows an original MRI image of a brain.  
<br>  
<br>
<img src="assets/README-96519894.png" width="600" height="250"/>   
The image above shows the same original MRI image post skull-strip.  
<!-- <br>
<br>
<img src="assets/README-de0309e1.png" width="600" height="250"/>  -->

## **Executive Summary**  
The goal of this project is to successfully classify between high-grade gliomas (HGG) and low-grade gliomas (LGG) using 3D-Image Classification through neural networks.  

3D MRI data was acquired through the BraTS2019 competition. Steps needed to acquire the data included signing up through the BraTS2019 competition and requesting data. BraTS2019 Admin then had to approve my account and approve my data request. This is a manual process that took about 2 to 3 days.  

The predictions of the model were measured against accuracy and loss. A very simple model that took about 40 hours to fit on my personal computer returned an accuracy of about 78% for validation data and 81% on training data with a loss of 0.55.

Further improvements to the neural network are made through Google Cloud Compute Engine. The final best model for this project has an accuracy of **INSERT BEST MODEL ACCURACY HERE** with a loss of **INSERT BEST MODEL LOSS HERE**
## **Conclusions & Recommendations**
**INSERT CONCLUSIONS ABOUT FINAL MODEL HERE**
## **Sources**
[1] B. H. Menze, A. Jakab, S. Bauer, J. Kalpathy-Cramer, K. Farahani, J. Kirby, et al. "The Multimodal Brain Tumor Image Segmentation Benchmark (BRATS)", IEEE Transactions on Medical Imaging 34(10), 1993-2024 (2015) DOI: 10.1109/TMI.2014.2377694

[2] S. Bakas, H. Akbari, A. Sotiras, M. Bilello, M. Rozycki, J.S. Kirby, et al., "Advancing The Cancer Genome Atlas glioma MRI collections with expert segmentation labels and radiomic features", Nature Scientific Data, 4:170117 (2017) DOI: 10.1038/sdata.2017.117

[3] S. Bakas, M. Reyes, A. Jakab, S. Bauer, M. Rempfler, A. Crimi, et al., "Identifying the Best Machine Learning Algorithms for Brain Tumor Segmentation, Progression Assessment, and Overall Survival Prediction in the BRATS Challenge", arXiv preprint arXiv:1811.02629 (2018)

[4] S. Bakas, H. Akbari, A. Sotiras, M. Bilello, M. Rozycki, J. Kirby, et al., "Segmentation Labels and Radiomic Features for the Pre-operative Scans of the TCGA-GBM collection", The Cancer Imaging Archive, 2017. DOI: 10.7937/K9/TCIA.2017.KLXWJJ1Q

[5] S. Bakas, H. Akbari, A. Sotiras, M. Bilello, M. Rozycki, J. Kirby, et al., "Segmentation Labels and Radiomic Features for the Pre-operative Scans of the TCGA-LGG collection", The Cancer Imaging Archive, 2017. DOI: 10.7937/K9/TCIA.2017.GJQ7R0EF
