# THRESHOLDING
## Aim :
To segment the image using global thresholding, adaptive thresholding and Otsu's thresholding using python and OpenCV.

## Software Required :
1. Anaconda - Python 3.7
2. OpenCV

## Algorithm :

### Step1 :
Load the original image using cv2.imread() and convert it from BGR to RGB. Also, load the grayscale version of the image for further processing.

### Step2 :
Apply different global thresholding methods like binary, inverse binary, to-zero, to-zero inverse, and truncate using cv2.threshold().


### Step3 :
Use Otsu's method to automatically determine the threshold value and segment the grayscale image into foreground and background.

### Step4 :
Implement adaptive thresholding (mean and Gaussian) using cv2.adaptiveThreshold() to handle varying lighting conditions in different parts of the image.

### Step5 :
Use matplotlib to visualize the original image and the thresholded results side by side in subplots, with appropriate titles for each technique used.

## Program :
```py
Developed By : MOHAMED ATHIL B
Register No : 212222230081
```
```py
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the Image and convert to grayscale
image = cv2.imread("nature.jpg")  # Read the image using imread
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)  # Convert the color from BGR to RGB
image_gray = cv2.imread("nature.jpg", 0)  # Grayscale image

# Use Global thresholding to segment the image
ret, thresh_dipt1 = cv2.threshold(image_gray, 86, 255, cv2.THRESH_BINARY)
ret, thresh_dipt2 = cv2.threshold(image_gray, 86, 255, cv2.THRESH_BINARY_INV)
ret, thresh_dipt3 = cv2.threshold(image_gray, 86, 255, cv2.THRESH_TOZERO)
ret, thresh_dipt4 = cv2.threshold(image_gray, 86, 255, cv2.THRESH_TOZERO_INV)
ret, thresh_dipt5 = cv2.threshold(image_gray, 100, 255, cv2.THRESH_TRUNC)

# Use Otsu's method to segment the image
ret, thresh_dipt6 = cv2.threshold(image_gray, 0, 255, cv2.THRESH_BINARY + cv2.THRESH_OTSU)

# Use Adaptive thresholding to segment the image
thresh_dipt7 = cv2.adaptiveThreshold(image_gray, 255, cv2.ADAPTIVE_THRESH_MEAN_C, cv2.THRESH_BINARY, 11, 2)
thresh_dipt8 = cv2.adaptiveThreshold(image_gray, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C, cv2.THRESH_BINARY, 11, 2)

# Display the results
titles = ["Gray Image", "Threshold Image (Binary)", "Threshold Image (Binary Inverse)", "Threshold Image (To Zero)",
          "Threshold Image (To Zero-Inverse)", "Threshold Image (Truncate)", "Otsu", "Adaptive Threshold (Mean)",
          "Adaptive Threshold (Gaussian)"]

images = [image_gray, thresh_dipt1, thresh_dipt2, thresh_dipt3, thresh_dipt4, thresh_dipt5, thresh_dipt6, thresh_dipt7, thresh_dipt8]

for i in range(0, 9):
    plt.figure(figsize=(10, 10))
    plt.subplot(1, 2, 1)
    plt.title("Original Image")
    plt.imshow(image_rgb)
    plt.axis("off")
    plt.subplot(1, 2, 2)
    plt.title(titles[i])
    if i == 0:
        plt.imshow(images[i], cmap='gray')  # Display grayscale image
    else:
        plt.imshow(images[i], cmap='gray')  # Display thresholded images
    plt.axis("off")
    plt.show()

```
## Output :

### Original Image
![image](https://github.com/user-attachments/assets/b5ed6d15-826c-4d7a-a0d1-209b288358ad)

### Global Thresholding
![image-1](https://github.com/user-attachments/assets/ed913bc4-5bb6-4ccd-a5b0-b1e94f5fff53)
![image-2](https://github.com/user-attachments/assets/a970604e-252c-45ac-a990-a89cf4514a5b)
![image-3](https://github.com/user-attachments/assets/ca03b4bc-c165-4606-9e11-9e33982db0c6)
![image-4](https://github.com/user-attachments/assets/5e50a329-9156-4fb0-b899-af6838189bdd)
![image-5](https://github.com/user-attachments/assets/55630f8b-f2ac-42d8-8896-30a17db76681)


### Adaptive Thresholding
![image-7](https://github.com/user-attachments/assets/a4fd1a86-6cc0-4b9f-a785-40a0f515a802)
![image-8](https://github.com/user-attachments/assets/a5f0a01a-304b-46ef-abcb-1f03a7a13852)



### Optimum Global Thesholding using Otsu's Method
![image-6](https://github.com/user-attachments/assets/8c115e1e-87e4-4132-883a-66d92d45b402)



## Result :
Thus the images are segmented using global thresholding, adaptive thresholding and optimum global thresholding using python and OpenCV is executed successfully.
