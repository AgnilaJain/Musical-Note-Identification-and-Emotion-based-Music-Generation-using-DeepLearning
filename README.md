# Musical-Note-Identification-and-Emotion-based-Music-Generation-using-DeepLearning
This repository contains the code for a project that analyzes uploaded audio (from an MP3 file or YouTube URL) to identify its musical composition. It then leverages two specially trained LSTM neural networks—one for "happy" music and one for "sad" music—to generate new, original piano pieces in a selected emotional style.
The project demonstrates a complete workflow, from initial audio processing and note extraction to training deep learning models and generating new musical content.
Key Features:
Flexible Audio Input: Accepts user-uploaded MP3 files or links to YouTube videos.
Dual Emotion Models: Utilizes two distinct LSTM models trained on the EMOPIA dataset, one for generating happy melodies and another for sad ones.
AI-Powered Music Generation: Creates original musical sequences based on the patterns learned by the neural networks.
Comprehensive Output: Produces both a playable audio file and the corresponding sheet music for the generated piece.
Core Technologies:
Deep Learning: TensorFlow and Keras
Music & Audio Processing: music21, librosa, pretty_midi
Data Handling: pydub, yt-dlp, numpy
This entire project is designed to run within a Google Colab environment, with dependencies and setup instructions included.
