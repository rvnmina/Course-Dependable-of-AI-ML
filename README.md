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

---

## Task 2 – Kernel Size, Stride & Pooling Operations

This task explores the effect of **kernel size**, **stride**, and **pooling operations** on image representations, closely mirroring downsampling and receptive field growth in Convolutional Neural Networks (CNNs).

---

## 📌 Objective (Task 2)

To study how different **kernel sizes** and **stride values** influence spatial resolution and information retention, and to compare **max, min, and average pooling** operations using robust, reusable parameter choices.

---

## 🖼️ Input Images

The same grayscale images from Task 1 are reused to ensure consistency:

- `Gradient.png`
- `car.png`
- `car_resize.png`

---

## 🧩 Kernel Sizes & Stride Selection

The following kernel sizes are applied:

- **5 × 5**
- **9 × 9**
- **11 × 11**

Stride values are chosen **relative to kernel size** to balance spatial coverage and computational efficiency:

| Kernel Size | Stride Values Used |
|------------|-------------------|
| 5 × 5      | 1, 3              |
| 9 × 9      | 1, 3, 5           |
| 11 × 11    | 1, 3, 5, 7        |

> Larger kernels are paired with larger strides to simulate receptive field expansion while avoiding redundant overlap.

---

## 🧪 Pooling Operations Implemented

For each kernel–stride combination, the following pooling methods are applied:

- **Max Pooling** – preserves dominant local features and edges  
- **Min Pooling** – suppresses bright noise, similar to erosion  
- **Average Pooling** – smooth downsampling with stable representations  

All pooling operations are implemented **without padding**, and the output spatial dimensions are computed analytically.

---

## 📊 Output Visualization

- Results are visualized in **grid format** for each input image.
- Each grid cell shows:
  - Pooling type
  - Kernel size
  - Stride value
  - Output resolution
- This allows direct comparison of:
  - Detail preservation vs downsampling
  - Sensitivity to stride changes
  - Pooling behavior across different images

---

## 🧠 Key Observations

- Smaller kernels with stride 1 retain fine spatial details.
- Larger kernels combined with higher strides significantly reduce spatial resolution while increasing contextual coverage.
- Max pooling highlights structural edges, while average pooling provides smoother, more stable feature maps.
- Min pooling effectively suppresses isolated bright artifacts.

---

## 🧠 Learning Outcomes

- Understanding the role of **receptive fields** in CNNs
- Effect of stride on feature map resolution
- Functional differences between pooling operations
- Practical intuition for selecting kernel–stride combinations

---

## ✅ Status

✔️ Task 2 Completed  
✔️ All kernel–stride–pooling combinations evaluated  
✔️ Parameter choices validated for reuse in future tasks

---

## ✍️ Author

**Ravindra Mina**  
M.Tech – Artificial Intelligence  
IIT Kharagpur
