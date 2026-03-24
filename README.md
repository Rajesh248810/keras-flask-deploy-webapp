# Image Classification Web App

[![Python 3.9+](https://img.shields.io/badge/python-3.9+-blue.svg)](https://www.python.org/downloads/)
[![TensorFlow 2.x](https://img.shields.io/badge/tensorflow-2.x-orange.svg)](https://www.tensorflow.org/)
[![Flask](https://img.shields.io/badge/flask-2.0+-green.svg)](https://flask.palletsprojects.com/)
[![Docker](https://img.shields.io/badge/docker-ready-blue.svg)](https://www.docker.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A production-ready, minimalist web application template for deploying deep learning image classification models. Built with Flask and TensorFlow/Keras, this solution enables rapid deployment of pre-trained architectures (VGG, ResNet, DenseNet) or custom-trained models through an intuitive, responsive web interface.

**Maintained by:** [GYANARANJAN SAHOO](https://github.com/gyanaranjansahoo)

---

## Features

- **🚀 Rapid Deployment**: Deploy trained models or industry-standard architectures (VGG16, ResNet50, DenseNet121) within minutes
- **📱 Responsive Interface**: Mobile-first design with touch-friendly drag-and-drop functionality
- **⚡ Lightweight Frontend**: Built with vanilla JavaScript, HTML5, and CSS3—no jQuery or Bootstrap dependencies
- **🐳 Containerized**: Docker-ready configuration for consistent cross-platform deployment
- **🔧 Modern Backend**: TensorFlow 2.x and tf.keras integration with Python 3.11+ support
- **🎯 Flexible Input**: Support for JPEG, PNG, and WebP formats with automatic preprocessing
- **📊 RESTful API**: Programmatic access via JSON endpoints for integration with external systems

---

## Installation

### Prerequisites

- Python 3.9 or higher
- pip package manager
- Docker (optional, for containerized deployment)

### Option 1: Docker Deployment (Recommended)

Deploy instantly using the pre-built container:

```bash
docker run --rm -p 5000:5000 ghcr.io/gyanaranjansahoo/image-classifier-flask:latest
```

Navigate to `http://localhost:5000` to access the application.

### Option 2: Manual Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/gyanaranjansahoo/image-classifier-flask.git
   cd image-classifier-flask
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

4. **Configure model**
   - Place your trained model file (`.h5` or SavedModel format) in the `models/` directory
   - Update class labels in `labels.txt` (one label per line)
   - Modify `config.py` to match your model's input specifications

---

## Usage

### Starting the Application

**Development Server:**
```bash
python app.py
```

**Production Server (Gunicorn):**
```bash
gunicorn -w 4 -b 0.0.0.0:5000 app:app
```

Access the interface at `http://localhost:5000`.

### Web Interface

1. **Upload**: Drag and drop an image or click the upload area to browse files
2. **Analysis**: The model automatically processes the image and displays:
   - Predicted class with confidence percentage
   - Top-5 probability distribution (for multi-class models)
   - Processing time metrics

### API Integration

**Endpoint:** `POST /predict`

**Request:**
```bash
curl -X POST -F "file=@image.jpg" http://localhost:5000/predict
```

**Response:**
```json
{
  "success": true,
  "predictions": [
    {"label": "golden_retriever", "probability": 0.987},
    {"label": "labrador", "probability": 0.008}
  ],
  "processing_time": "0.042s"
}
```

### Supported Models

- **Pre-trained**: VGG16, VGG19, ResNet50, ResNet101, DenseNet121, DenseNet169, MobileNetV2
- **Custom**: Any Keras/TensorFlow model exported in `.h5` or SavedModel format

---

<p align="center">
  <img src="./docs/screenshot.avif" alt="Application Interface" width="700"/>
  <br>
  <em>Clean, responsive interface optimized for desktop and mobile devices</em>
</p>

---

**Author:** GYANARANJAN SAHOO  
**Contributions:** Issues and pull requests are welcome  
**License:** MIT

---

### Maintenance
Maintained and optimized by **GYANARANJAN SAHOO**. Focus: Performance enhancements and stability updates.
