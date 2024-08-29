# Enhancing ROI Selection in Deep Learning Heatmaps: Using Pathology Location in Chest X-rays as a Case Study


## About the project

In this work we present and evaluate ERSM (Enhanced ROI Selection Method), an adaptive method for selecting accurate RoI (Region of Interest) from deep learning heatmaps. This method employs computer vision algorithms to delineate BB (Bounding Boxes) around body organs and intersects them with Grad-CAM BB from CNN-processed medical images, reducing noise and irrelevant markers in RoI.

## Contributions

1. We propose NRSM (Naive RoI SeLection Method), a baseline, naive method based on selecting RoI around the most intense color in heatmap obtained from the Grad-CAM technique applied to the last convolutional layer of the DenseNet-121 and ResNet-152 models trained on the CheXpert dataset to detect common pathologies. 

2. We design and develop ERSM, a novel method that integrates a series of computer vision techniques to identify regions of body organs and reduce noise in Grad-CAM heatmaps. This method aims to improve the accuracy of RoI selection, providing a more precise delineation of the pathologies predicted by the trained CNN.
 
3. We evaluate the NRSM and ERSM methods using the VinDr-CXR dataset, which contains BB annotations from different radiologists. In this analysis, we evaluate the performance and effectiveness of both methods by comparing them to the radiologists' annotations using area overlap metrics, such as purity, integrity, and the Dice-Sørensen similarity coefficient.


## Structure

We have a script (pathology.ipynb) for each pathology evaluated in the paper (atelectasis, cardiomegaly, consolidation, lung opacity, effusion and pneumothorax) that evaluates the performance of ERSM and NRSM against radiologists using confusion matrices. The script includes all the steps described in the paper.


The images are classified into disease folders to facilitate the computational tasks. Also, each neural network (DenseNet-121 and ResNet-121) has its own folder with the neural network obtained by training on the CheXpert dataset and a set of .txt files (one for each pathology) with the AUC of the image, the width and the height of each CXR. The AUC is used to calculate the confusion matrices of a set of CXRs above a threshold (0.8 and 0.9 in the paper). The width and height are used to scale the coordinates of the bounding boxes marked by the radiologist for comparison with the bounding boxes of the ERSM and NRSM methods, since the heatmaps resulting from the application of the Grad-CAM method in the CNN are in 320x320 (due to the input of the DenseNent-121 and Resnet-152).



