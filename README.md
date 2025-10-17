# 🍅 Tomato Freshness Detector

An AI-powered web application that detects and classifies tomato freshness in real-time using deep learning and computer vision. The system can identify four different tomato states: **Ripe**, **Unripe**, **Old**, and **Damaged**.

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.10+-orange.svg)
![Flask](https://img.shields.io/badge/Flask-2.3+-green.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

## 🌟 Features

### 🎥 **Live Webcam Detection**
- Real-time tomato detection and classification
- Color-coded bounding boxes with confidence scores
- Automatic tomato segmentation using HSV color space
- Live status indicator

### 📤 **Image Upload Analysis**
- Drag-and-drop file upload support
- Batch detection of multiple tomatoes in one image
- Detailed results with position and confidence metrics
- Download processed images with annotations

### 🎨 **Modern Web Interface**
- Responsive dark-themed UI
- Smooth animations and transitions
- Mobile-friendly design
- Professional color-coding system:
  - 🟢 **Green**: Ripe (Perfect for consumption)
  - 🟠 **Orange**: Unripe (Needs more time)
  - 🟤 **Dark Orange**: Old (Past prime condition)
  - 🔴 **Red**: Damaged (Not suitable for sale)

### 🧠 **AI-Powered Detection**
- Deep learning model trained on tomato images
- High accuracy classification
- Confidence score for each prediction
- Robust to varying lighting conditions

## 🚀 Quick Start

### Prerequisites

- Python 3.8 or higher
- Webcam (optional, for live detection)
- pip package manager

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/amanbangeraa/tomatoFreshness.git
cd tomatoFreshness
```

2. **Install dependencies**
```bash
pip install -r requirements.txt
```

Or install individually:
```bash
pip install flask tensorflow opencv-python numpy pillow
```

3. **Run the application**
```bash
python app.py
```

4. **Open your browser**

Navigate to: `http://localhost:5000`

## 📁 Project Structure

```
tomatoFreshness/
├── app.py                          # Flask backend with AI processing
├── tomato_freshness_model.h5       # Pre-trained TensorFlow model
├── requirements.txt                # Python dependencies
├── README.md                       # Project documentation
├── run_app.sh                      # Shell script to run app
├── templates/
│   └── index.html                  # Main web interface
└── static/
    ├── css/
    │   └── style.css              # Modern dark theme styling
    └── js/
        └── app.js                 # Frontend interactivity
```

## 💻 Usage

### Web Interface

#### Mode 1: Live Webcam Detection
1. Click on **"Live Webcam"** tab
2. Allow camera access when prompted
3. Point your camera at tomatoes
4. View real-time detection with bounding boxes and labels

#### Mode 2: Upload Image
1. Click on **"Upload Image"** tab
2. Drag and drop an image or click to browse
3. Click **"Analyze Image"** button
4. View detailed results with all detected tomatoes

### API Endpoints

The application also provides REST API endpoints:

- `GET /` - Main web interface
- `GET /video_feed` - Video streaming endpoint
- `POST /analyze_image` - Analyze uploaded image
- `GET /camera_status` - Check camera availability

#### Example API Usage

```python
import requests

# Analyze an image
with open('tomato.jpg', 'rb') as f:
    files = {'image': f}
    response = requests.post('http://localhost:5000/analyze_image', files=files)
    results = response.json()
    print(results)
```

## 🔧 Configuration

### Model Details
- **Architecture**: Deep CNN (Convolutional Neural Network)
- **Input Size**: 224x224 pixels
- **Classes**: 4 (Damaged, Old, Ripe, Unripe)
- **Framework**: TensorFlow/Keras

### Detection Parameters
You can adjust detection sensitivity by modifying HSV color ranges in `app.py`:

```python
# Red tomato mask
lower_red1 = np.array([0, 120, 70])
upper_red1 = np.array([10, 255, 255])

# Green tomato mask
lower_green = np.array([35, 50, 50])
upper_green = np.array([90, 255, 255])
```

## 🛠️ Technical Stack

- **Backend**: Flask (Python web framework)
- **AI/ML**: TensorFlow, Keras
- **Computer Vision**: OpenCV
- **Frontend**: HTML5, CSS3, JavaScript
- **Styling**: Custom CSS with modern design principles
- **Image Processing**: NumPy, Pillow

## 📊 Model Performance

The classification model identifies tomatoes in four categories:

| Class | Description | Use Case |
|-------|-------------|----------|
| **Ripe** | Perfect ripeness | Ready for sale/consumption |
| **Unripe** | Not yet ripe | Need storage time |
| **Old** | Past prime | Discount/processing |
| **Damaged** | Physical damage | Reject/compost |

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 🐛 Known Issues & Troubleshooting

### Camera Not Working
- Ensure camera permissions are granted
- Check if camera is not being used by another application
- Try restarting the application

### Model Loading Error
- Verify `tomato_freshness_model.h5` exists in the project root
- Check TensorFlow version compatibility

### Port Already in Use
Change the port in `app.py`:
```python
app.run(debug=True, host='0.0.0.0', port=5001)  # Change 5000 to 5001
```

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 👏 Acknowledgments

- TensorFlow and Keras teams for the deep learning framework
- OpenCV community for computer vision tools
- Flask team for the web framework

## 📧 Contact

**Project Repository**: [https://github.com/amanbangeraa/tomatoFreshness](https://github.com/amanbangeraa/tomatoFreshness)

---

Made with ❤️ and 🍅 by [amanbangeraa](https://github.com/amanbangeraa)
