# Object-Detection
# Vehicle Counting Project

This project uses YOLO v4 deep learning model to identify cars in images and count them.

## Installation

Before running the project, you need to install Python and OpenCV.

```bash
pip install opencv-python

## Usage
To identify cars in an image, you can use the vehicle_detector.py module.

python
Copy code
import cv2
from vehicle_detector import VehicleDetector

# Load Vehicle Detector
vd = VehicleDetector()

# Load an image
img = cv2.imread('images/pexels-charles-kettor-1077785.jpg')

# Detect vehicles in the image
vehicle_boxes = vd.detect_vehicles(img)

# Draw bounding boxes around the vehicles
for box in vehicle_boxes:
    x, y, w, h = box
    cv2.rectangle(img, (x, y), (x + w, y + h), (25, 0, 180), 3)

# Display the image with bounding boxes
cv2.imshow("Cars", img)
cv2.waitKey(0)
