# Hand Gesture Controller

A computer vision-based application that allows you to control your computer using hand gestures captured through your webcam. Built with Python, OpenCV, and MediaPipe for real-time hand tracking and gesture recognition.

## Features

- **Mouse Control**: Move cursor with hand movements
- **Click Operations**: Left click, right click, and double click
- **Drag & Drop**: Hold and drag objects
- **System Volume Control**: Adjust volume with pinch gestures
- **Screen Brightness Control**: Modify brightness using hand gestures  
- **Scrolling**: Vertical and horizontal scrolling
- **Real-time Processing**: Smooth gesture recognition with noise filtering

## Supported Gestures

| Gesture | Action |
|---------|--------|
| ✌️ V-Gesture | Move cursor / Enable cursor mode |
| ✊ Fist | Click and drag |
| 🖕 Middle Finger | Left click (when cursor active) |
| 👆 Index Finger | Right click (when cursor active) |
| ✌️ Two Fingers Closed | Double click (when cursor active) |
| 🤏 Pinch (Major Hand) | Volume control (Y-axis) / Brightness control (X-axis) |
| 🤏 Pinch (Minor Hand) | Vertical scroll (Y-axis) / Horizontal scroll (X-axis) |

## Requirements

### Hardware
- Webcam or built-in camera
- Windows, macOS, or Linux system

### Software Dependencies

```bash
pip install opencv-python
pip install mediapipe
pip install pyautogui
pip install pycaw
pip install comtypes
pip install screen-brightness-control
pip install protobuf
```

## Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/hand-gesture-controller.git
   cd hand-gesture-controller
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Run the application**
   ```bash
   python gesture_controller.py
   ```

## Usage

1. **Launch the application** - Your webcam will activate and show a live feed
2. **Position your hand** in front of the camera (recommended distance: 1-2 feet)
3. **Perform gestures** as listed in the supported gestures table
4. **Exit the application** by pressing `Enter` key in the camera window

### Tips for Best Performance

- Ensure good lighting conditions
- Keep your hand clearly visible in the camera frame
- Maintain steady hand movements for smoother cursor control
- The dominant hand (right by default) is used for primary controls
- The non-dominant hand (left by default) is used for scrolling

## Configuration

### Changing Dominant Hand

To switch the dominant hand from right to left, modify the `dom_hand` attribute:

```python
GestureController.dom_hand = False  # Set to False for left-handed users
```

### Adjusting Sensitivity

You can fine-tune gesture sensitivity by modifying these parameters:

```python
# In Controller class
pinch_threshold = 0.3  # Adjust pinch sensitivity
```

## Technical Details

### Architecture

- **HandRecog Class**: Converts MediaPipe landmarks to recognizable gestures
- **Controller Class**: Executes system commands based on detected gestures  
- **GestureController Class**: Main class handling camera input and coordination

### Gesture Recognition Pipeline

1. **Capture**: Video frame captured from webcam
2. **Detection**: MediaPipe detects hand landmarks
3. **Classification**: Hand gestures classified using landmark ratios
4. **Filtering**: Noise reduction and gesture stabilization
5. **Execution**: System commands executed based on recognized gestures

## Troubleshooting

### Common Issues

**Camera not detected**
- Ensure your webcam is properly connected
- Check if other applications are using the camera
- Try changing the camera index in `cv2.VideoCapture(0)` to `cv2.VideoCapture(1)`

**Gestures not recognized**
- Improve lighting conditions
- Ensure your hand is clearly visible
- Check that all dependencies are properly installed

**Permission errors (Windows)**
- Run the application as administrator
- Ensure Windows allows camera access for Python applications

**Audio/Brightness control not working**
- Install audio drivers (pycaw dependency)
- For Linux users, install additional brightness control packages

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-gesture`)
3. Commit your changes (`git commit -am 'Add new gesture'`)
4. Push to the branch (`git push origin feature/new-gesture`)
5. Create a Pull Request

## Future Enhancements

- [ ] Add gesture customization interface
- [ ] Implement gesture learning mode
- [ ] Add support for more complex gestures
- [ ] Integrate with smart home devices
- [ ] Add gesture recording and playback
- [ ] Implement multi-user gesture profiles

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- [MediaPipe](https://mediapipe.dev/) for hand tracking capabilities
- [OpenCV](https://opencv.org/) for computer vision processing
- [PyAutoGUI](https://pyautogui.readthedocs.io/) for system control automation

## Contact

For questions, suggestions, or issues, please open an issue on GitHub .

---

**Note**: This application requires camera permissions and system control permissions to function properly. Please ensure you trust the source before running.
