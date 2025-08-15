# Basic Security Camera

A simple motion detection security camera system built with Python and OpenCV. This application monitors your webcam feed in real-time and triggers audio alerts when motion is detected.

## Features

- **Real-time Motion Detection**: Continuously monitors webcam feed for movement
- **Audio Alerts**: Plays beep sound when motion is detected
- **Visual Display**: Shows the processed threshold image for monitoring
- **Configurable Sensitivity**: Adjustable motion detection threshold
- **Lightweight**: Minimal resource usage with efficient frame processing

## Requirements

### Hardware
- Webcam or built-in camera
- Speakers or audio output device
- Windows operating system (for `winsound` module)

### Software Dependencies
```
opencv-python>=4.5.0
```

## Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/naakaarafr/Basic-Security-Camera.git
   cd Basic-Security-Camera
   ```

2. **Install required packages**
   ```bash
   pip install opencv-python
   ```

3. **Ensure your webcam is connected** and accessible

## Usage

Run the security camera application:

```bash
python security_cam.py
```

### Controls
- **ESC key**: Exit the application
- The application will automatically start monitoring for motion

### How It Works

1. **Frame Capture**: The system captures two consecutive frames from the webcam
2. **Difference Detection**: Calculates the absolute difference between frames
3. **Image Processing**: Converts to grayscale and applies binary threshold
4. **Motion Analysis**: Finds contours in the processed image
5. **Alert System**: Triggers audio alert for significant motion (contour area > 1000 pixels)
6. **Display**: Shows the processed binary image for visual monitoring

## Configuration

You can modify these parameters in `security_cam.py`:

- **Motion Sensitivity**: Change `cv2.contourArea(c) < 1000` threshold value
  - Lower values = more sensitive (detects smaller movements)
  - Higher values = less sensitive (detects only larger movements)

- **Threshold Value**: Modify `cv2.threshold(gray,20,255,cv2.THRESH_BINARY)`
  - Adjust the `20` value to change motion detection sensitivity
  - Lower values detect smaller changes, higher values require more significant changes

- **Audio Alert**: Customize `winsound.Beep(500,100)`
  - First parameter: frequency in Hz
  - Second parameter: duration in milliseconds

## Troubleshooting

### Common Issues

**Camera not detected**
- Ensure your webcam is properly connected
- Try changing `cv2.VideoCapture(0)` to `cv2.VideoCapture(1)` or higher numbers
- Check if other applications are using the camera

**No audio alerts**
- Verify speakers/audio output is working
- Check system volume settings
- On non-Windows systems, replace `winsound` with alternative audio libraries

**High CPU usage**
- Reduce frame processing by adding delays
- Lower the camera resolution if possible
- Adjust the motion detection threshold to reduce false positives

## Platform Compatibility

- **Windows**: Fully supported (uses `winsound` for audio)
- **Linux/macOS**: Requires modification to replace `winsound` with alternative audio library like `pygame` or `playsound`

### Cross-platform Audio Alternative

For Linux/macOS compatibility, replace the audio alert section:

```python
# Replace winsound.Beep(500,100) with:
import os
os.system('echo -e "\a"')  # System beep

# Or use pygame for better audio control:
# import pygame
# pygame.mixer.init()
# pygame.mixer.Sound('alert.wav').play()
```

## Future Enhancements

- [ ] Video recording when motion is detected
- [ ] Email/SMS notifications
- [ ] Web interface for remote monitoring
- [ ] Multiple camera support
- [ ] Motion detection zones
- [ ] Timestamp logging
- [ ] Cross-platform audio support

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-feature`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/new-feature`)
5. Create a Pull Request

## License

This project is open source. Feel free to use, modify, and distribute as needed.

## Contact

For questions, issues, or suggestions, please open an issue on the [GitHub repository](https://github.com/naakaarafr/Basic-Security-Camera).

---

**⚠️ Note**: This is a basic implementation intended for educational purposes and simple monitoring. For production security systems, consider more robust solutions with proper authentication, encryption, and professional monitoring capabilities.
