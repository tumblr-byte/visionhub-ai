# visionhub-ai

![Image](https://github.com/user-attachments/assets/e5db962e-8b50-4234-bd06-877beac35a35)

VisionHub-AI is a Django-based application that demonstrates a powerful pipeline combining **YOLOv11n-seg (instance segmentation)** with bird classification and face recognition features.

## Pipeline Overview

The application uses the `yolo11n-seg.pt` model, trained on the **COCO dataset**, to perform **instance segmentation** this includes detecting objects and generating pixel-level segmentation masks.

From the 80 COCO classes, we focus on two: **bird** and **person**. Based on which is detected, the pipeline branches into two modules:

---

## Bird Detection and Classification

- When a **bird** is detected by yolo11n-seg, a **"View Bird"** button appears.
- Clicking the button navigates to the **Bird Classification** page.
- On that page, clicking **"Classify Bird"** runs the `bird_resnet_classifier.pt` model.
- This model is trained to classify bird species using a custom dataset.
- You can explore the training notebook here:  
  [Bird Classification using PyTorch (Kaggle)](https://www.kaggle.com/code/healingsoal25/bird-classification-using-pytorch/notebook)
- The bird images used for testing were taken from Pixabay.

**Demo Video:**  
[Watch Bird Classification Demo](https://github.com/user-attachments/assets/4432c110-424f-4e62-91ab-72e7a789299e)

---

## Face Detection and Recognition

- When a **person** is detected by YOLOv11n-seg, a **"View Face"** button appears.
- Clicking it redirects the user to the **Face Recognition** page.
- On this page, clicking **"Recognize Face"** runs the face recognition logic.
- It uses the [`face_recognition`](https://github.com/ageitgey/face_recognition) library, which provides a pretrained model based on dlib's ResNet.
- If the detected face matches any in the pre-stored **images folder**, it’s labeled with a bounding box and name.

> No training was done for face recognition we use pretrained embeddings to compare known and unknown faces.

Dataset used:  
[Celebrity Face Dataset (Kaggle)](https://www.kaggle.com/datasets/vishesh1412/celebrity-face-image-dataset)
*This dataset was originally created by the author listed above. For this project, it has been slightly modified, and the face images used for testing were also taken from it.*

**Demo Video:**  
[Watch Face Recognition Demo](https://github.com/user-attachments/assets/2a47c3f7-886a-47e6-a902-302546a15a74)

---

## Technology Stack

**Frontend:**  
- HTML  
- CSS  
- JavaScript  

**Backend:**  
- Django (Python)  

**Models and Libraries Used:**  
- `YOLOv11n-seg` (for instance segmentation)  
- `bird_resnet_classifier.pt` (custom ResNet model for bird classification)  
- [`face_recognition`](https://github.com/ageitgey/face_recognition) (for face recognition using pretrained face embeddings)

---

## Summary

VisionHub-AI demonstrates how to combine instance segmentation with classification and recognition features in a modular and interactive Django web application.

