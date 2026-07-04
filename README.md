# ✍️ Real-Time Handwritten Digit Classifier

![TensorFlow](https://img.shields.io/badge/TensorFlow-%23FF6F00.svg?style=flat&logo=TensorFlow&logoColor=white)
![Keras](https://img.shields.io/badge/Keras-%23D00000.svg?style=flat&logo=Keras&logoColor=white)
![Gradio](https://img.shields.io/badge/Gradio-%23FF6F00.svg?style=flat&logo=gradio&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)

An end-to-end Deep Learning web application that predicts handwritten digits (0-9) in real-time. Built with TensorFlow/Keras and deployed using a Gradio web interface.

## 🚀 The Project
This project trains a Convolutional Neural Network (CNN) on the classic MNIST dataset to achieve ~99% test accuracy. Instead of just stopping at a Jupyter Notebook, I integrated the trained model with a live sketchpad UI so users can draw digits and get instant, real-time predictions. 

## 🛠️ Tech Stack
* **Deep Learning Framework:** TensorFlow / Keras
* **Architecture:** Convolutional Neural Network (CNN)
* **Web Interface:** Gradio
* **Data Processing:** NumPy, PIL (Python Imaging Library), Scikit-Learn

## 🐛 Overcoming "Domain Shift"
The biggest challenge wasn't hitting 99% accuracy during training—it was deploying the model to production. Initially, the model failed completely on the live sketchpad, misclassifying obvious numbers. 

**The Bug:** The MNIST dataset consists of *white ink on a black background*. The Gradio sketchpad uses *black ink on a white background*. The model was blinded by the white background, resulting in random guesses.

**The Engineering Fix:** I built an image preprocessing pipeline using `PIL.ImageOps.invert` to convert the live user input to match the training data's color space *before* passing the tensor to the model. This immediately restored the 99% accuracy in the live production environment.

## 🏃‍♂️ How to Run This Code
The entire project is self-contained in a Google Colab notebook. 

1. Open `digit_classifier_app.ipynb` in Google Colab.
2. Go to **Runtime** > **Change runtime type** and select **T4 GPU**.
3. Run all cells to download the dataset, train the CNN, and launch the Gradio server.
4. Click the public `*.gradio.live` link generated at the very bottom of the notebook to open the web app and draw your own digits!
