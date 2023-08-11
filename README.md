# Test Torchreg 
Repository for test [Torchreg](https://github.com/codingfisch/torchreg) registration tool comparing with antsRegistration affine.

`Data` from ISBI 2015 - MS Lesion segmentation available [here](https://smart-stats-tools.org/lesion-challenge-2015)  

Test based on [this blog](https://codingfisch.github.io/2023/08/09/affine-registration-in-12-lines-of-code.html)


## Input Images for test
![Data](https://github.com/Nilser3/Test_Torchreg/assets/77469192/723f5d76-08e1-48fc-aa41-995c6ff40d72)

# 1. Affine Intrasubject Intersession registration
## Registration by Torchreg and antsRegistration
a) Torchreg in [notebook](https://github.com/Nilser3/Test_Torchreg/blob/main/code/torchreg_MRI.ipynb)

b) `antsRegistrationSyNQuick.sh -f sub01_ses02_t2.nii.gz -m sub01_ses01_pd.nii.gz -o sub01_ses01_pd_to_sub01_ses02_t2_ -t a`

![Data_2](https://github.com/Nilser3/Test_Torchreg/assets/77469192/5cbb6947-bdc1-4394-b4c9-cb8652e139a2)

### Mutual Information (Torchreg registration)
`MeasureImageSimilarity -d 3 -m MI[sub01_ses02_t2.nii.gz, sub01_PD_to_ses02_t2.nii.gz ,1,32]`

**0.797**
### Mutual Information (antsRegistration)
`MeasureImageSimilarity -d 3 -m MI[ sub01_ses02_t2.nii.gz, ants/sub01_ses01_pd_to_sub01_ses02_t2_Warped.nii.gz ,1,32]`

**0.802**
 
## Registration by Transform warp  - Torchreg 
![image](https://github.com/Nilser3/Test_Torchreg/assets/77469192/9b772b65-b919-43fc-981c-eda8ad6897ff)

# 2. Affine Intersubject registration
## Registration intersubject
a) Torchreg in [notebook](https://github.com/Nilser3/Test_Torchreg/blob/main/code/torchreg_MRI.ipynb)

b) `antsRegistrationSyNQuick.sh -f sub01_ses02_t2.nii.gz -m sub02_ses01_pd.nii.gz -o  ants/sub02_ses01_pd_to_sub01_ses02_t2_ -t a`
![Data_3](https://github.com/Nilser3/Test_Torchreg/assets/77469192/df8d49da-c275-431a-9cf7-d5c1ab9e2700)



### Mutual Information (Torchreg registration)
`MeasureImageSimilarity -d 3 -m MI[sub01_ses02_t2.nii.gz, sub02_PD_to_sub01_ses02_t2.nii.gz.nii.gz ,1,32]`

**0.529**
### Mutual Information (antsRegistration)
`MeasureImageSimilarity -d 3 -m MI[ sub01_ses02_t2.nii.gz, ants/sub02_ses01_pd_to_sub01_ses02_t2_Warped.nii.gz ,1,32]`

**0.543**


## Bibliography

Carass A, Roy S, Jog A, Cuzzocreo JL, Magrath E, Gherman A, Button J, Nguyen J, Prados F, Sudre CH, Jorge Cardoso M, Cawley N, Ciccarelli O, Wheeler-Kingshott CAM, Ourselin S, Catanese L, Deshpande H, Maurel P, Commowick O, Barillot C, Tomas-Fernandez X, Warfield SK, Vaidya S, Chunduru A, Muthuganapathy R, Krishnamurthi G, Jesson A, Arbel T, Maier O, Handels H, Iheme LO, Unay D, Jain S, Sima DM, Smeets D, Ghafoorian M, Platel B, Birenbaum A, Greenspan H, Bazin PL, Calabresi PA, Crainiceanu CM, Ellingsen LM, Reich DS, Prince JL, Pham DL. Longitudinal multiple sclerosis lesion segmentation: Resource and challenge. Neuroimage. 2017 Mar 1;148:77-102. doi: 10.1016/j.neuroimage.2016.12.064. Epub 2017 Jan 11. PMID: 28087490; PMCID: PMC5344762. [PubMed:28087490](https://pubmed.ncbi.nlm.nih.gov/28087490/)
