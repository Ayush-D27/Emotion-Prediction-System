# Emotion Prediction System using Deep Learning

A deep learning-based Natural Language Processing (NLP) project that classifies text into six emotion categories using a **Bidirectional Gated Recurrent Unit (BiGRU)** neural network. The trained model is integrated with a FastAPI backend and a web interface for interactive emotion prediction.

## Overview

The Emotion Prediction System analyzes a user's text and predicts the emotion expressed in it. The project uses recurrent neural network architectures to learn contextual patterns in text and classify sentences into one of six emotion categories.

### Emotion Categories

- Sadness
- Joy
- Love
- Anger
- Fear
- Surprise

## Features

- Text preprocessing and normalization
- NLP tokenization and sequence padding
- Deep learning-based emotion classification using BiGRU
- Comparison of RNN, LSTM, and GRU-based models in the training notebook
- Prediction confidence and probability scores for all six emotions
- FastAPI backend for model inference
- Interactive frontend built with HTML, CSS, and JavaScript
- Health-check endpoint to check server status and model loading

## Tech Stack

| Category | Technologies |
|---|---|
| Programming Language | Python |
| NLP | Text preprocessing, tokenization, sequence padding |
| Deep Learning | TensorFlow, Keras, RNN, LSTM, GRU, BiGRU |
| Data Processing | NumPy, Pandas |
| Visualization and Evaluation | Matplotlib, Seaborn, Scikit-learn |
| Dataset Loading | Hugging Face Datasets |
| Backend | FastAPI, Uvicorn, Pydantic |
| Frontend | HTML5, CSS3, JavaScript |
| Model Storage | Keras model (`.keras`), Pickle tokenizer |

## Dataset

The project uses the **[Emotion Dataset by dair-ai on Hugging Face](https://huggingface.co/datasets/dair-ai/emotion)**.

The dataset contains text samples labelled with six emotions. It is used to train and evaluate deep learning models for emotion classification.

## Model Development

The Jupyter notebook, `final_clean.ipynb`, covers the model development workflow:

1. Load the emotion dataset.
2. Prepare training and testing data.
3. Preprocess text and convert words into numerical sequences.
4. Pad sequences to a fixed length of 50 tokens.
5. Train and compare recurrent neural network architectures, including RNN, LSTM, and GRU-based models.
6. Build and evaluate a Bidirectional GRU (BiGRU) model.
7. Evaluate predictions and inspect confusion matrices.
8. Save the trained model and tokenizer for deployment.

### Model Performance

The saved BiGRU model achieved the following results on the notebook's test evaluation:

| Metric | Result |
|---|---:|
| Test Accuracy | 92.65% |
| Test Loss | 0.1988 |

*These results reflect the evaluation recorded in the notebook and are not a guarantee of performance on every real-world text input.*

## Project Structure

```text
DL_Project/
│
├── Artifacts/
│   ├── BiGRU_Modle.keras
│   └── tokenizer.pkl
│
├── static/
│   ├── index.html
│   ├── script.js
│   └── style.css
│
├── final_clean.ipynb
├── main.py
├── README.md
└── .gitignore
```

**Note:** The model filename is `BiGRU_Modle.keras` in the current project files. The filename and path used in `main.py` must match exactly.

## Installation and Setup

### 1. Clone the repository

```bash
git clone https://github.com/Ayush-D27/Emotion-Prediction-System.git
cd Emotion-Prediction-System
```

### 2. Create and activate a virtual environment (optional but recommended)

Using Python:

```bash
python -m venv .venv
```

On Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

If you already have a working Conda environment with the required packages installed, you can use that environment instead.

### 3. Install dependencies

```bash
python -m pip install fastapi "uvicorn[standard]" tensorflow numpy pydantic
```

The notebook also uses packages such as:

```bash
python -m pip install pandas matplotlib seaborn scikit-learn datasets jupyter
```

## Running the Application

Make sure the model and tokenizer files exist inside the `Artifacts` folder and that the paths in `main.py` match their actual filenames.

From the project root directory, run:

```bash
python -m uvicorn main:app --reload
```

After the server starts, open:

**Web application:** http://127.0.0.1:8000

**API documentation:** http://127.0.0.1:8000/docs

**Health check:** http://127.0.0.1:8000/health

To stop the server, press `Ctrl + C` in the terminal.

## API Endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/` | Opens the web interface |
| GET | `/health` | Checks server status and model loading |
| POST | `/predict` | Predicts the emotion expressed in text |

### Example Prediction Request

Send a POST request to `/predict` with this JSON body:

```json
{
  "text": "I feel so happy and excited today!"
}
```

The API returns the original text, predicted emotion, confidence score, and probability scores for all six emotion categories.

## Future Improvements

- Add more diverse text samples to improve generalization.
- Evaluate precision, recall, macro F1-score, and class-wise performance.
- Improve handling of sarcasm, ambiguous sentences, and mixed emotions.
- Compare the BiGRU model with Transformer-based models such as BERT.
- Deploy the application to a cloud hosting platform.

## Author

**Ayush Deore**

GitHub: [Ayush-D27](https://github.com/Ayush-D27)

## Disclaimer

This project is intended for educational and research purposes. Predicted emotions are model estimates based on text patterns and should not be treated as definitive assessments of a person's emotional or mental state.
