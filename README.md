# DeepShield


DeepShield is a deepfake detection project with a Chrome extension for analyzing video-call content and Python tools for image analysis. The extension captures video frames and sends them to a local backend for machine-learning inference.

## Features

- Captures frames from video elements on supported meeting pages.
- Sends frames to a local Node.js API for analysis.
- Uses a Python TensorFlow/Keras model for deepfake detection.
- Includes a React and Vite extension popup and a Streamlit image and live-detection dashboard.

## Technology

- Chrome Extension, Manifest V3, JavaScript
- React and Vite
- Node.js and Express
- Python, TensorFlow/Keras, OpenCV, and NumPy

## Project structure

```text
DeepShield/
+-- Code/                         # Python detection tools and Node.js backend
|   +-- app.py                    # Streamlit dashboard
|   +-- backgroundProcess.js      # Express API server
|   +-- predict.py                # Python inference worker
|   +-- requirements.txt          # Python dependencies
|   +-- train.py                  # Model training script
+-- DeepShield-extension/        # Chrome extension
    +-- content-script.js
    +-- manifest.json
    +-- frontend/                 # React/Vite popup
```

## Setup

### Python backend and dashboard

From the project root, create and activate a virtual environment, then install the Python dependencies:

```bash
cd Code
python -m venv venv
```

On Windows:

```powershell
venv\Scripts\Activate.ps1
```

On macOS or Linux:

```bash
source venv/bin/activate
```

Install dependencies and start the Streamlit dashboard:

```bash
pip install -r requirements.txt
streamlit run app.py
```

### Node.js API server

In another terminal, install the backend packages and start the API:

```bash
cd Code
npm install
node backgroundProcess.js
```

The server listens on `http://localhost:5000`.

### Chrome extension

Build the popup from the project root:

```bash
cd DeepShield-extension/frontend
npm install
npm run build
```

Then open `chrome://extensions` in Chrome, enable **Developer mode**, choose **Load unpacked**, and select the `DeepShield-extension` folder.

## Model and data

Place the trained model where the inference code expects it. Dataset files used for training and evaluation are not included in this repository. See the scripts in `Code/` for their expected model and dataset paths.
