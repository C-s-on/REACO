# REACO


## Introduction:
Reaco is an intelligent face detection and classification app designed to automate the sorting and grouping of images based on the individuals present, addressing the time-consuming and inefficient manual processes that photographers often face. It leverages technologies like Convolutional Neural Networks (CNNs), representation learning, N-Short learning, and k-Nearest Neighbors (KNN) algorithms to streamline photography workflows. The app provides an intuitive user interface built with the Flutter framework and Dart programming language, enabling photographers to seamlessly upload their image collections. The backend is powered by Python's Fast API and a MongoDB database, ensuring efficient data management and scalability. Docker is used for seamless deployment and cross-platform compatibility.

## Table of Contents
- [Introduction](#introduction)
- [Objectives](#objectives)
- [Features](#features)
- [Background](#background)
- [Methodology](#methodology)
- [Results](#results)
- [Discussion](#Discussion)
- [Outcomes](#outcomes)
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
- Face Detection using YOLOv8: Face Detection Dataset is used to train a YOLOv8m model to locate the face in an image and extracts the faces from the image for further processing.<p align="center">
  <img src="https://github.com/C-s-on/REACO/blob/main/gfx/yolo_result.png" width="400"/>
  <img src="https://github.com/C-s-on/REACO/blob/main/gfx/yolo_prediction.png" width="400"/>
</p>
- [Face alignment using Dlib](https://medium.com/@dsfellow/precise-face-alignment-with-opencv-dlib-e6c8acead262): Locating 68 key points (landmarks) on the face. Based on these landmarks, a few key points on the face were located to align the face.
- Data collection to train the Embedding model: Images of 11,197 individuals, which contain an average of ~20 photos per person.
- Train the embedding model with the implementation of the Siamese network: Preprocessing images to a fixed size, preparing triplets, and using a pre-trained InceptionV3 model. The model was trained with triplet data, using the Adam optimizer.
<p align='center'>
<img src="https://github.com/C-s-on/REACO/blob/main/gfx/triplets_.png" width="600"/>
<img src="https://github.com/C-s-on/REACO/blob/main/gfx/Inception_Network.png" width="600"/>
</p>
- Face Recognition: Taking a short video from the users and extracting 3 frames from it. Embeddings generated by the trained Siamese network is used to train machine learning models such as K-Nearest Neighbors (KNN) and Support Vector Machine (SVM).

## Results:
The project achieved several significant outcomes:
User-Friendly Interface: An intuitive and easy-to-navigate user interface.
Smooth Backend Pipeline: Efficiently handles face verification and recognition tasks.
Effective Face Detection Model: Demonstrates high accuracy and real-time processing.
Reliable Embedding Model: Generates embeddings that effectively capture the unique features of each face.
Robust Dataset Collection: A diverse dataset that enhances the model's generalization capability.
Model Performance: Achieved effective results in training and validation, with a nearly balanced performance between correct and incorrect predictions.

## Discussion:
The Reaco project addresses the problem of manually sorting and categorizing large image collections, which is a time-consuming challenge for photographers and event organizers. By utilizing advanced machine learning techniques such as CNNs, N-Short learning, and KNN, the project aims to automate this process, making it more efficient and less tedious. The development of a user-friendly mobile app with an intuitive interface further enhances the accessibility and usability of the system.

## Outcomes:
The Reaco project successfully developed a face detection and sorting app that provides a valuable solution for users and photographers to efficiently manage and organize their image collections based on face detection results. The project leverages cutting-edge technologies and machine learning techniques to automate the process of face detection, clustering, and image categorization.

Key outcomes of the Reaco project include:
• A robust face detection model capable of accurately identifying and locating faces in images.
• A user-friendly mobile app with an intuitive user interface.
• A reliable and scalable API that facilitates the integration of the face detection model with the application.
• Efficient sorting and filtering of images based on the presence and locations of detected faces.
• Comprehensive documentation detailing the project's architecture, implementation details, and usage instructions.
• Successful deployment and adoption of the face detection and sorting app.

## Resources
1. Python Documentation - https://docs.python.org/3/tutorial/index.html
2. Ipython Documentation - https://ipython.org/documentation.html
3. TensorFlow - https://www.tensorflow.org/guide
4. InseptionV3 - https://keras.io/api/applications/inceptionv3/
5. Face Alignment - https://medium.com/@dsfellow/precise-face-alignment-with-opencv-dlib-e6c8acead262
6. yoloV8 - https://github.com/autogyro/yolo-V8
