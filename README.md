# Drowsiness Detection System

A real-time drowsiness detection system that monitors driver alertness using computer vision and sends email alerts when drowsiness is detected.

## Features

- Real-time face detection and eye tracking
- Drowsiness detection using Eye Aspect Ratio (EAR)
- Audio alerts when drowsiness is detected
- Email notifications to multiple recipients
- Visual feedback with OpenCV
- Easy-to-configure alert thresholds

## Requirements

- Python 3.x
- OpenCV (`cv2`)
- dlib
- imutils
- scipy
- pygame
- numpy

## Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/drowsiness-detection.git
cd drowsiness-detection
```

2. Install the required packages:
```bash
pip install opencv-python dlib imutils scipy pygame
```

3. Download the shape predictor file:
- Download `shape_predictor_68_face_landmarks.dat` from [dlib's model repository](http://dlib.net/files/shape_predictor_68_face_landmarks.dat.bz2)
- Extract and place it in the `models` directory

4. Add your alert sound:
- Place your alert sound file (WAV format) in the project directory
- Name it `music.wav`

## Configuration

Update the email configuration in the script with your details:

```python
email_sender = 'your-email@gmail.com'
email_password = 'your-app-specific-password'
email_receivers = ['recipient1@email.com', 'recipient2@email.com']
```

Note: For Gmail, you'll need to use an App-Specific Password. Two-factor authentication must be enabled to generate one.

## Usage

1. Run the script:
```bash
python drowsiness_detection.py
```

2. The system will:
- Access your webcam
- Monitor your eyes in real-time
- Display the video feed with eye tracking
- Trigger alerts if drowsiness is detected
- Send email notifications to configured recipients

3. Press 'q' to quit the application

## How It Works

1. **Face Detection**: Uses dlib's frontal face detector to locate faces in the video stream

2. **Facial Landmarks**: Applies the shape predictor to detect 68 facial landmarks

3. **Eye Tracking**: 
   - Extracts eye regions using facial landmarks
   - Calculates Eye Aspect Ratio (EAR) for both eyes
   - Monitors EAR values to detect drowsiness

4. **Alert System**:
   - Triggers when EAR falls below threshold for specified frames
   - Plays audio alert
   - Sends email notifications
   - Displays visual warning on screen

## Customization

You can adjust these parameters in the code:
- `thresh`: EAR threshold (default: 0.25)
- `frame_check`: Number of consecutive frames required to trigger alert (default: 20)

