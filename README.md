# Sentiment Analysis with BERT

This project demonstrates how to create a sentiment analysis model using BERT, Flask, and a dataset from Kaggle. The model can predict the sentiment (positive or negative) of given text inputs.

## Table of Contents

- [Overview](#overview)
- [Setup](#setup)
- [Running the App](#running-the-app)
- [API Endpoints](#api-endpoints)
- [Frontend](#frontend)
- [References](#references)

## Overview

This project includes:
1. Training a sentiment analysis model using BERT.
2. Serving the model via a Flask web application.
3. A simple web interface for users to input text and receive sentiment predictions.

## Setup

### Prerequisites

- Python 3.6 or higher
- pip (Python package installer)
- Kaggle API credentials (`kaggle.json`)

### Install Dependencies

1. Clone this repository:

```bash
git clone https://github.com/yourusername/sentiment-analysis.git
cd sentiment-analysis
```
2. Install the required Python packages:
```bash
pip install transformers torch pandas sklearn flask
```
## Download the Dataset
1. Upload your kaggle.json file to the project directory.

2. Run the following commands to download and unzip the dataset:

```bash
mkdir -p ~/.kaggle
cp kaggle.json ~/.kaggle/
chmod 600 ~/.kaggle/kaggle.json

kaggle datasets download -d kazanova/sentiment140
unzip sentiment140.zip
```
## Train the Model
Train the model using the provided Jupyter notebook (you can use Google Colab for this step). Save the trained model weights as ` path_to_your_trained_model.pth`

## Save the Trained Model
Save the model state dict as ` path_to_your_trained_model.pth`:

```
torch.save(model.state_dict(), 'path_to_your_trained_model.pth')
```
