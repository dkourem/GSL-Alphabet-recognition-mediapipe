# GSL-Alphabet-Recognizer
GSL Alphabet Recognizer using [MediaPipe](https://mediapipe.dev/).
We estimate hand pose using MediaPipe (Python Version). 
This is a sample program that recognizes GSL Alphabet hand signs with a simple multilayer perceptron (MLP) using the detected key points.

![](https://github.com/dkourem/GSL-Alphabet-Recognizer/blob/main/demo-video.gif)


This repository contains the following contents.

- Sample code program
- GSL Alfabet Hand sign recognition model (TFLite)
- Learning data for Alphabet sign recognition 

## Requirements
mediapipe v0.8.11
OpenCV 3.4.2 or Later
Tensorflow 2.3.0 or Later
scikit-learn 0.23.2 or Later (Only if you want to display the confusion matrix)
matplotlib 3.3.2 or Later (Only if you want to display the confusion matrix)

## Using webcam (demo)

Here's how to run the demo using your webcam:

```
python gsl-alfabet-recognizer.py
```
or in some cases as macOS
```
python3 gsl-alfabet-recognizer.py
```

The following options can be specified when running the demo.

--device
Specifying the camera device number (Default：0)
--width
Width at the time of camera capture (Default：960)
--height
Height at the time of camera capture (Default：540)
--use_static_image_mode
Whether to use static_image_mode option for MediaPipe inference (Default：Unspecified)
--min_detection_confidence
Detection confidence threshold (Default：0.5)
--min_tracking_confidence
Tracking confidence threshold (Default：0.5)

## Directory
```bash
│ gsl-alfabet-recognizer.py  
│
├─model
│  ├─keypoint_classifier
│     │  keypoint.csv
│     │  keypoint_classifier.hdf5
│     │  keypoint_classifier.py
│     │  keypoint_classifier.tflite
│     └─ keypoint_classifier_label.csv                  
└─utils
    └─cvfpscalc.py
```
### gsl-alfabet-recognizer.py
This is a sample program for inference.
In addition, learning data (key points) for hand sign recognition.

### model/keypoint_classifier
This directory stores files related to hand sign recognition.
The following files are stored.

-   Training data (keypoint.csv)
-   Trained model (keypoint_classifier.tflite)
-   Label data (24 classes) (keypoint_classifier_label.csv)
-   Inference module (keypoint_classifier.py)
-   Greek alphabet (alphabet-24 letters.csv)

### utils/cvfpscalc.py
This is a module for FPS measurement.

## Learning data collection
The ahnd key points added to "model/keypoint_classifier/keypoint.csv" as shown below.
1st column: Pressed number (used as class ID), 2nd and subsequent columns: Key point coordinates
![](https://user-images.githubusercontent.com/37477845/102345725-28d26280-3fe1-11eb-9eeb-8c938e3f625b.png)

The key point coordinates are the ones that have undergone the following preprocessing one of the 24 classes.
![](https://github.com/dkourem/GSL-Alphabet-Recognizer/blob/main/mediapipe-hand-pose.png)
the landmarks coordinates does :
1. Convert to relative coordinates
2. Flatten to one-dimensional array
3. Normalize to the maximum value (absolute value)

Class ID: 0 is related to "alpha" label. 
Class ID: 1 to "beta" label. 

. . . 

Class ID: 23 for "omega" label.  

## Reference
- [MediaPipe](https://mediapipe.dev/)
- We used and modified code from the [repo](https://github.com/Kazuhito00/hand-gesture-recognition-using-mediapipe).

## License
GSL Alphabet Recognizer using mediapipe is under [Apache v2 license](https://github.com/kinivi/hand-gesture-recognition-mediapipe/blob/main/LICENSE).
