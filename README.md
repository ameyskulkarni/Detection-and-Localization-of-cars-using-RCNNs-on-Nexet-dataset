# Detection-and-Localization-of-cars-using-RCNNs-on-Nexet-dataset
This repository presents a code to detect the rear of cars using RCNNs. The dataset consists of road images in different conditions like daylight and night conditions. The labels are given in the .csv format. Each row of the labels file consists of name of the image, details about coordinates of the bounding box(x_min, x_max, y_min and y_max), and the label itself. 

Details are extracted from the csv file and stored in a dataframe. ONly a subset of the data was trained on due to the resource exhaustion. All the details will be given below.  

Object detection: There are two parts to object detection- 
1. Object classification
2. Object localization

Bounding boxes are used usually for the localization purpose and the labels are used for classification. The two major techniques used in the industry for object detection are RCNNs and YOLO. I have dedicated the time spent on these assignments to learn about one of these techniques: RCNNs.

Region Based Convolutional Neural Networks
The Architecture of RCNN is very extensive as it has different blocks of layes for the above mentioned purposes: classification and localization.
The code I have used takes VGG-16 as the first block of layers which take in the images as 3D tensors and and give out feature maps. To understand the importance of Transfer learning, I have used pre-trained weights of this model. This is the base network.

