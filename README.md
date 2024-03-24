# Object-Detection

Before writing the code for the Count Vehicles we need to find the cars that are present in the single photo. In this project I used the YOLO v4 deep learning model, you can decide whether to download the files I have made available to you or do your training by choosing the most suitable parameters for your project (in this case I recommend you also see Train YOLO to detect a custom object (online with free GPU)).

# Vehicle Counting Project

This project uses YOLO v4 deep learning model to identify cars in images and count them.

## Installation

Before running the project, you need to install Python and OpenCV.

pip install opencv-python

## Usage
To identify cars in an image, you can use the vehicle_detector.py module.

python
Copy code
import cv2
from vehicle_detector import VehicleDetector

## Load Vehicle Detector
vd = VehicleDetector()

## Load an image
img = cv2.imread('images/pexels-charles-kettor-1077785.jpg')

## Detect vehicles in the image
vehicle_boxes = vd.detect_vehicles(img)

## Draw bounding boxes around the vehicles
for box in vehicle_boxes:
    x, y, w, h = box
    cv2.rectangle(img, (x, y), (x + w, y + h), (25, 0, 180), 3)

# Display the image with bounding boxes
cv2.imshow("Cars", img)
cv2.waitKey(0)

##  Loop And Counting On A Images In A Folder
To count all the cars in the folder images, we need to create a loop that allows us to analyze image by image automatically. By using the Python Glob library and integrating it into the code we will achieve our goal.

import glob
...
### Load images from a folder
images_folder = glob.glob("images/*.jpg")
vehicles_folder_count = 0

We can rewrite the second part of the Count Vehicles like this:

### Loop through all the images

   for img_path in images_folder:
       print("Img path", img_path)
       img = cv2.imread(img_path)
       vehicle_boxes = vd.detect_vehicles(img)
       vehicle_count = len(vehicle_boxes)
       # Update total count
       vehicles_folder_count += vehicle_count
       for box in vehicle_boxes:
           x, y, w, h = box
           cv2.rectangle(img, (x, y), (x + w, y + h), (25, 0, 180), 3)
           cv2.putText(img, "Vehicles: " + str(vehicle_count), (20, 50), 0, 2, (100, 200, 0), 3)
       cv2.imshow("Cars", img)
       cv2.waitKey(1)    
   print("Total current count", vehicles_folder_count)


## Screenshot
![Screenshot 2024-03-24 214001](https://github.com/Sakshi-V08/Object-Detection/assets/122119205/1c854228-e632-4da4-a5d8-f2bb0f8ef898)
