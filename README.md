# Musical Note Identification and Emotion-based Music Generation using DeepLearning

This repository contains the code for a project that analyzes uploaded audio (from an MP3 file or YouTube URL) to identify its musical composition. It then leverages two specially trained LSTM neural networks—one for "happy" music and one for "sad" music—to generate new, original piano pieces in a selected emotional style.

The project demonstrates a complete workflow, from initial audio processing and note extraction to training deep learning models and generating new musical content.

---

## 📜 Table of Contents

- [About The Project](#about-the-project)
- [✨ Key Features](#-key-features)
- [⚙️ How It Works](#️-how-it-works)
- [🛠️ Technologies Used](#️-technologies-used)
- [🚀 Getting Started: How to Run](#-getting-started-how-to-run)
  - [Prerequisites](#prerequisites)
  - [Setup Instructions](#setup-instructions)
  - [Training The Models (Optional)](#training-the-models-optional)
  - [Running the Music Generation Application](#running-the-music-generation-application)
- [🧠 Model Architecture](#-model-architecture)
- [🎵 Dataset](#-dataset)

---

## About The Project

The goal of this project is to explore the intersection of music, emotion, and artificial intelligence. By training separate deep learning models on music explicitly labeled as "happy" or "sad," the system learns the unique melodic patterns and structures associated with each emotion. The final application serves as an interactive tool where a user can provide any piece of music and use it as an inspirational seed to generate brand new, emotionally-targeted compositions.

---

## ✨ Key Features

-   **Flexible Audio Input:** Accepts music from user-uploaded MP3 files or any YouTube URL.
-   **Note & Tempo Identification:** Automatically processes raw audio, converts it to MIDI, and extracts its musical notes and tempo.
-   **Dual Emotion Models:** Utilizes two distinct LSTM models, one trained exclusively on "happy" music and the other on "sad" music from the EMOPIA dataset.
-   **AI-Powered Music Generation:** Generates new, original piano melodies that reflect the emotional style of the chosen model.
-   **Comprehensive Output:** Produces both a playable audio file (WAV) and the corresponding sheet music (PDF) for the generated piece.

---

## ⚙️ How It Works

The application follows a sequential pipeline to go from raw audio to a new musical creation:

1.  **User Input:** The user chooses to either upload an MP3 file or provide a YouTube URL.
2.  **Audio Processing:** The system downloads the audio (if from YouTube) and converts the MP3 file into a WAV format.
3.  **WAV to MIDI Conversion:** The WAV audio is analyzed to detect note onsets, pitches, and tempo, which are then used to construct a MIDI file.
4.  **Emotion Selection:** The user selects whether they want to generate "happy" or "sad" music.
5.  **Model Loading:** The appropriate pre-trained model (`happy_model.keras` or `sad_model.keras`) and its metadata are loaded.
6.  **Music Generation:** The model generates a new sequence of musical notes, with tempo and note duration adjusted to match the chosen emotion.
7.  **Final Output:** The generated notes are converted into a final MIDI file, which is then synthesized into a playable WAV audio file. A PDF of the sheet music is also created and provided for download.

---

## 🛠️ Technologies Used

-   **Deep Learning:** TensorFlow & Keras
-   **Music & Audio Processing:** `music21`, `librosa`, `pretty_midi`
-   **Audio Handling:** `pydub`, `yt-dlp`
-   **Data Science:** `numpy`, `pandas`, `scikit-learn`
-   **Environment:** Google Colab

---

## 🚀 Getting Started: How to Run

This project is designed to be run in a Google Colab environment.

### Prerequisites

1.  A **Google Account** to use Google Drive and Colab.
2.  The **EMOPIA Dataset**. You can download it from the official source: [EMOPIA Dataset](https://www.upf.edu/web/mtg/emopia)

### Setup Instructions

1.  **Create a Project Folder in Google Drive:**
    -   In your Google Drive, create a new folder named `emopia_project`.

2.  **Upload the Dataset:**
    -   Upload the downloaded `EMOPIA_1.0.zip` file into the `emopia_project` folder.

3.  **Upload the Notebooks:**
    -   Upload the three Jupyter Notebook files from this repository into your main Google Drive directory (or inside `emopia_project`):
        -   `Happy_Model.ipynb`
        -   `Sad_Model.ipynb`
        -   `Music Generation.ipynb`

### Training The Models (Optional)

If you wish to train the models from scratch:

1.  Open `Happy_Model.ipynb` in Google Colab. Run all the cells. This will train the happy model and save `happy_model.keras` and `happy_metadata.pkl` to your `emopia_project` folder.
2.  Open `Sad_Model.ipynb` in Google Colab. Run all the cells. This will train the sad model and save `sad_model.keras` and `sad_metadata.pkl` to your `emopia_project` folder.

**Note:** You must have the trained models (`.keras` files) and metadata (`.pkl` files) in your `emopia_project` folder before running the final application. You can either train them yourself or find pre-trained versions.

### Running the Music Generation Application

1.  Open `Music Generation.ipynb` in Google Colab.
2.  Run the cells in order. The notebook will guide you through:
    -   Mounting your Google Drive.
    -   Loading the trained models.
    -   Prompting you to provide a YouTube URL or upload an MP3 file.
    -   Asking you to choose an emotion ("happy" or "sad").
3.  After the generation is complete, the notebook will display a playable audio player and provide a download link for the sheet music.

---

## 🧠 Model Architecture

Both the happy and sad models use the same Long Short-Term Memory (LSTM) network architecture:

-   **LSTM Layer 1:** 256 units, returns sequences.
-   **Dropout Layer 1:** 30% dropout rate to prevent overfitting.
-   **LSTM Layer 2:** 256 units.
-   **Dropout Layer 2:** 30% dropout rate.
-   **Dense Output Layer:** A fully connected layer with a `softmax` activation function, producing a probability distribution over all unique notes in the vocabulary.

The model is compiled with the `adam` optimizer and `categorical_crossentropy` loss function.

---

## 🎵 Dataset

This project uses the **EMOPIA Dataset**, a shared multi-modal (audio and MIDI) database for emotion analysis in piano music. The dataset contains 1,087 music clips from 387 piano solos, with emotion labels based on a 4-quadrant emotion model.

---

