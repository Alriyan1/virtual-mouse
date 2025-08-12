# Virtual Mouse Controller

A computer vision-based application that allows you to control your computer mouse using hand gestures captured through your webcam. This project uses MediaPipe for hand tracking and provides an intuitive way to navigate your computer without physical mouse input.

## 🚀 Features

- **Hand Gesture Recognition**: Real-time hand tracking using MediaPipe
- **Mouse Movement Control**: Control cursor position with index finger
- **Click Functionality**: Perform mouse clicks using index and middle finger gestures
- **Smooth Cursor Movement**: Interpolated movement with smoothing for natural feel
- **Real-time FPS Display**: Monitor performance with live FPS counter
- **Responsive Interface**: Low-latency hand tracking and mouse control
- **Cross-platform Support**: Works on Windows, macOS, and Linux

## 🎯 How It Works

### Gesture Controls

1. **Mouse Movement**: 
   - Raise only your **index finger** (finger 1)
   - Move your hand to control cursor position
   - The cursor follows your index finger tip

2. **Mouse Click**:
   - Raise both **index and middle fingers** (fingers 1 and 2)
   - Bring them close together (distance < 40 pixels)
   - This triggers a mouse click

3. **No Action**:
   - Lower all fingers or use other finger combinations
   - Cursor remains stationary

### Technical Implementation

- **Hand Detection**: MediaPipe Hand Landmarks for precise finger tracking
- **Coordinate Mapping**: Interpolation from camera frame to screen coordinates
- **Smoothing Algorithm**: Exponential smoothing for natural cursor movement
- **Gesture Recognition**: Finger state analysis using landmark positions

## 📋 Prerequisites

- **Python 3.7+**
- **Webcam** (built-in or external USB camera)
- **Sufficient lighting** for hand detection
- **4GB+ RAM** recommended
- **OpenCV-compatible camera drivers**

## 🛠️ Installation

### 1. Clone the Repository
```bash
git clone <repository-url>
cd virtual_mouse
```

### 2. Install Required Packages
```bash
pip install -r requirements.txt
```

Or install manually:
```bash
pip install opencv-python mediapipe numpy autopy
```

### 3. Verify Installation
```bash
python -c "import cv2, mediapipe, numpy, autopy; print('All packages installed successfully!')"
```

## 🚀 Usage

### Running the Application

1. **Start the virtual mouse:**
   ```bash
   python main.py
   ```

2. **Position your hand** in front of the webcam
3. **Use gesture controls** to navigate:
   - Index finger up = move cursor
   - Index + middle finger up + close = click
4. **Press ESC** to exit the application

### Optimal Setup

- **Camera Position**: Place webcam at eye level or slightly above
- **Lighting**: Ensure good, even lighting on your hands
- **Background**: Use a plain, contrasting background
- **Hand Position**: Keep your hand within the frame boundaries
- **Distance**: Maintain 20-50cm distance from camera

## 🏗️ Project Structure

```
virtual_mouse/
├── main.py                    # Main application file
├── handtrackmodule.py         # Hand tracking and detection module
├── requirements.txt           # Python dependencies
└── README.md                 # This documentation file
```

## 🔧 Technical Details

### Core Components

#### `main.py`
- **Camera Setup**: Webcam initialization and configuration
- **Main Loop**: Continuous frame processing and gesture recognition
- **Mouse Control**: Integration with autopy for system mouse control
- **UI Display**: Real-time video feed with gesture overlays

#### `handtrackmodule.py`
- **HandDetector Class**: MediaPipe-based hand tracking
- **Landmark Detection**: 21-point hand landmark identification
- **Gesture Analysis**: Finger state and position calculation
- **Distance Calculation**: Euclidean distance between landmarks

### Key Parameters

```python
wCam, hCam = 640, 480        # Camera resolution
frameR = 100                 # Frame reduction for movement area
smoothening = 5              # Cursor movement smoothing factor
maxHand = 1                  # Maximum hands to track
detectionCon = 1             # Hand detection confidence
trackCon = 0.5               # Hand tracking confidence
```

### Performance Optimization

- **Frame Processing**: Optimized OpenCV operations
- **Memory Management**: Efficient numpy array operations
- **Smoothing Algorithm**: Reduces jitter in cursor movement
- **Gesture Recognition**: Fast finger state analysis

## 🎮 Customization

### Adjusting Sensitivity

1. **Movement Speed**: Modify the `smoothening` variable
   - Lower values = faster, more responsive movement
   - Higher values = slower, smoother movement

2. **Click Distance**: Change the click threshold (default: 40 pixels)
   ```python
   if length < 40:  # Adjust this value
       autopy.mouse.click()
   ```

3. **Camera Resolution**: Modify `wCam` and `hCam` for different quality
   ```python
   wCam, hCam = 1280, 720  # Higher resolution
   ```

### Adding New Gestures

1. **Extend the `fingersUp` method** in `handtrackmodule.py`
2. **Add gesture logic** in the main loop
3. **Implement corresponding actions** using autopy functions

## 🐛 Troubleshooting

### Common Issues

1. **Camera Not Detected**
   - Check camera connections and drivers
   - Verify camera permissions
   - Try different camera indices: `cv2.VideoCapture(1)`

2. **Poor Hand Detection**
   - Improve lighting conditions
   - Use plain, contrasting backgrounds
   - Ensure hands are clearly visible
   - Check camera focus and positioning

3. **Cursor Movement Issues**
   - Adjust `smoothening` parameter
   - Check screen resolution compatibility
   - Verify autopy installation

4. **High CPU Usage**
   - Reduce camera resolution
   - Lower frame processing rate
   - Close unnecessary applications

### Performance Tips

- **Optimal Resolution**: 640x480 provides good balance of performance and accuracy
- **Lighting**: Natural daylight or bright, even lighting works best
- **Background**: Avoid complex patterns or moving objects
- **Hand Position**: Keep hands steady and within frame boundaries

## 🔒 Security Considerations

- **Camera Access**: Application requires webcam permissions
- **Mouse Control**: Grants system-level mouse control
- **Privacy**: Video feed is processed locally, not transmitted
- **Permissions**: Ensure proper access controls on your system

## 🤝 Contributing

1. **Fork the repository**
2. **Create a feature branch** (`git checkout -b feature/amazing-feature`)
3. **Commit your changes** (`git commit -m 'Add amazing feature'`)
4. **Push to the branch** (`git push origin feature/amazing-feature`)
5. **Open a Pull Request**

### Development Areas

- **Gesture Recognition**: Add more hand gestures and actions
- **Performance**: Optimize tracking algorithms
- **UI Enhancement**: Improve visual feedback and controls
- **Accessibility**: Add features for users with disabilities

## 🙏 Acknowledgments

- **MediaPipe** for hand tracking and landmark detection
- **OpenCV** for computer vision operations
- **Autopy** for cross-platform mouse control
- **Google Research** for MediaPipe framework

## 📞 Support

For questions, issues, or contributions:
- **Open an issue** on GitHub
- **Check troubleshooting** section above
- **Review code comments** for implementation details
- **Test with different setups** for compatibility

## 🔮 Future Enhancements

- [ ] **Multi-hand Support**: Track and use both hands
- [ ] **Advanced Gestures**: Scroll, drag, right-click, etc.
- [ ] **Customizable Controls**: User-defined gesture mappings
- [ ] **Machine Learning**: Improved gesture recognition
- [ ] **Mobile Support**: Android/iOS applications
- [ ] **API Integration**: Support for other applications
- [ ] **Gesture Recording**: Learn and replay custom gestures
- [ ] **Accessibility Features**: Voice commands and haptic feedback

## 🎯 Use Cases

- **Presentations**: Control slides without physical devices
- **Gaming**: Alternative input method for certain games
- **Accessibility**: Assist users with motor impairments
- **Productivity**: Hands-free computer navigation
- **Education**: Interactive learning environments
- **Healthcare**: Sterile environment computer control

---

**Transform your hand into a virtual mouse! 🖱️✋✨**
