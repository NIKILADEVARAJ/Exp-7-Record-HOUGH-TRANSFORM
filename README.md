# Hough Transform for Line Detection Using OpenCV

**NAME:** NIKILA D  
**REG NO:** 212224230187

## Aim

To detect straight lines in an input image using the Probabilistic Hough Transform technique with OpenCV and Python.

## Software Requirements

- Python
- Anaconda
- Jupyter Notebook
- OpenCV
- NumPy
- Matplotlib

## Hough Transform

The Hough Transform is a feature extraction technique used in digital image processing to detect straight lines in an image.

The Probabilistic Hough Transform detects line segments from an edge-detected image. In this experiment, Canny Edge Detection is used to identify edges, and HoughLinesP() is used to detect straight lines.

## Algorithm

1. Import the required libraries: OpenCV, NumPy, and Matplotlib.
2. Read the input image using `cv2.imread()`.
3. Convert the input image into grayscale using `cv2.cvtColor()`.
4. Display the original image.
5. Apply Canny Edge Detection using `cv2.Canny()`.
6. Detect line coordinates using `cv2.HoughLinesP()`.
7. Extract the starting and ending coordinates of the detected lines.
8. Draw the detected lines on the original image using `cv2.line()`.
9. Display the final image with detected lines.

## Implementation

### 1. Import Libraries

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

### 2. Read and Convert the Image

```python
image = cv2.imread('Image.png')

gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
```

### 3. Display Original Image

```python
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Input Image")
plt.axis('off')
```

**OUTPUT:**

  <img width="410" height="542" alt="image" src="https://github.com/user-attachments/assets/7aed6eca-f01b-4bce-bf1d-a607f3e01ec9" />

### 4. Grayscale Image

```python
plt.imshow(gray_image, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')
```

**OUTPUT:**

<img width="496" height="560" alt="image" src="https://github.com/user-attachments/assets/5bb2f6f1-f984-4f5b-8ab5-24068829b491" />

### 5. Canny Edge Detection

```python
edges = cv2.Canny(gray_image, 50, 150)

plt.imshow(edges, cmap='gray')
plt.title("Canny Edge Detector")
plt.axis('off')
```

**OUTPUT:**

<img width="527" height="560" alt="image" src="https://github.com/user-attachments/assets/648aa693-93f5-4b95-b41f-8aa07e4df6ef" />

### 6. Hough Transform for Line Detection

```python
lines = cv2.HoughLinesP(
    edges,
    1,
    np.pi / 180,
    100,
    minLineLength=50,
    maxLineGap=10
)
```

### 7. Draw the Detected Lines

```python
if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line[0]
        cv2.line(image, (x1, y1), (x2, y2),
                 (0, 255, 0), 2)
```

### 8. Display the Result of Hough Transform

```python
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Result of Hough Transform")
plt.axis('off')
```

**OUTPUT:**

<img width="435" height="557" alt="image" src="https://github.com/user-attachments/assets/64aba745-d048-4e74-a979-bd2cb37535eb" />

## Result

Thus, straight lines in the input image were successfully detected using the Probabilistic Hough Transform technique with OpenCV and Python.
