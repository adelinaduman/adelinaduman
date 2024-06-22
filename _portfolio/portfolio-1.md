---
title: "Machine Learning Project in Medicine – Alzheimer MRI Predictions"
excerpt: "Implemented a deep learning model(CNN) in Python to replicate the findings of a research paper on Alzheimer's disease prediction using brain MRI images.<br/><img src='/images/11.png'>"
collection: portfolio
---

### **Paper Implementation – Alzheimer MRI Predictions** 🧠
- [GitHub Repository](https://github.com/adelinaduman/AlzheimerMRIpredictions)
- [Dataset](https://www.kaggle.com/datasets/tourist55/alzheimers-dataset-4-class-of-images)
- [Paper](https://www.medrxiv.org/content/10.1101/2021.05.24.21257554v2.full)
- Implemented a deep learning model in Python to replicate the findings of a research paper on Alzheimer's disease prediction using brain MRI images.
- Used a Convolutional Neural Network (CNN) architecture to classify brain MRI images into different stages of Alzheimer's disease.
- Tech Stack: Python, TensorFlow/Keras, Deep Learning, Convolutional Neural Networks


# Image Classification for MRI of Patients with Alzheimer’s Disease Using 2D CNN

## Choice of the Paper

I chose this project for several reasons. Firstly, the impact of diseases on global health is immense, with approximately 29.8 million people affected worldwide in 2015. Addressing the challenges posed by diseases is crucial for improving healthcare outcomes and quality of life. Since I wanted to work on a project that is actively applied in real-world contexts, working on Alzheimer’s disease classification seemed relevant.

Additionally, I was intrigued by the application of deep learning in this project. Deep learning has shown remarkable success in various domains, and I was keen to explore its potential in the context of medical image analysis. I also found that this project would be the perfect opportunity to delve into deep learning techniques in practice.

What makes this project particularly interesting is its approach to image classification using 2D CNNs. While many existing papers exploit the use of 3D CNNs in analyzing MRI data, this project stands out by proposing a method that studies 2D CNNs. The writers transformed 3D MRIs into 2D images and used 2D CNNs for classification. Their models achieve comparable performance to 3D CNNs while offering several advantages. These include simplicity, lower operational costs, and similar efficiency, making it a practical and effective solution for medical image classification tasks.

## Task

The objective was to develop a 2D CNN model capable of classifying MRI images into four distinct categories: Non-Demented, Very Mild Demented, Mild Demented, and Moderate Demented. In a real-world context, this classification system aims to assist medical professionals in their diagnostic procedures.

## Method

My initial step involved preprocessing the dataset. This included standardizing the images to ensure uniformity in format and converting them from RGB to grayscale, given that MRI images are inherently in black and white.

Subsequently, I conducted exploratory data analysis, revealing class imbalances within the dataset. Notably, as the disease progresses, the representation of each class decreases, with the moderate demented category constituting a mere 5% of the dataset.

Using a codebase sourced from GitHub as a foundation, I constructed a 2D CNN model and proceeded to analyze the resulting confusion matrix.

## Extensions

In my efforts to address the issue of data imbalance, I explored two distinct techniques. The first approach involved the use of SMOTE oversampling, which generated synthetic samples for the minority class. However, I realized that while SMOTE can be efficient to balance a numerical dataset, this technique is not appropriate for balancing an image dataset. Therefore, I explored a second approach, using Generative Adversarial Networks (GANs) to create new instances for the underrepresented classes. Through these methods, I aimed to improve the efficiency of my model.

## Challenges in Reproducing the Results

In my case, finding a clean dataset appeared to be a significant hurdle. While datasets for Alzheimer's disease such as ADNI and OASIS are available, accessing them involves a time-consuming process, often requiring formal requests, which was not adapted for a class project. As a result, I opted for a dataset sourced from Kaggle, where MRI scans were already converted into 2D images. The dataset I used unfortunately lacked proper documentation regarding its sources. Additionally, it was originally split into a testing and training set. However, I encountered issues with the testing set, leading me to divide the training set further to create separate training, validation, and testing subsets. Finally, I found out that since my 2D images are slices that were extracted from 3D volumes, there is a risk of data leakage.

## What Worked? What Didn’t?

Despite the issues previously stated, encountered with the quality of the dataset and the difficulty to find the appropriate dataset, I managed to build a 2D CNN with class-specific F1-scores ranging from 0.93 to 1. My future work here would be to train other algorithms and even try ensemble methods to improve these metrics.

I decided to extend my work in this project with the utilization of GANs. This was a challenging part of the project since I had to adapt existing codes trained on MNIST to my own dataset, with data shaped differently. That led me to tune the parameters related to the architecture of the generator. Finding the right epoch and batch number in order to have a decrease and a convergence in the generator loss was also a computationally expensive and time-consuming step. Finally, I didn’t manage to generate MRI images with the quality of the original images; they are more pixelated. However, I believe that this technique could be efficient if the generator was trained on a larger dataset (with ADNI data, for instance).

Even though using the GAN to augment the data seems to improve the class-specific F1-scores, I want to remain careful with these results since the generator has been trained on a very small dataset. Moreover, I didn’t want to introduce too many generated images since the generator could be overfitting the original dataset and therefore introduce some sort of overfitting in my classification model.
