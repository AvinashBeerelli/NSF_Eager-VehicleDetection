Multi Vehicle Detection

The Repository is for Multi Vehicle Dectection using YOLOV4 and Darknet framework.
The repo has the darknet framewrok written in C and CUDA.

This repo can also be used for custom object detection using YOLOV4.

Steps for implementing the Object Dectection

Data Preparation
----------------

Have Train and Test dataset ready with annotation files in YOLO format, Place both the folders in data folder

1. Changing the cfg file

If you downloaded cfg to google drive you can use the built in Text Editor by going to your google drive and double clicking on yolov4-obj.cfg and then clicking on the Open with drop down and selectin Text Editor.


Have batch = 64 and subdivisions = 16 for ultimate results. If you run into any issues then up subdivisions to 32.

Make the rest of the changes to the cfg based on how many classes you are training your detector on.

How to Configure Your Variables:

width = 416

height = 416 (these can be any multiple of 32, 416 is standard, you can sometimes improve results by making value larger like 608 but will slow down training)

max_batches = (# of classes) * 2000 (but no less than 6000 so if you are training for 1, 2, or 3 classes it will be 6000, however detector for 5 classes would have max_batches=10000)

steps = (80% of max_batches), (90% of max_batches) (so if your max_batches = 10000, then steps = 8000, 9000)

filters = (# of classes + 5) * 3 (so if you are training for one class then your filters = 18, but if you are training for 4 classes then your filters = 27)

Optional: If you run into memory issues or find the training taking a super long time.
In each of the three yolo layers in the cfg, change one line from random = 1 to random = 0 to speed up training but slightly reduce accuracy of model.
Will also help save memory if you run into any memory issues.


2. edit the obj.name and obj.data files in the data folder

change the obj.names to the class labels of your model
change the classes varaible in obj.data file 

Run the VehicleDetection.ipynb file in google Colab
