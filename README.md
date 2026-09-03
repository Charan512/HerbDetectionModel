# Herb Identification System

A web-based herb identification system using Deep Learning (EfficientNetV2B3 + PCA + SVM) with a FastAPI backend and modern HTML/CSS/JavaScript frontend.

## Model Architecture

- **Feature Extractor**: EfficientNetV2B3 (pre-trained on ImageNet)
- **Dimensionality Reduction**: PCA (1024 components)
- **Classifier**: SVM with RBF kernel
- **Accuracy**: 95.92% on validation set
- **Classes**: 92 different herb/plant species

## Features

- 🌿 Identify 92 different herb and plant species
- 📸 Drag-and-drop or click to upload images
- 🎨 Modern, responsive UI with animations
- ⚡ Fast predictions using pre-trained models
- 📊 Real-time confidence scores

## Installation

### Quick Setup (Recommended)

1. **Navigate to the repository**:
   ```bash
   cd /Users/<USER_NAME>/HerbIdentificationModel
   ```

2. **Run the setup script**:
   ```bash
   ./setup.sh
   ```
   
   This will:
   - Create a virtual environment
   - Install all required dependencies
   - Set up the project

### Manual Setup

If you prefer to install manually:

```bash
cd /Users/<USER_NAME>/HerbIdentificationModel
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

## Usage

### Quick Start

1. **Run the application**:
   ```bash
   ./run.sh
   ```

2. **Open your browser** and navigate to:
   ```
   http://localhost:8000
   ```

3. **Upload an image** of a herb or plant and click "Identify Herb" to get the prediction!

### Manual Start

If you set up manually:

```bash
source venv/bin/activate
python app.py
```

Or using uvicorn directly:
```bash
uvicorn app:app --host 0.0.0.0 --port 8000 --reload
```

## API Endpoints

### 1. Home Page
- **GET** `/`
- Returns the HTML interface

### 2. Predict
- **POST** `/predict`
- Upload an image file to get herb identification
- **Request**: Multipart form data with image file
- **Response**:
  ```json
  {
    "prediction": "Ocimum tenuiflorum (Tulsi)",
    "class_index": 59,
    "confidence": 0.95
  }
  ```

### 3. Get Classes
- **GET** `/classes`
- Returns list of all available herb classes
- **Response**:
  ```json
  {
    "classes": ["Allium cepa (Onion)", ...],
    "total": 92
  }
  ```

### 4. Health Check
- **GET** `/health`
- Check if the API is running and models are loaded
- **Response**:
  ```json
  {
    "status": "healthy",
    "models_loaded": true
  }
  ```

## Model Files

The following files are required for the application to work:

- `feature_extractor.keras` - EfficientNetV2B3 feature extraction model
- `pca.pkl` - PCA transformation model
- `svm_model.pkl` - SVM classifier model
- `class_names.json` - List of 92 herb/plant class names

## Supported Plants/Herbs

The system can identify 92 different species including:
- Tulsi (Holy Basil)
- Neem
- Aloe Vera
- Turmeric
- Ginger
- Mint
- And 86 more species!

## Technical Details

### Image Processing
- Input size: 300x300 pixels
- Preprocessing: EfficientNetV2 preprocessing
- Supported formats: JPG, PNG, JPEG

### Model Pipeline
1. Image is resized to 300x300
2. EfficientNetV2B3 extracts features (1536 dimensions)
3. PCA reduces dimensions to 1024
4. SVM classifier predicts the species

## Requirements

- Python 3.8+
- TensorFlow 2.15.0
- FastAPI 0.104.1
- See `requirements.txt` for full list

## License

This project is for educational purposes.

## Acknowledgments

- Model trained on Herbify Dataset
- Uses EfficientNetV2B3 architecture
- Built with FastAPI and modern web technologies
