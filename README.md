This project converts **2D images into 3D point clouds** using deep learning. The goal is to take an image of a product and predict its 3D structure.

---

## Project Summary

This project uses:

* **VGG16** to extract image features from 2D images.
* **MLP (Multi-Layer Perceptron)** to convert those features into a **3D point cloud**.
* **Chamfer Distance** as the loss function to compare predicted point clouds with real point clouds.
* **Amazon-Berkeley Objects Dataset** containing multi-view images and 3D point clouds.

---

## Dataset Used

The dataset contains:

* Multiple product images from different angles
* A `.csv` file with paths and IDs
* A folder with 3D point cloud files (`.ply`)

Each image has a matching 3D point cloud.

---

## How the Model Works

### **1. Feature Extraction (VGG16)**

* Every 2D image is passed through VGG16.
* VGG16 converts the image into a **feature vector**.
* These features represent the important information of the image.

### **2. Point Cloud Generation (MLP)**

* The feature vector is sent into an **MLP model**.
* The MLP predicts thousands of **(x, y, z)** points.
* These points form the **3D shape** of the object.

### **3. Loss Function: Chamfer Distance**

* Used to measure how close the predicted point cloud is to the real one.
* The smaller the loss → the better the 3D reconstruction.

---

## Training

* The model is trained for **20 epochs**.
* Uses GPU and mixed-precision training.
* Loss becomes very small (close to zero).
* Checkpoints are saved during training.

---

## Output

The final output of the model is:

* A **predicted 3D point cloud** (shape of the object)
* You can visualize it using PyTorch3D or any 3D viewer

---

## What Is a Point Cloud?

A **point cloud** is a group of thousands of tiny 3D points.
Each point has:

```
x coordinate
y coordinate
z coordinate
```

Together, these points create the **3D shape** of the object.

---

## What Is an MLP?

An **MLP (Multi-Layer Perceptron)** is a simple neural network that:

* Takes input
* Passes through multiple layers
* Creates an output

In this project:

```
VGG Features → MLP → 3D Point Cloud
```

---

## Libraries Used

* PyTorch
* PyTorch3D
* NumPy
* Pandas
* Scikit-Learn
* Open3D

---

## Notes

* This project shows how 2D images can be turned into 3D structures.
* It combines **CNN features** and **MLP prediction**.
* It is simple, clean, and easy to extend with NeRF or more advanced methods.

---
