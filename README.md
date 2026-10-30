# Experiment 2: Image Acquisition Using Web Camera

## Aim

To write a Python program using OpenCV to capture images from a webcam, save the captured frame as a JPG file, display live video, resize video frames, and rotate video frames.

## Software Used

- Python
- Jupyter Notebook
- OpenCV (`cv2`)
- NumPy
- Matplotlib

## Algorithm

1. Import the required libraries.
2. Initialize the webcam using `cv2.VideoCapture(0)`.
3. Capture a frame from the webcam.
4. Save the captured frame as `captured_frame.jpg`.
5. Read and display the captured image.
6. Capture and display live video frames.
7. Resize the video frames using `cv2.resize()`.
8. Rotate the video frames by 90 degrees clockwise using `cv2.rotate()`.
9. Release the webcam after completing the operations.

## Program

### 1. Import Required Libraries

```python
import cv2
import matplotlib.pyplot as plt
from IPython.display import clear_output
import time
```

### 2. Image Capture and Saving

```python
cap = cv2.VideoCapture(0)

if not cap.isOpened():
    print("Camera not available")
else:
    ret, frame = cap.read()

    if ret:
        cv2.imwrite('captured_frame.jpg', frame)
        print("Image saved successfully")
    else:
        print("Unable to capture image")

cap.release()
```

### 3. Display Captured Image

```python
captured_image = cv2.imread('captured_frame.jpg')

if captured_image is not None:
    plt.imshow(cv2.cvtColor(captured_image, cv2.COLOR_BGR2RGB))
    plt.title('Captured Frame')
    plt.axis('off')
    plt.show()
else:
    print("Captured image not found")
```

### 4. Live Video Display

```python
cap = cv2.VideoCapture(0)

if cap.isOpened():
    for i in range(50):
        ret, frame = cap.read()

        if not ret:
            break

        frame_rgb = cv2.cvtColor(frame, cv2.COLOR_BGR2RGB)

        clear_output(wait=True)
        plt.imshow(frame_rgb)
        plt.title('Live Video')
        plt.axis('off')
        plt.show()

        time.sleep(0.05)

cap.release()
```

### 5. Video Resizing

```python
cap = cv2.VideoCapture(0)

if cap.isOpened():
    for i in range(50):
        ret, frame = cap.read()

        if not ret:
            break

        resized_frame = cv2.resize(frame, (100, 150))
        frame_rgb = cv2.cvtColor(resized_frame, cv2.COLOR_BGR2RGB)

        clear_output(wait=True)
        plt.imshow(frame_rgb)
        plt.title('Resized Video')
        plt.axis('off')
        plt.show()

        time.sleep(0.05)

cap.release()
```

### 6. Video Rotation

```python
cap = cv2.VideoCapture(0)

if cap.isOpened():
    for i in range(50):
        ret, frame = cap.read()

        if not ret:
            break

        rotated_frame = cv2.rotate(frame, cv2.ROTATE_90_CLOCKWISE)
        frame_rgb = cv2.cvtColor(rotated_frame, cv2.COLOR_BGR2RGB)

        clear_output(wait=True)
        plt.imshow(frame_rgb)
        plt.title('Rotated Video')
        plt.axis('off')
        plt.show()

        time.sleep(0.05)

cap.release()
```

## Expected Output

1. Captured image saved as `captured_frame.jpg`.
2. Captured image displayed successfully.
3. Live webcam video displayed.
4. Resized video displayed with dimensions 100 × 150 pixels.
5. Video rotated 90 degrees clockwise and displayed.

## Result

Thus, the Python program for image acquisition using a webcam was implemented using OpenCV. Image capturing, saving, displaying, resizing, and rotation operations were demonstrated.
