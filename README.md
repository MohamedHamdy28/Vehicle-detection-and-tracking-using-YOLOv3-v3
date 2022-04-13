# This Project solve the Multiple Object Tracking(MOT) problem where:
**Detection**
- First, all the objects are detected in the frame


**Association**
- Once we have detections from the frame, a matching is performed for similar detections with respect to the previous frame

# First: object detection and recognition
**YOLO**
- is able to perform object detection and recognition at the same time
- is a detector applying a singel neural network, which predict bounding boxes and do multi-lable classification

# Second: object tracking
- It is the process of locating moving objects over time in videos
- involves
  - taking an initial set of object detections 
  - creating unique ID for each of the detections
  - tracking the objects over time
  - maintaining the ID assignment  
## Simple online and real time tracking(SORT)
- applies Kalman Filtering and Hungarian method to handel motion prediction and data association
  - Object models contains object position, scale, bounding box ration and mothion prediction for the next frame
  - SORT solves the data association by calculating bounding box intersection over union (IoU) distance 
  - Based on the IoU distance, final assignment is done
- is fast, simple, and have high precision and accuracy 
- cannot handle occlusion very well as SORT relies on a simple motion model 

## Deep SORT
- is an extension of SORT
- improves the matching procedures and reduces the number of identity switches by adding visual appearnces descriptor or appearance features 
- obtains higher accuracy with the use of 
  - Motion measurement
  - Appearance features

# How YOLO and Deep SORT work
**Step 1- Object detection and recognition**
- YOLO or fast-CNN


**Step 2- Motion prediction and feature generation**
- An estimation model is an intermediate phase before the data association, which utilizes the status of each track
- Kalman filter is used to model these states and make motion prediction 
- Feature generation or bounding box desriptors are computed using a pretrained CNN

**Step 3- Tracking**
- Given predicted states from
  - Kalman filtering in previous frame and
  - newly detected box in current frame
- an association is made for the new detection in current frame with old object tracks in the previous frame
- Cosine feature distance, IoU distance and Kalman state distance are calculated for matching update
   

# An example of the output
![image](https://user-images.githubusercontent.com/71794972/133089010-9d9fb086-0527-4855-993a-f29f8658c822.png)
