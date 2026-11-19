# Image Smoothing and Sharpening Using OpenCV
## Aim
To write a Python program using OpenCV to apply different smoothing filters (Averaging, Weighted Averaging, Gaussian, Median) and sharpening filters (Laplacian Kernel and Laplacian Operator) for image enhancement, and display each result separately along with the original image for comparison.

The program performs the following operations:
Read and display an input image
Apply Averaging filter
Apply Weighted Averaging filter
Apply Gaussian filter
Apply Median filter
Apply Laplacian sharpening using kernel
Apply Laplacian operator
Display all outputs for comparison
## Software Used
Anaconda – Python 3.7
Jupyter Notebook / VS Code
OpenCV (cv2)
NumPy
Matplotlib
## Algorithm
### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image (e.g., image.jpg).

### Step 3:
Convert the image from BGR to RGB format for display.

### Step 4:
Apply Averaging Filter using cv2.blur().

### Step 5:
Apply Weighted Averaging Filter using a custom kernel with cv2.filter2D().

### Step 6:
Apply Gaussian Filter using cv2.GaussianBlur().

### Step 7:
Apply Median Filter using cv2.medianBlur().

### Step 8:
Apply Laplacian Sharpening using Kernel with cv2.filter2D().

### Step 9:
Convert image to grayscale and apply Laplacian Operator using cv2.Laplacian().

### Step 10:
Display all filtered images using a grid layout for comparison.

## Program:
### Developed By
### Name: KIRUTIKA K R
### Register No: 212224230128  
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
# Step 2: Load the image using imread() from cv2 module
image = cv2.imread('sudoku.png')  # Replace 'image.jpg' with your image path
# Step 3: Convert the image to grayscale
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
# Input image and grayscale image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Convert image to RGB for displaying
plt.title("Input Image")
plt.axis('off')
```
```
plt.imshow(gray_image, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')
```
```
# Step 4: Using Canny operator from cv2, detect the edges of the image
edges = cv2.Canny(gray_image, 50, 150)  # Canny edge detection with threshold values 50 and 150
# Canny Edge Detector output
plt.imshow(edges, cmap='gray')
plt.title("Canny Edge Detector")
plt.axis('off')
```
```
# Step 5: Using the HoughLinesP(), detect line coordinates for every point in the image
# The parameters of HoughLinesP are: image, resolution, threshold, minLineLength, maxLineGap
lines = cv2.HoughLinesP(edges, 1, np.pi / 180, 100, minLineLength=50, maxLineGap=10)
# Step 6: Using a for loop, draw the lines on the original image
# The lines variable contains the endpoints of the detected lines

if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line.reshape(-1)
        cv2.line(image, (x1, y1), (x2, y2), (0, 255, 0), 2)
# Display the result of Hough Transform (Image with lines)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Image with lines drawn
plt.title("Result of Hough Transform")
plt.axis('off')
```
## Output
<img width="430" height="425" alt="image" src="https://github.com/user-attachments/assets/43a94b1b-e196-4d15-a5f0-50be6d521791" />

<img width="428" height="421" alt="image" src="https://github.com/user-attachments/assets/bcc5bda6-e1ea-43f2-88bf-6fc9a3685c1a" />

<img width="428" height="420" alt="image" src="https://github.com/user-attachments/assets/20bdefe5-f523-45d1-acb0-ae6d3aa57f8c" />

<img width="415" height="415" alt="image" src="https://github.com/user-attachments/assets/294b0c9a-fc36-40a9-a2dd-cee9714a3fac" />

## Result
Thus, smoothing filters and sharpening filters are successfully implemented using OpenCV.

The smoothing filters reduce noise and improve image quality, while sharpening filters enhance edges and details for better feature extraction.
