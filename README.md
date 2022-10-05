# GSL-Alphabet-Recognizer
GSL Alphabet Recognizer using [MediaPipe](https://mediapipe.dev/).
We estimate hand pose using MediaPipe (Python Version). 
This is a sample program that recognizes GSL Alphabet hand signs with a simple multilayer perceptron (MLP) using the detected key points.

![](https://github.com/dkourem/GSL-Alphabet-Recognizer/blob/main/demo-video.gif)


This repository contains the following contents.

- Sample code program
- GSL Alfabet Hand sign recognition model (TFLite)

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
| gsl-alfabet-recognizer.py  
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

### Training data(keypoint.csv)
Trained model(keypoint_classifier.tflite)
Label data(keypoint_classifier_label.csv)
Inference module(keypoint_classifier.py)

### utils/cvfpscalc.py
This is a module for FPS measurement.

## Learning data collection
The key point coordinates (21) are the ones that have undergone the following preprocessing up to 24 classes.
![](https://github.com/dkourem/GSL-Alphabet-Recognizer/blob/main/mediapipe-hand-pose.png)

## Reference
-   [MediaPipe](https://mediapipe.dev/)

## Author

- Kazuhito Takahashi([https://twitter.com/KzhtTkhs](https://twitter.com/KzhtTkhs))

## Translation and other improvements 
- Kouremenos Dimitris (https://github.com/dkourem)

## License
GSL Alphabet Recognizer using mediapipe is under [Apache v2 license](https://github.com/kinivi/hand-gesture-recognition-mediapipe/blob/main/LICENSE).
