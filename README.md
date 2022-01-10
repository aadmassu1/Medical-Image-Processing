# Medical-Image-Processing
Binary Classification of Parkinson’s Disease by Applying Linear SVM on Shape Features of DaTSPECT Images.  

Original Paper replicated from:
_Shiiba T, Arimura Y, Nagano M, Takahashi T, Takaki A (2020) Improvement of classification performance of 
Parkinson’s disease using shape features for machine learning on dopamine transporter single photon emission computed 
tomography. PLoS ONE 15(1): e0228289. https://doi.org/10.1371/journal. pone.0228289

First, I had to find the appropriate data to use from the PPMI database. After requesting and 
receiving access to the database, I initially started with 44 NC and 46 PD images. Out of which, I 
randomly selected 28 NC images and 23 PD images for training: for a total of 51 training
images. 

Then I randomly selected 13 NC images and 16 PD images for testing: for a total of 29 
testing images. As mentioned by the authors (original paper), the extraction of the ROI (segmentation 
process) was performed manually by the help of an expert. Since that wasn't ideal, an alternatively automatic 
segmentation method was essential. 

The alternative method I have found to work best was Adaptive thresholding technique. For the technique to work best, I found 
that initially passing each image through a low pass gaussian filter was an important step. Neverthless, some 
images have had some residue artifacts right after the segmentation (parts that are not the 
striatum have also been segmented). 

To get rid of these artifacts, an easier method would have been to use morphological operations such as opening; 
but since I did not want the segmented striatum to be affected by the process, I decided to add another step after labeling the markers
and finding the contour. 

In this stage, I find the area of all the contours (including the artifact)
and only keep the ones that have values greater than 10 (value found by trial and error). 


"DaTSCAN_for_PD" : Folder containing raw DaTSCAN images of a patient with Parkinson's disease.
"PD" : Folder containing .png DaTSCAN images of a patient with Parkinson's disease.
"DaTSCAN_of_NC" : Folder containing raw DaTSCAN images of a the Normal Control Group.
"NC" : Folder containing .png DaTSCAN images of a the Normal Control Group.

"Scripts" : Contains all the randomly selected testing & training images (selected from the previous folders), as well as all the scripts used
            for processing the images and the svm model for prediction.
