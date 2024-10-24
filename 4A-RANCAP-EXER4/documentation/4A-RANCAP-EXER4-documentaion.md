# Object Detection with HOG, YOLO, and SSD

This project demonstrates three different object detection methods: Histogram of Oriented Gradients (HOG), You Only Look Once (YOLO), and Single Shot MultiBox Detector (SSD) using TensorFlow. 

# HOG Object Detection

Load an image and convert it to grayscale.
Apply HOG descriptor to visualize features.
Use OpenCV's pre-trained HOG descriptor to detect pedestrians.
YOLO Object Detection

Download YOLOv3 weights, configuration file, and class labels.
Load the YOLO model and preprocess the image.
Perform detection and draw bounding boxes around detected objects.
SSD Object Detection

Download the SSD MobileNet V2 model and label map.
Load the model and image, convert the image to a tensor.
Run the model for detection and draw bounding boxes.

# Results
The results of each detection method will be displayed using Matplotlib. The images will show the original image with bounding boxes drawn around detected objects for each method.

# HOG Results
HOG results visualize the features used for object detection.

# YOLO Results
YOLO provides real-time detection with a balance of speed and accuracy.

# SSD Results
SSD is designed for speed, detecting objects in a single pass.

# Conclusion
The final section of the script visually compares the results of the traditional HOG method with the deep learning approaches (YOLO and SSD). The comparisons highlight the strengths of each method. This can be viewed in image folder.
