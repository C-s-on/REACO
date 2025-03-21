# REACO


## Introduction:
Reaco is an intelligent face detection and classification app designed to automate the sorting and grouping of images based on the individuals present, addressing the time-consuming and inefficient manual processes that photographers often face. It leverages technologies like Convolutional Neural Networks (CNNs), representation learning, N-Short learning, and k-Nearest Neighbors (KNN) algorithms to streamline photography workflows. The app provides an intuitive user interface built with the Flutter framework and Dart programming language, enabling photographers to seamlessly upload their image collections. The backend is powered by Python's Fast API and a MongoDB database, ensuring efficient data management and scalability. Docker is used for seamless deployment and cross-platform compatibility.

## Table of Contents
- [Introduction](#introduction)
- [Objectives](#objectives)
- [Features](#features)
- [Background](#background)
- [Methodology](#methodology)
- [Outcomes](#outcomes)
- [Appendix](#appendix)
- [Resources](#resources)

## Objectives:
Develop an automated system for accurate face detection, recognition, and clustering in image collections. Utilizing CNNs, N-Short learning, and KNN for robust facial recognition and categorization, paired with a user-friendly Flutter/Dart interface for easy image uploads and organized result retrieval which Enable efficient distribution of requested photos based on facial recognition.

## Features:
- Automated Face Detection and Categorization: Uses CNNs and other machine learning algorithms to automatically detect and categorize faces in images.
- User-Friendly Interface: Built with Flutter and Dart to provide a responsive and intuitive user experience across multiple platforms.
- Efficient Data Management: Utilizes Fast API and a MongoDB database for efficient and scalable data management.
- Cross-Platform Compatibility: Employs Docker for seamless deployment across different computing environments.
- Account Registration: Users can register by uploading a video of their face, which is then processed to store three images for future comparison.
- Image Upload and Processing: Users can upload images, which are then stored in MongoDB and processed using face detection algorithms.
- Sorted Image Retrieval: Users can access a dashboard to receive sorted and filtered images based on face detection predictions.

## Background:
Manually organizing large collections of photographs based on individuals present is a cumbersome task. Existing solutions lack efficient facial recognition and image categorization capabilities specific to photography workflow needs. Reaco addresses this gap by developing an intelligent system that automates face detection, extraction, and clustering through cutting-edge technologies. The user-friendly solution aims to streamline image organization for photographers, enabling them to focus on their creative pursuits while revolutionizing automated image analysis.

## Methodology:
The methodology involves several key steps:
Labeled data for Face Detection: We used a freely available dataset from Kaggle, containing approximately 32,000 images (26,000 for training and 6,000 for validation). This dataset included clean labels in the xywh format for human face detection tasks.
- Face Detection using YOLOv8: Face Detection Dataset is used to train a YOLOv8m model to locate the face in an image and extracts the faces from the image for further processing.
<p align="center">
<img src="https://github.com/C-s-on/REACO/blob/main/gfx/yolo_result.png" width="600"/>
<img src="https://github.com/C-s-on/REACO/blob/main/gfx/yolo_predict.png" width="600"/></p>

- [Face alignment using Dlib](https://medium.com/@dsfellow/precise-face-alignment-with-opencv-dlib-e6c8acead262): Locating 68 key points (landmarks) on the face. Based on these landmarks, a few key points on the face were located to align the face.
- Data collection to train the Embedding model: Images of 11,197 individuals, which contain an average of ~20 photos per person.
- Train the embedding model with the implementation of the Siamese network: Preprocessing images to a fixed size, preparing triplets, and using a pre-trained InceptionV3 model. The model was trained with triplet data, using the Adam optimizer.
<p align='center'>
<img src="https://github.com/C-s-on/REACO/blob/main/gfx/triplets_.png" width="400"/>
<img src="https://github.com/C-s-on/REACO/blob/main/gfx/Inception_Network.png" width="375"/>
</p>

- Face Recognition: Taking a short video from the users and extracting 3 frames from it. Embeddings generated by the trained Siamese network is used to train machine learning models such as K-Nearest Neighbors (KNN) and Support Vector Machine (SVM).

## Outcomes:
1. User-Friendly Interface
   The project includes a well-designed user interface that is intuitive and easy to navigate.
   Key features include:
   * Ease of Use
   * Responsive Design
   * Clean Feedback
2. Smooth Backend Pipeline
   The backend architecture is designed to handle face verification and recognition tasks
   efficiently. Key characteristics include:
   * Scalability
   * Robustness
   * Efficiency
3. Effective Face Detection Model
   The core of the system is a highly effective face-detection model, which demonstrates
   the following qualities:
   * High Accuracy
   * Real-Time Processing
   * Robust Performance
4. Reliable Embedding Model
   A critical component of the system is the reliable embedding model, which has been trained
   using a Siamese network with the implementation of triplet loss. Key outcomes include:
   * Effective Feature Extraction
   * Robustness

### Model Performance
<p align="center"><img src="https://github.com/C-s-on/REACO/blob/main/gfx/train_val_loss.png" width="600"/></p>
The graph shows the training and validation loss of a Siamese network over batches. Initially, 
both losses drop sharply, indicating rapid learning. After this initial phase, the losses stabilize 
and show slight fluctuations around lower values, suggesting that the model has learned the 
key patterns. The validation loss is consistently slightly lower than the training loss, 
indicating minimal overfitting well, with both losses converging and maintaining stability. 

## Appendix
<p align="center">
  <img src="https://github.com/C-s-on/REACO/blob/main/gfx/reaco.jpg" width="250"/>
  <img src="https://github.com/C-s-on/REACO/blob/main/gfx/reaco_welcome.jpg" width="250"/>
  <img src="https://github.com/C-s-on/REACO/blob/main/gfx/reaco_signup.jpg" width="250"/>
</p>

## Resources
1. Python Documentation - https://docs.python.org/3/tutorial/index.html
2. Ipython Documentation - https://ipython.org/documentation.html
3. TensorFlow - https://www.tensorflow.org/guide
4. InseptionV3 - https://keras.io/api/applications/inceptionv3/
5. Face Alignment - https://medium.com/@dsfellow/precise-face-alignment-with-opencv-dlib-e6c8acead262
6. yoloV8 - https://github.com/autogyro/yolo-V8
