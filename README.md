# Exp-05-Image-Smoothing-and-Sharpening-Using-OpenCV

## NAME : SIVAKARTHIKEYAN V

## REG. NO. : 212225220098

---

## AIM

To write a Python program using OpenCV to apply different **smoothing and sharpening filters** to an image and display the results for comparison.

### Filters Performed

#### Smoothing Filters

* Average Filter
* Weighted Average Filter
* Gaussian Filter
* Median Filter

#### Sharpening / Edge Detection Filters

* Laplacian Kernel
* Laplacian Operator

---

## SOFTWARE USED

* Python
* Jupyter Notebook / VS Code
* OpenCV (`cv2`)
* NumPy
* Matplotlib

---

## INPUT IMAGE

The input image used for this experiment is:

```text
Photo.jpg
```

The image should be placed in the **same directory as the Python program or Jupyter Notebook**.

The image is loaded using:

```python
image1 = cv2.imread("Photo.jpg")
```

---

# ALGORITHM

### Step 1: Import Libraries

Import the required libraries:

* OpenCV
* NumPy
* Matplotlib

### Step 2: Read the Image

Read the input image `Photo.jpg` using `cv2.imread()`.

### Step 3: Convert Image

Convert the image from **BGR to RGB** format using `cv2.cvtColor()` so that it can be displayed correctly using Matplotlib.

### Step 4: Apply Average Filter

Create an averaging kernel and apply it to the image using `cv2.filter2D()`.

### Step 5: Apply Weighted Average Filter

Create a weighted kernel where the center pixels have greater importance and apply it using `cv2.filter2D()`.

### Step 6: Apply Gaussian Filter

Apply Gaussian smoothing using `cv2.GaussianBlur()` to reduce noise while maintaining important image structures.

### Step 7: Apply Median Filter

Apply a median filter using `cv2.medianBlur()` to smooth the image and reduce impulse noise.

### Step 8: Apply Laplacian Kernel

Apply a custom Laplacian kernel using `cv2.filter2D()` to enhance image details and edges.

### Step 9: Apply Laplacian Operator

Use `cv2.Laplacian()` to detect regions with rapid changes in intensity.

### Step 10: Display Results

Display the original image and the output of each filter separately for comparison.

---

# PROGRAM

## Import Libraries and Read Image

```python
import cv2
import matplotlib.pyplot as plt
import numpy as np

image1 = cv2.imread("Photo.jpg")
image2 = cv2.cvtColor(image1, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(6,5))
plt.imshow(image2)
plt.title("Original Image")
plt.axis("off")
plt.show()
```

---

## Average Filter

The Average Filter smooths the image by replacing each pixel with the average value of its neighboring pixels.

```python
kernel = np.ones((11,11), np.float32) / 121
image3 = cv2.filter2D(image2, -1, kernel)

plt.figure(figsize=(9,5))

plt.subplot(1,2,1)
plt.imshow(image2)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,2,2)
plt.imshow(image3)
plt.title("Average Filter Image")
plt.axis("off")

plt.show()
```

### Kernel Used

```text
1/121 ×
[1 1 1 ... 1]
[1 1 1 ... 1]
[1 1 1 ... 1]
...
```

The kernel size is **11 × 11**.

---

## Weighted Average Filter

The Weighted Average Filter gives greater importance to pixels near the center of the kernel.

```python
kernel1 = np.array([
    [1,2,1],
    [2,4,2],
    [1,2,1]
]) / 16

image3 = cv2.filter2D(image2, -1, kernel1)

plt.figure(figsize=(9,5))

plt.subplot(1,2,1)
plt.imshow(image2)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,2,2)
plt.imshow(image3)
plt.title("Weighted Average Filter Image")
plt.axis("off")

plt.show()
```

### Kernel Used

```text
[1 2 1]
[2 4 2] / 16
[1 2 1]
```

---

## Gaussian Filter

The Gaussian Filter performs smoothing using a Gaussian distribution.

```python
gaussian_blur = cv2.GaussianBlur(image2, (33,33), 0, 0)

plt.figure(figsize=(9,5))

plt.subplot(1,2,1)
plt.imshow(image2)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,2,2)
plt.imshow(gaussian_blur)
plt.title("Gaussian Blur")
plt.axis("off")

plt.show()
```

The Gaussian kernel size used is **33 × 33**.

---

## Median Filter

The Median Filter replaces each pixel with the median value of its neighboring pixels. It is particularly useful for reducing impulse or salt-and-pepper noise.

```python
median = cv2.medianBlur(image2, 13)

plt.figure(figsize=(9,5))

plt.subplot(1,2,1)
plt.imshow(image2)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,2,2)
plt.imshow(median)
plt.title("Median Blur")
plt.axis("off")

plt.show()
```

The kernel size used is **13 × 13**.

---

## Laplacian Kernel

A custom kernel is applied to enhance edges and fine details.

```python
kernel2 = np.array([
    [-1,-1,-1],
    [2,-2,1],
    [2,1,-1]
])

image3 = cv2.filter2D(image2, -1, kernel2)

plt.figure(figsize=(9,5))

plt.subplot(1,2,1)
plt.imshow(image2)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,2,2)
plt.imshow(image3)
plt.title("Laplacian Kernel")
plt.axis("off")

plt.show()
```

### Kernel Used

```text
[-1  -1  -1]
[ 2  -2   1]
[ 2   1  -1]
```

---

## Laplacian Operator

The Laplacian Operator detects areas where the image intensity changes rapidly.

```python
laplacian = cv2.Laplacian(image2, cv2.CV_64F)

plt.figure(figsize=(9,5))

plt.subplot(1,2,1)
plt.imshow(image2)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,2,2)
plt.imshow(laplacian)
plt.title("Laplacian Operator")
plt.axis("off")

plt.show()
```

---

# OUTPUT

## 1. Original Image

The original `Photo.jpg` image before applying any smoothing or sharpening operation.

**Output:** Original Image
<img width="371" height="481" alt="image" src="https://github.com/user-attachments/assets/ddda953b-8257-4fc5-a706-a4b21fa06a64" />

---

## 2. Average Filter Output

The Average Filter produces a blurred and smoothed version of the original image by averaging neighboring pixels.

**Kernel Size:** 11 × 11

**Output:** Average Filter Image
<img width="887" height="560" alt="image" src="https://github.com/user-attachments/assets/a34e538e-14d2-4be5-8e56-6a5d537be15f" />

---

## 3. Weighted Average Filter Output

The Weighted Average Filter provides different weights to neighboring pixels, with greater importance given to the center pixels.

**Kernel Size:** 3 × 3

**Output:** Weighted Average Filter Image
<img width="899" height="562" alt="image" src="https://github.com/user-attachments/assets/230a9769-cba5-4dce-ae2d-e719013a7ba7" />

---

## 4. Gaussian Filter Output

The Gaussian Filter smooths the image using a Gaussian distribution and helps reduce image noise.

**Kernel Size:** 33 × 33

**Output:** Gaussian Blur
<img width="893" height="553" alt="image" src="https://github.com/user-attachments/assets/d49a9141-17e2-46e5-978f-b8e84fe7cbc2" />

---

## 5. Median Filter Output

The Median Filter smooths the image while being particularly effective at removing salt-and-pepper noise.

**Kernel Size:** 13 × 13

**Output:** Median Blur
<img width="875" height="553" alt="image" src="https://github.com/user-attachments/assets/83943d5a-aae6-44ec-81b2-07edf6c841b4" />

---

## 6. Laplacian Kernel Output

The custom Laplacian kernel enhances edges and fine image details.

**Kernel Size:** 3 × 3

**Output:** Laplacian Kernel
<img width="885" height="544" alt="image" src="https://github.com/user-attachments/assets/f14920e8-5006-4538-b422-317523fa0513" />

---

## 7. Laplacian Operator Output

The Laplacian Operator detects edges and regions with rapid changes in intensity.

**Output:** Laplacian Operator
<img width="888" height="536" alt="image" src="https://github.com/user-attachments/assets/5ce09ee1-7d2d-443a-b4fd-498c6073fc4a" />

---

# OUTPUT DESCRIPTION

## Smoothing Filters

### Average Filter

Produces a smooth and blurred version of the original image by averaging neighboring pixel values.

### Weighted Average Filter

Produces a smoother image by assigning different weights to neighboring pixels, with the center pixel receiving higher importance.

### Gaussian Filter

Reduces noise and smooths the image using a Gaussian distribution while maintaining important image structures.

### Median Filter

Effectively reduces impulse or salt-and-pepper noise while preserving important edges.

---

## Sharpening and Edge Detection Filters

### Laplacian Kernel

Enhances edges and fine details using a custom convolution kernel.

### Laplacian Operator

Detects edges and areas where there are rapid changes in image intensity.

---

# RESULT

Thus, different **smoothing and sharpening filters** were successfully implemented using **OpenCV in Python**.

The Average, Weighted Average, Gaussian, and Median filters were used for image smoothing, while the Laplacian Kernel and Laplacian Operator were used for edge enhancement and edge detection.

The results of each filter were successfully displayed and compared with the original image.

---

## STUDENT DETAILS

**Name:** Sivakarthikeyan V

**Reg. No.:** 212225220098

**Experiment:** EXP-5 - Image Smoothing and Sharpening

**Input Image:** `Photo.jpg`
