🧘‍♂️ Yoga Mudra Hand Sign Recognition
Using Python, OpenCV, TensorFlow & Google Teachable Machine

This project is a real-time yoga mudra recognition system that detects hand gestures through a webcam and classifies them into different yoga mudras using a deep learning model trained on Google’s Teachable Machine.

It combines OpenCV for image processing, cvzone for hand tracking, and a TensorFlow model for gesture classification.

📸 Demo

The system captures your hand in real-time and classifies the yoga mudra (e.g., Gyan Mudra, Vayu Mudra, Prithvi Mudra, etc.) directly on the screen.

🧩 Tech Stack

Python

OpenCV – Image capture & processing

cvzone – Hand tracking module

TensorFlow / Keras – Deep learning model loading & prediction

NumPy – Image array manipulation

Google Teachable Machine – Model training

🚀 Features

✅ Real-time hand tracking using webcam
✅ Auto-cropped and resized hand image input for model consistency
✅ Custom dataset creation for yoga mudras
✅ Deep learning classification using .h5 model
✅ Easy to extend with new mudras

🧠 How to Train Your Own Model using Teachable Machine

Go to Google Teachable Machine
.

Choose Image Project → Standard Image Model.

Create one class per yoga mudra (e.g., Gyan Mudra, Vayu Mudra, etc.).

Capture multiple images for each mudra using your webcam.

Click Train Model to let Teachable Machine build a classifier.

After training, click Export Model → TensorFlow → Download my model.

Rename the downloaded model file to keras_model.h5 and place it in your project directory.

🧰 Installation
1️⃣ Clone the repository
git clone https://github.com/<your-username>/Yoga-Mudra-Hand-Recognition.git
cd Yoga-Mudra-Hand-Recognition

2️⃣ Install dependencies
pip install opencv-python cvzone tensorflow numpy

3️⃣ Create data folders

If you plan to capture new training images:

mkdir -p data/VayuMudra

4️⃣ Run the data capture script
python data_capture.py


Press ‘s’ to save each image.
Captured images are stored inside the folder you define (e.g., data/VayuMudra).

▶️ Running the Gesture Recognition Script

Once you have your trained model (keras_model.h5):

python detect_mudra.py


Ensure your webcam is enabled. The live feed will appear with bounding boxes around your hand and the detected mudra name.

🧾 Code Explanation
1️⃣ Hand Detection & Cropping

The script uses cvzone.HandDetector to find the hand and extract its bounding box.

hands, img = detector.findHands(img)


The cropped hand image is then resized to a 300x300 white background for model compatibility.

2️⃣ Aspect Ratio Adjustment

Maintains the correct proportions of the hand image before resizing.

if aspectRatio > 1:
    # Taller image
else:
    # Wider image

3️⃣ Image Saving

Each cropped and processed image is saved when you press the ‘s’ key.

cv2.imwrite(f'{folder}/Image_{time.time()}.jpg', imgWhite)

4️⃣ Model Training & Prediction

The captured dataset is trained using Teachable Machine.

The .h5 file is used later in a separate detection script to predict mudras in real time.

📂 Folder Structure
Yoga-Mudra-Hand-Recognition/
│
├── keras_model.h5              # Trained model from Teachable Machine
├── data_capture.py             # Script for capturing mudra images
├── detect_mudra.py             # (Optional) Script for model inference
├── data/
│   └── VayuMudra/              # Folder containing captured images
└── README.md                   # Project documentation

🔮 Future Improvements

Add multi-hand detection

Integrate audio feedback for recognized mudras

Build a streamlit or web interface

Improve dataset quality with more diverse lighting

👨‍💻 Author

Dhanush M

📧 mrdhanush11@gmail.com

🔗 LinkedIn

💻 GitHub

⭐ Support

If you like this project, consider giving it a ⭐ on GitHub — it helps others find it!
