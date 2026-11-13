# Geometric Transformations Using OpenCV

---

## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

- Image Translation  
- Image Scaling (Resizing)  
- Image Shearing  
- Image Reflection (Flipping)  
- Image Rotation  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image in color mode.

### Step 3: Image Translation
- Create a translation matrix to shift the image  
- Move the image 50 pixels to the right and 80 pixels down  
- Apply transformation using `cv2.warpAffine()`  
- Display original and translated images  

### Step 4: Image Scaling
- Resize the image to 0.5× (downscale)  
- Resize the image to 2× (upscale)  
- Use `cv2.resize()`  
- Display original, downscaled, and upscaled images  

### Step 5: Image Shearing
- Create transformation matrices for:
  - Horizontal shearing  
  - Vertical shearing  
- Apply transformations using `cv2.warpAffine()`  
- Display original and sheared images  

### Step 6: Image Reflection
- Perform flipping using `cv2.flip()`:
  - Horizontal reflection  
  - Vertical reflection  
  - Both axes  
- Display all reflected images  

### Step 7: Image Rotation
- Create rotation matrices for:
  - 45° rotation  
  - 90° rotation  
- Use `cv2.getRotationMatrix2D()` and `cv2.warpAffine()`  
- Display original and rotated images  

---

##  Program

### Developed By:
**Name:** 
SHAABIN R S

### Register No:
212224230259

Import the required libraries: OpenCV, NumPy, and Matplotlib.
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

Read the input image in color mode.
```
image = cv2.imread(r"C:\Users\admin\OneDrive\Desktop\ai assistant\WhatsApp Image 2026-10-30 at 8.45.52 AM.jpeg", cv2.IMREAD_COLOR)

image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(6,6))
plt.imshow(image_rgb)
plt.title("Original Image")
plt.axis("off")
plt.show()
```

Image Translation
```
rows, cols = image.shape[:2]

translation_matrix = np.float32([
    [1, 0, 50],
    [0, 1, 80]
])

translated = cv2.warpAffine(image, translation_matrix, (cols, rows))
translated_rgb = cv2.cvtColor(translated, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(10,5))

plt.subplot(1,2,1)
plt.imshow(image_rgb)
plt.title("Original")
plt.axis("off")

plt.subplot(1,2,2)
plt.imshow(translated_rgb)
plt.title("Translated")
plt.axis("off")

plt.show()
```

Image Scaling
```
downscaled = cv2.resize(image, None, fx=0.5, fy=0.5)
upscaled = cv2.resize(image, None, fx=2, fy=2)

downscaled_rgb = cv2.cvtColor(downscaled, cv2.COLOR_BGR2RGB)
upscaled_rgb = cv2.cvtColor(upscaled, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(image_rgb)
plt.title("Original")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(downscaled_rgb)
plt.title("Downscaled (0.5x)")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(upscaled_rgb)
plt.title("Upscaled (2x)")
plt.axis("off")

plt.show()
```

Image Shearing
```
rows, cols = image.shape[:2]

horizontal_matrix = np.float32([
    [1, 0.5, 0],
    [0, 1, 0]
])

vertical_matrix = np.float32([
    [1, 0, 0],
    [0.5, 1, 0]
])

horizontal_shear = cv2.warpAffine(image, horizontal_matrix, (cols + 150, rows))
vertical_shear = cv2.warpAffine(image, vertical_matrix, (cols, rows + 150))

horizontal_rgb = cv2.cvtColor(horizontal_shear, cv2.COLOR_BGR2RGB)
vertical_rgb = cv2.cvtColor(vertical_shear, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(image_rgb)
plt.title("Original")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(horizontal_rgb)
plt.title("Horizontal Shearing")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(vertical_rgb)
plt.title("Vertical Shearing")
plt.axis("off")

plt.show()
```

Image Reflection
```
horizontal_flip = cv2.flip(image, 1)
vertical_flip = cv2.flip(image, 0)
both_flip = cv2.flip(image, -1)

horizontal_rgb = cv2.cvtColor(horizontal_flip, cv2.COLOR_BGR2RGB)
vertical_rgb = cv2.cvtColor(vertical_flip, cv2.COLOR_BGR2RGB)
both_rgb = cv2.cvtColor(both_flip, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(15,5))

plt.subplot(1,4,1)
plt.imshow(image_rgb)
plt.title("Original")
plt.axis("off")

plt.subplot(1,4,2)
plt.imshow(horizontal_rgb)
plt.title("Horizontal Reflection")
plt.axis("off")

plt.subplot(1,4,3)
plt.imshow(vertical_rgb)
plt.title("Vertical Reflection")
plt.axis("off")

plt.subplot(1,4,4)
plt.imshow(both_rgb)
plt.title("Both Axes")
plt.axis("off")

plt.show()
```

Image Rotation
```
rows, cols = image.shape[:2]
center = (cols // 2, rows // 2)

rotation45 = cv2.getRotationMatrix2D(center, 45, 1)
rotation90 = cv2.getRotationMatrix2D(center, 90, 1)

rotated45 = cv2.warpAffine(image, rotation45, (cols, rows))
rotated90 = cv2.warpAffine(image, rotation90, (cols, rows))

rotated45_rgb = cv2.cvtColor(rotated45, cv2.COLOR_BGR2RGB)
rotated90_rgb = cv2.cvtColor(rotated90, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(image_rgb)
plt.title("Original")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(rotated45_rgb)
plt.title("45° Rotation")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(rotated90_rgb)
plt.title("90° Rotation")
plt.axis("off")

plt.show()
```


---

##  Output

### Image Translation
- Original image is displayed  
- Translated image (shifted right and down) is displayed

<img width="431" height="526" alt="image" src="https://github.com/user-attachments/assets/8d487620-3759-4ca4-b34c-bd55efd51b19" />




### Image Scaling
- Original image is displayed  
- Downscaled image (0.5×) is displayed  
- Upscaled image (2×) is displayed

<img width="692" height="382" alt="image" src="https://github.com/user-attachments/assets/2a44af6f-951b-4ca9-b965-b8f3acfd684c" />




### Image Shearing
- Original image is displayed  
- Horizontally sheared image is displayed  
- Vertically sheared image is displayed

<img width="425" height="530" alt="image" src="https://github.com/user-attachments/assets/89586302-5ecb-44ff-935a-ba9ad01d5ccc" />




### Image Reflection
- Original image is displayed  
- Horizontally flipped image is displayed  
- Vertically flipped image is displayed  
- Both-axis flipped image is displayed

<img width="411" height="523" alt="image" src="https://github.com/user-attachments/assets/afc58b19-1450-4b09-8ead-251b8df83dc3" />

  

### Image Rotation
- Original image is displayed  
- 45° rotated image is displayed  
- 90° rotated image is displayed  

<img width="440" height="517" alt="image" src="https://github.com/user-attachments/assets/26a1bc03-4ab7-4cdc-80db-24a10fb4e3fb" />



---

##  Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
