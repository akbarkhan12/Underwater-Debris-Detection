# AquaVision: Marine Debris Detection System

![AquaVision Logo](https://img.shields.io/badge/AquaVision-Marine%20Debris%20Detection-blue?style=for-the-badge&logo=python)
![YOLO](https://img.shields.io/badge/Model-YOLOv8%2FYOLOv10-green?style=flat-square)
![Flask](https://img.shields.io/badge/Framework-Flask-orange?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-red?style=flat-square)

A comprehensive web-based application for detecting and classifying marine debris in underwater environments using advanced computer vision techniques. Built with YOLO (You Only Look Once) object detection models and a modern Flask web interface.

## 🌊 Project Overview

Marine pollution poses a significant threat to ocean ecosystems worldwide. AquaVision provides an automated solution for identifying and categorizing underwater debris, enabling researchers, environmental agencies, and conservation organizations to monitor and address marine pollution more effectively.

### Key Features

- **Real-time Object Detection**: Upload images or videos for instant debris detection
- **Multi-class Classification**: Identifies 10 different types of marine debris
- **Web-based Interface**: User-friendly web application with modern UI
- **Video Processing**: Support for video analysis with frame-by-frame detection
- **Performance Analytics**: Built-in charts and metrics visualization
- **User Authentication**: Secure login and registration system
- **High Accuracy**: Trained on comprehensive underwater dataset

## 🏗️ Architecture

```
├── app.py                 # Main Flask application
├── best.pt               # Trained YOLO model weights
├── data.yaml            # Dataset configuration
├── requirements.txt     # Python dependencies
├── static/              # Web assets (CSS, JS, images)
├── templates/           # HTML templates
├── uploads/             # User uploaded files
├── results/             # Detection results
├── train/               # Training dataset
├── valid/               # Validation dataset
└── test/                # Test dataset
```

## 📊 Dataset

The model is trained on the **Underwater Object Detection** dataset from Roboflow Universe:

- **Source**: [Roboflow Universe](https://universe.roboflow.com/underwater-ztbtg/underwater-object-detection-5xmdy)
- **Images**: 1,112 annotated images
- **Format**: YOLOv8 annotation format
- **Resolution**: 640x640 pixels
- **Classes**: 10 marine debris categories

### Object Classes

1. **Accessories** - Personal items like jewelry, watches
2. **Cutlery** - Kitchen utensils and tools
3. **Glass** - Glass bottles and containers
4. **Litter** - General waste and trash
5. **Metal** - Metal objects and cans
6. **Natural-Debris** - Organic materials
7. **Plastic** - Plastic waste and containers
8. **Rope** - Ropes and cords
9. **Rubber** - Rubber items and tires
10. **Wood** - Wooden objects and debris

## 🚀 Installation

### Prerequisites

- Python 3.8 or higher
- FFmpeg (for video processing)
- Git

### Step-by-Step Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd MARINE
   ```

2. **Create virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Update dataset paths** (if necessary)
   Edit `data.yaml` to point to correct dataset locations:
   ```yaml
   train: ./train/images
   val: ./valid/images
   test: ./test/images
   ```

5. **Run the application**
   ```bash
   python app.py
   ```

6. **Access the web interface**
   Open your browser and navigate to `http://localhost:5002`

## 🎯 Usage

### Web Interface

1. **Registration/Login**: Create an account or login to access the system
2. **Upload Media**:
   - **Images**: Upload JPEG/PNG images for instant detection
   - **Videos**: Upload MP4/AVI/MOV videos for frame-by-frame analysis
3. **View Results**: See annotated images/videos with detected debris highlighted
4. **Performance Dashboard**: Monitor detection metrics and analytics

### API Endpoints

- `GET /` - Home page
- `GET /index` - Main dashboard
- `POST /upload` - Upload and process media files
- `GET /performance` - Performance metrics
- `GET /chart` - Analytics charts

## 🧠 Model Training

### Training Setup

The model was trained using Ultralytics YOLOv8/YOLOv10 framework with the following configuration:

```python
from ultralytics import YOLO

# Load pre-trained model
model = YOLO('yolov8n.pt')  # or yolov10n.pt

# Train the model
model.train(
    data='data.yaml',
    epochs=100,
    imgsz=640,
    batch=16,
    name='marine_debris_detection'
)
```

### Training Results

The model achieved the following performance metrics:

- **mAP@50**: 0.357 (35.7% mean Average Precision at IoU 0.5)
- **mAP@50-95**: 0.184 (18.4% mean Average Precision across IoU 0.5-0.95)
- **Precision**: 0.398 (39.8%)
- **Recall**: 0.431 (43.1%)

Training progress and metrics are logged in `results.csv` and visualization plots are available in the `runs/` directory.

## 🔧 Configuration

### Model Configuration

- **Model**: YOLOv8n / YOLOv10n (nano variants for efficiency)
- **Input Size**: 640x640 pixels
- **Confidence Threshold**: 0.25 (default)
- **IoU Threshold**: 0.45 (default)

### Application Settings

Key settings in `app.py`:

```python
UPLOAD_FOLDER = 'uploads'      # Upload directory
RESULTS_FOLDER = 'results'     # Results directory
model = YOLO('best.pt')        # Model weights path
app.secret_key = 'your-secret-key'  # Flask secret key
```

## 📈 Performance Analysis

The application includes comprehensive performance tracking:

- **Detection Accuracy**: Real-time metrics for each detection
- **Processing Speed**: Frame processing time for videos
- **Model Metrics**: Training and validation performance
- **User Analytics**: Upload statistics and usage patterns

Access performance data through:
- `/performance` - Detailed metrics dashboard
- `/chart` - Visual analytics and charts
- `results.csv` - Raw training data

## 🛠️ Technologies Used

- **Backend**: Python Flask
- **AI/ML**: Ultralytics YOLOv8/YOLOv10
- **Computer Vision**: OpenCV
- **Frontend**: HTML5, CSS3, JavaScript
- **Styling**: Bootstrap, Font Awesome
- **Video Processing**: FFmpeg
- **Data Visualization**: Chart.js (integrated in templates)

## 🤝 Contributing

We welcome contributions to improve AquaVision! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Guidelines

- Follow PEP 8 style guidelines
- Add docstrings to new functions
- Update tests for new features
- Ensure compatibility with Python 3.8+

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Dataset**: Underwater Object Detection dataset from Roboflow Universe
- **Framework**: Ultralytics YOLO for object detection
- **Community**: Open-source computer vision community

## 📞 Contact

For questions, suggestions, or collaborations:

- **Project Lead**: [Your Name]
- **Email**: [your.email@example.com]
- **GitHub**: [your-github-username]
- **LinkedIn**: [your-linkedin-profile]

## 🔄 Future Enhancements

- [ ] Real-time video streaming detection
- [ ] Mobile application development
- [ ] Integration with drone footage
- [ ] Advanced analytics dashboard
- [ ] Multi-language support
- [ ] API endpoints for third-party integration
- [ ] Cloud deployment options

---

**Made with ❤️ for a cleaner ocean**

*Help us protect marine ecosystems by detecting and removing underwater debris!* 🐟🌊
