# WORKSHOP---5-License-Plate-Detection-using-OpenCV-and-Haar-Cascade-Classifier
# WORKSHOP-5-DIP

# 🚗 License Plate Detection using OpenCV

A lightweight computer vision project that detects and crops vehicle license plates from images using OpenCV and a Haar Cascade Classifier.

---

## 📌 Overview

This project implements an end-to-end digital image processing pipeline to detect vehicle registration plates. It applies preprocessing techniques (grayscale conversion and smoothing) to clean the input image, runs a multi-scale Haar feature detector, draws bounding boxes around detected plates, and automatically crops and saves the plate region of interest (ROI).

---

## ⚙️ Features

* **Image Preprocessing:** Grayscale conversion and noise reduction for better detection accuracy.
* **Haar Cascade Classifier:** Fast, multi-scale object detection via `detectMultiScale`.
* **Automatic Cropping:** Extracts and saves detected license plate regions to disk.
* **Side-by-Side Visualization:** Matplotlib display showing the detected plate and the cropped result.

---

## 🛠️ Requirements

Install the required Python packages before running:

## Program

```python

img = cv2.imread("car_plate.jpg")

gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
blurred = cv2.GaussianBlur(gray, (5, 5), 0)

plates = plate_cascade.detectMultiScale(
    blurred,
    scaleFactor=1.1,
    minNeighbors=4
)

print("Plates detected:", len(plates))

import matplotlib.pyplot as plt

img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

cropped_plate = None

for (x, y, w, h) in plates:
    # Draw rectangle
    cv2.rectangle(
        img_rgb,
        (x, y),
        (x + w, y + h),
        (0, 255, 0),
        3
    )

    # Crop plate
    cropped_plate = img_rgb[y:y+h, x:x+w]

# Display
plt.figure(figsize=(10, 5))

plt.subplot(1, 2, 1)
plt.title("Detected Plate")
plt.imshow(img_rgb)
plt.axis("off")

if cropped_plate is not None:
    plt.subplot(1, 2, 2)
    plt.title("Cropped Plate")
    plt.imshow(cropped_plate)
    plt.axis("off")

plt.show()

```

## Output

<img width="960" height="311" alt="image" src="https://github.com/user-attachments/assets/011a513f-3655-420b-a260-42744f825a4a" />



## Result
    Thus, the workshop has been implemented successfully.
