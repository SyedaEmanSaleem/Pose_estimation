## YOLOv8 Pose Estimation on Custom Human Activities

---

### 📌 Overview

This project uses **Ultralytics' YOLOv8n-pose** model to detect and classify human body poses from images. The model is trained on a custom dataset of physical movements and gestures, enabling it to recognize specific human activities with high precision. Applications range from fitness tracking to gesture-based control systems.

---

### 🎯 Objective

The goal of this project is to:

* Accurately detect **key body landmarks** in humans.
* Classify actions or gestures into predefined **pose categories**.
* Train a lightweight yet effective model for **real-time pose estimation**.
* Support use cases such as **gesture recognition**, **health monitoring**, and **human-computer interaction**.

---

### 📁 Dataset

* The dataset is custom-labeled in YOLOv8 format.
* Includes images across multiple pose classes.
* Divided into training, validation, and testing sets.
* Used for recognizing fine-grained actions like *pump up and down*, *pull*, *rover*, and more.

---

### 🏋️‍♂️ Pose Classes

The model is trained to detect and classify the following actions:

```
['cross', 'extra', 'overhead', 'point', 'pull', 
 'pump up and down', 'push', 'push-forward', 
 'rover', 'shoulder-swipe', 'snap', 'stop', 'sway']
```

---

### ⚙️ Training Details

* **Base Model**: `yolov8n-pose.pt` (nano version of YOLOv8 Pose)
* **Training Tool**: Ultralytics YOLO via Python
* **Environment**: Google Colab, GPU-enabled (Tesla T4)
* **Epochs**: 150 (early stopped at 148 due to no improvement)
* **Time**: ~22 minutes total training
* **Hyperparameters**:

  * Learning rate: `0.0005`
  * Weight decay: `0.0001`
  * Warmup epochs: `3`
  * Patience: `30`

Best performance observed at **epoch 118**, and the corresponding model checkpoint was saved.

---

### 📈 Performance Summary

#### ✅ Overall Validation Metrics

* **Bounding Box Precision**: `0.83`

* **Bounding Box Recall**: `0.775`

* **mAP50 (Box)**: `0.871`

* **mAP50-95 (Box)**: `0.591`

* **Pose Precision**: `0.753`

* **Pose Recall**: `0.709`

* **mAP50 (Pose)**: `0.76`

* **mAP50-95 (Pose)**: `0.36`

#### 🏷️ Top Class Performance (Pose)

| Class            | mAP50 | mAP50-95 |
| ---------------- | ----- | -------- |
| pump up and down | 0.969 | 0.708    |
| pull             | 0.747 | 0.383    |
| extra            | 0.963 | 0.247    |
| shoulder-swipe   | 0.797 | 0.356    |
| rover            | 0.903 | 0.367    |

> Model fitness score: **0.951**

---

### 🖼️ Inference & Results

After training, the model was tested on unseen images with a confidence threshold of **0.6**. Inference results included:

* Detected poses with keypoint overlays
* Class predictions
* Confidence scores

Visual output (e.g., `results.png`) was used to verify model accuracy. Inference time per image: ~20 ms.

---

### 🚀 Use Cases

This project lays the foundation for various real-world applications:

* 🧘 **Fitness pose feedback**
* 🦾 **Human-robot interaction**
* 👨‍⚕️ **Rehabilitation posture tracking**
* 🕹️ **Gesture-based control**
* 🎯 **Surveillance or activity recognition**

---

### 🧪 Future Enhancements

* Support live webcam or video inference
* Improve performance on underrepresented classes
* Expand dataset diversity and size
* Convert model to ONNX or TFLite for mobile deployment
* Integrate into a UI or real-time app

---
