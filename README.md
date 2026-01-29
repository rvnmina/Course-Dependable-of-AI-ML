# Assignment 1: CNN Basics & Fault-Tolerant CNN  
## Task 1 – Image Filtering & Edge Detection

This assignment focuses on applying classical **spatial-domain image processing filters** as a foundation for understanding convolution operations used in Convolutional Neural Networks (CNNs).

---

## 📌 Objective (Task 1)

To apply and analyze different **smoothing, denoising, and edge detection filters** on input images and identify **robust parameter values** that generalize well across different image types.

---

## 🖼️ Input Images

The following grayscale images are used for experimentation:

- `Gradient.png` – synthetic gradient image (ideal for observing filter behavior)
- `car.png` – real-world natural image
- `car_resize.png` – resized version for stable comparison

---

## 🧪 Filters Implemented

### 🔹 Smoothing / Denoising Filters
- Gaussian Filter  
- Gaussian Blur  
- Neighbourhood Average Filter  
- BOX Filter  
- Weighted-Average Filter (Gaussian-based)  
- Median Filter  
- Minimum Filter (Erosion)  
- Maximum Filter (Dilation)

### 🔹 Edge Detection / Derivative Filters
- Laplacian Filter  
- Sobel Filter (Gradient Magnitude)  
- Generic Edge Detection (Sobel-based)  
- Canny Edge Detector (Automatic Threshold Selection)

> **Note:** Gaussian pre-smoothing is applied before second-derivative filters to reduce noise amplification.

---

## ⚙️ Parameter Selection Strategy

Instead of arbitrary tuning, **stable and reusable default values** are chosen based on classical image processing heuristics:

- **Gaussian Filter:**  
  - Kernel size: `5 × 5`  
  - Sigma: `1.0`  
  - Provides optimal noise reduction with minimal edge distortion.

- **Median Filter:**  
  - Kernel size: `3 × 3`  
  - Effective for salt-and-pepper noise.

- **Canny Edge Detector:**  
  - Thresholds are computed automatically using the image median:  
    - `low = (1 − σ) × median`  
    - `high = (1 + σ) × median`, where `σ = 0.33`  
  - This makes edge detection robust across varying images.

---

## 📊 Output Visualization

For each input image:
- All filters are applied sequentially.
- Results are displayed in a **grid format** for direct visual comparison.
- This helps in understanding:
  - Noise suppression behavior
  - Edge localization quality
  - Over-smoothing vs detail preservation

---

## 🧠 Key Learning Outcomes

- Understanding spatial filtering as convolution operations
- Effect of kernel size and parameters on image quality
- Practical intuition behind edge detection pipelines
- Foundations for CNN filter interpretation

---

## 🛠️ Tools & Libraries Used

- Python  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

## 📂 How to Run

1. Upload the input images to the working directory (`/content/` in Colab).
2. Run the provided notebook cells sequentially.
3. Observe filter outputs for all images in the generated grids.

---

## ✅ Status

✔️ Task 1 Completed  
✔️ Outputs verified on multiple images  
✔️ Parameter values validated for generalization

---

## ✍️ Author

**Ravindra Mina**  
M.Tech – Artificial Intelligence  
IIT Kharagpur
