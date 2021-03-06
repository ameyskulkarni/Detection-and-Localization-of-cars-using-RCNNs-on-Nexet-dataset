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

The next network block is the Region Proposal Network. This is a Fully Convolutional Network. This network uses a concept of Anchors. It is a very interesting concept. This solves the problem of using exactly what length of bounding boxes. The image is scaled down and now each pixel woks as an anchor. 

Each anchor defines a certain number of bounding box primitives. The RPN is used to predict the score of object being inside each of this bounding box primitive. A Region of INterest pooling layer appears next. This is a layer which takes in ROIs of the feature map to compare and classify each bounding box.

A post processing technique of Non-maximal supression is used to select the bounding box with the highest probability of the object being there. The image is scaled back up and this box is displayed. 

Hyperparameters used-
Number of samples for training- 2252
Number of samples for testing- 176
ROIs- 4
epoch length- 500
Epochs- 91
Anchors-9

All results are visible in the ipynb files of training and testing. With only running the 40 epochs the mAP over the test data gave 0.68 value. THis is close to the 75% expected. I trained more and the accuracy visibly improved from the loss graph and the bounding box accuracy but sadly I am not able to find the mAP after this training round because the I increased the dataset size and I always get and error of resource exhaustion. I am planning to make the code more modular so that I can allocate resources to different modules separately and this issue is overcome. The accuarcy can further be improved by training over a larger dataset and running for more epochs. I will try to do this and improve the accuracy. 
Images of all results are also added in this repo. 

Google drive link to check out the assignment- https://drive.google.com/open?id=1KYV_F9dSvXLh5clLvKeb2-sETz-mak6n

train.ipynb- used to train
test.ipynb- for generating loss graphs and finding mAP

References -

1. https://github.com/RockyXu66/Faster_RCNN_for_Open_Images_Dataset_Keras by Rockyxu66- excellent tutorial for using RCNN code on google colab
2. https://towardsdatascience.com/faster-r-cnn-object-detection-implemented-by-keras-for-custom-data-from-googles-open-images-125f62b9141a for understanding the RCNN flow
3. https://tryolabs.com/blog/2018/01/18/faster-r-cnn-down-the-rabbit-hole-of-modern-object-detection/ for understanding the RCNN architecture
4. https://colab.research.google.com/notebooks/welcome.ipynb#recent=true- Google colab for the resources




