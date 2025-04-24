# Live Real-Time Sign Language & Numeric Gesture Recognition

## Description
This repository provides a complete pipeline for real-time sign language detection (alphabet) and numeric gesture recognition (numbers 0–9) using a webcam feed. It leverages the Sign Language MNIST dataset for alphabet gestures and a separate Kaggle dataset for numeric gestures, extracting hand landmarks via MediaPipe and training a Random Forest classifier on these features.

## Features
- **Real-time Webcam Detection**: Captures live video feed and predicts hand gestures on-the-fly.
- **Alphabet Recognition**: Supports detection of alphabet signs (A–Z) from the Sign Language MNIST dataset.
- **Numeric Gesture Recognition**: Recognizes hand signs for digits (0–9) from the "Sign Language for Numbers" dataset.
- **MediaPipe Hand Tracking**: Utilizes MediaPipe’s hand landmark model for robust hand posture extraction.
- **Random Forest Classifier**: Trains a Random Forest model on extracted landmarks for high-accuracy predictions.

## Datasets
- **Sign Language MNIST**: Alphabet dataset of hand images labeled A–Z. Source: [Kaggle Sign Language MNIST](https://www.kaggle.com/datasets/datamunge/sign-language-mnist)
- **Sign Language for Numbers**: Numeric gesture dataset for digits 0–9. Source: [Kaggle Sign Language for Numbers](https://www.kaggle.com/datasets/muhammadkhalid/sign-language-for-numbers)

## Project Structure
```
├── data/                   # Extracted dataset images organized by label
├── scripts/                # Python scripts for data extraction, training, and detection
│   ├── create_dataset.py    # Extract hand landmarks into data.pickle
│   ├── train_classifier.py          # Train Random Forest and save model.p
│   └── inference_classifier.py      # Run live detection on webcam
├── model.p                 # Trained Random Forest model pickle file
├── data.pickle             # Landmark features and labels
├── requirements.txt        # Python dependencies
└── README.md               # Project documentation
```

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/tahangz/Real-Time-Sign-Language-Numeric-Gesture-Recognition.git
   cd Real-Time-Sign-Language-Numeric-Gesture-Recognition
   ```
2. Create and activate a virtual environment (optional but recommended):
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

### 1. Extract Hand Landmarks
Run the landmark extraction script to process images and save features:
```bash
python scripts/extract_landmarks.py --data_dir ./data --output data.pickle
```

### 2. Train the Model
Train the Random Forest classifier using the extracted features:
```bash
python scripts/train_model.py --input data.pickle --output model.p
```

### 3. Real-Time Detection
Launch live detection via your webcam:
```bash
python scripts/detect_realtime.py --model model.p
```

## Dependencies
- Python 3.7+
- OpenCV (`cv2`)
- MediaPipe
- scikit-learn
- NumPy
- Matplotlib

All dependencies are listed in `requirements.txt`.

## Contributing
Contributions are welcome! Please open an issue or submit a pull request for bug fixes and improvements.


