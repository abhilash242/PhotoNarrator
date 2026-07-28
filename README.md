# PhotoNarrator — Automated Image Captioning

Photo Narrator is a Flask web application that generates a short text caption for an uploaded image. It extracts visual features with a pre-trained ResNet50 model and uses a trained image-captioning network to predict a caption word by word.

## Team

- Abhilash Mohan Das
- Medha Hegde

## Features

- Upload an image from the browser
- Generate an automated caption for the uploaded image
- Display the uploaded image and its predicted caption
- Uses a pre-trained ResNet50 model for image feature extraction

## Project structure

```text
Photo-narrator/
├── app.py                  # Flask application and caption-generation logic
├── mine_model_weights.h5   # Trained captioning-model weights
├── vocab.npy               # Vocabulary used by the captioning model
├── static/
│   └── file.jpg            # Latest uploaded image (created/replaced at runtime)
└── templates/
    ├── base.html           # Shared page layout
    ├── index.html          # Image-upload page
    └── after.html          # Caption result page
```

## Requirements

- Python 3.8 or later
- Flask
- TensorFlow / Keras
- NumPy
- OpenCV
- tqdm

Install the required packages:

```bash
pip install flask tensorflow numpy opencv-python tqdm
```

> The application uses pre-trained ImageNet weights for ResNet50. TensorFlow may download these weights the first time the app runs.

## Run the application

1. Open a terminal in the project folder.
2. Install the requirements.
3. Start the Flask app:

```bash
python app.py
```

4. Open the address shown in the terminal, normally `http://127.0.0.1:5000/`.
5. Select an image and click **Predict Caption**.

## How it works

1. The user uploads an image through the web page.
2. The app resizes the image to 224 × 224 pixels.
3. ResNet50 converts the image into a 2,048-value feature vector.
4. The captioning model combines the image features with previously predicted words.
5. It predicts the next word repeatedly to form an image caption.

## Notes

- The model predicts up to 20 words for each image.
- Uploaded images are saved as `static/file.jpg`, so a new upload replaces the previous one.
- Caption quality depends on the training data and the uploaded image.

## Technologies used

- Python
- Flask
- TensorFlow / Keras
- ResNet50
- OpenCV
- Bootstrap

## Future improvements

- Show a preview before caption generation
- Use a unique filename for every upload instead of replacing `static/file.jpg`
- Add file-type and file-size validation
- Add support for downloading the generated caption
- Improve the model using a larger image-captioning dataset

