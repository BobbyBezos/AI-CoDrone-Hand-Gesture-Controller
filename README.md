# MediaPipe Drone Controller

A hand-gesture-controlled drone interface built using MediaPipe hand tracking.

## Credits

This project is based on:
https://github.com/Kazuhito00/hand-gesture-recognition-using-mediapipe

Original author:
Kazuhito Takahashi

## Changes from the original project

- Added custom gesture classification model
- Added drone control mode
- Added custom commands and gestures
- Modified inference pipeline
- Updated UI and controls

## Project Description

This project uses MediaPipe hand tracking and a custom-trained gesture recognition model to control a drone using hand gestures captured through a webcam. The program detects hand landmarks in real time, classifies gestures, and converts them into drone commands such as takeoff, landing, movement, and hovering.

The project was developed by modifying the open-source hand gesture recognition project by Kazuhito Takahashi and adding custom gesture classification and drone control functionality.

---

## AI Control Method

The project uses machine learning for hand gesture recognition.

1. MediaPipe Hands detects 21 hand landmarks from webcam footage.
2. A custom-trained TensorFlow Lite (TFLite) model classifies the hand pose.
3. The recognised gesture is mapped to a drone command.
4. Commands are sent to the drone through the drone control library.

The model was trained using hand landmark coordinate data collected through the application.

---

## Resources Used

### Libraries

* MediaPipe
* OpenCV
* TensorFlow / TensorFlow Lite
* NumPy

### Tutorials and References

* MediaPipe documentation
* OpenCV documentation
* TensorFlow documentation
* Original project:
  https://github.com/Kazuhito00/hand-gesture-recognition-using-mediapipe

### Additional Resources

* CoDrone EDU Python SDK documentation: https://docs.robolink.com/docs/CoDroneEDU/Python/
* GitHub examples and community tutorials related to MediaPipe hand tracking

---

## Installation

Install Python 3.10 or later.

Install the required libraries:

```bash
pip install mediapipe
pip install opencv-python
pip install tensorflow
pip install numpy
pip install codrone
```

---

## Running the Program

1. Connect the drone controller to your computer and switch the controller to link mode, which allows the computer to control the drone.
2. Open a terminal in the project folder.
3. Run:

```bash
python app.py
```

4. Allow webcam access when prompted.
5. Show recognised gestures to the camera to control the drone.

---

## Controls

### Open Hand -> Takeoff
If drone has already taken off, Open Hand will do nothing.

### Closed Fist -> Emergency Stop
This will make the propellors immediately stop, causing drone to fall.
For caution, Closed Fist must be held for a second to prevent accidental stops.

### Okay Sign -> Land
Drone will stop moving and slowly land.

### Peace Sign -> Forward
Drone's pitch will be set to move_speed degrees, which can be changed and is by default 60

### Phone -> Backward
Drone's pitch will be set to -move_speed degrees, which can be changed and is by default 60

### Point Left -> Left
Drone's roll will be set to -move_speed degrees, which can be changed and is by default 60

### Point Right -> Right
Drone's roll will be set to move_speed degrees, which can be changed and is by default 60

### Point Up -> Up
Drone's throttle will be set to move_speed, which can be changed and is by default 60

### Point Down -> Down
Drone's throttle will be set to -move_speed, which can be changed and is by default 60

### Spiderman Sign -> Flip
Drone will attempt to flip, only works when drone battery is >50%

---
## Modes

### Drone Mode
Drone mode is used so that when off, the program can run the hand gesture recognition without having a drone connected, which would otherwise result in errors.
Drone mode is set to False when program is run.
Press *Enter* to to toggle it.

### Control Mode
Control mode is used to toggle whether hand gestures control the drone when it is connected.<br>
Control mode is set to False when the program is run.
Press *Space* to toggle it.<br>
Control mode's polarity can be seen by the coloured outline around the screen.
- Red indicates that it is off
- Green indicates that it is on

### Data Collection Mode
The Data Collection Mode allows the user to collect more data for the model to be further trained.
To turn Data Collection Mode on, press the *k* key.
To return back to the default mode, press *n*<br>

By pressing keys 0 through 9, hand keypoints are saved in

---

## Known Issues and Limitations

* Gesture recognition accuracy decreases in poor lighting conditions.
* The model can only detect one hand at a time.
* Fast hand movements can occasionally be misclassified.
* The webcam must have a clear view of the hand.
* Drone response depends on wireless connection quality.
* The project has only been tested on Windows 10/11 with Python 3.13.13.


---

## License

This project includes code derived from the original project, which is licensed under the Apache License 2.0.

See the LICENSE file for details.
