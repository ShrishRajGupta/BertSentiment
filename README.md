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
``` bash
pip install transformers torch pandas sklearn flask
```
## Download the Dataset
1. Upload your kaggle.json file to the project directory.

2. Run the following commands to download and unzip the dataset:

``` python
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

``` python
torch.save(model.state_dict(), 'path_to_your_trained_model.pth')
```
### Configure Flask App
Ensure the path to the trained model in app.py matches the location where you saved the model weights.
``` python
model.load_state_dict(torch.load('path_to_your_trained_model.pth', map_location=torch.device('cpu')))
```
## Running the App
1. Start the Flask app:
``` bash
python app.py
```
2. Open a web browser and navigate to `http://localhost:5000` to access the web interface.

## API Endpoints

### Health Check
**URL**: _/health_

**Method**: _GET_

**Description**: Checks if the server is running.

**Response**: 
``` json
{"status": "healthy"}
```

### Single Prediction

**URL**: _/predict_

**Method**: _POST_

**Description**: Predicts sentiment for a single text input.

**Request**
``` json
{
  "text": "I love this product!"
}
```

**Response**
``` json
{
  "text": "I love this product!",
  "label": "positive"
}
```

## Frontend
A simple HTML form is provided for user input:

- **URL**: /

- **Method**: GET

- **Description**: Displays a form for text input and shows the predicted sentiment.

## References
- [Transformers Library by Hugging Face](https://huggingface.co/docs/transformers/en/index)

- [Flask Web Framework](https://flask.palletsprojects.com/en/3.0.x/)

- [Kaggle Sentiment140 Dataset](https://www.kaggle.com/datasets/kazanova/sentiment140)


