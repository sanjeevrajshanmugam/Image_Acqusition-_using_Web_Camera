# EXP 02: Image Acquisition using Web Camera

## Aim
 
To write a python program using OpenCV to capture the image from the web camera and do the following image manipulations.<br>
i) Write the frame as JPG <br>
ii) Display the video <br>
iii) Display the video by resizing the window<br>
iv) Rotate and display the video

## Software Used
Anaconda - Python 3.7

## Algorithm
### Step 1: 
Start the webcam using cv2.VideoCapture(0) and begin reading frames.
<br>

### Step 2: 
Capture and save a frame as a JPG file using cv2.imwrite().
<br>

### Step 3: 
Display the live video continuously in a window.
<br>

### Step 4:
Resize the frame to half its original size and display the smaller video.
<br>

### Step 5:
Rotate the resized frame (180°) and display it along with the normal frames.
<br>

### Step 6: 
Stop the webcam and close all windows when the user presses ‘q’.
<br>

## Program

### Developed By: SANJEEV RAJ.S
### Register No: 212223220096

## i) Write the frame as JPG file
```python
import cv2
obj = cv2.VideoCapture(0)
while(True):
    cap,frame = obj.read()
    cv2.imshow('photo.jpg',frame)
    cv2.imwrite("pic.jpg",frame)
    if cv2.waitKey(1) == ord('q'):
        break
obj.release()
```



## ii) Display the video
```python
import cv2
img = cv2.VideoCapture(0)
while(True):
    imagee,frame = img.read()
    cv2.imshow('video',frame)
    if cv2.waitKey(1) == ord('q'):
        break
img.release()
cv2.destroyAllWindows()
```



## iii) Display the video by resizing the window
```python
import numpy as np
import cv2
cap=cv2.VideoCapture(0)
while True:
    ret,frame=cap.read()
    width=int(cap.get(3))
    height=int(cap.get(4))
    image=np.zeros(frame.shape,np.uint8)
    smaller_frame=cv2.resize(frame,(0,0),fx=0.5,fy=0.5)
    image[:height//2, :width//2]=smaller_frame
    image[height//2:, :width//2]=smaller_frame
    image[:height//2, width//2:]=smaller_frame
    image[height//2:, width//2:]=smaller_frame
    cv2.imshow('resizedvideo',smaller_frame)
    if cv2.waitKey(1)==ord('q'):
        break
cap.release()
cv2.destroyAllWindows()
```



## iv) Rotate and display the video
```python
import cv2
import numpy as np
cap = cv2.VideoCapture(0)
while True:
    ret, frame = cap.read() 
    width = int(cap.get(3))
    height = int(cap.get(4))
    image = np.zeros(frame.shape, np.uint8) 
    smaller_frame = cv2.resize(frame, (0,0), fx = 0.5, fy=0.5)
    image[:height//2, :width//2] = cv2.rotate(smaller_frame,cv2.ROTATE_180)
    image[height//2:, :width//2] = smaller_frame 
    image[:height//2, width//2:] = smaller_frame
    image[height//2:, width//2:] = cv2.rotate(smaller_frame,cv2.ROTATE_180)
    cv2.imshow('rotatedvideo', image)
    if cv2.waitKey(1)==ord('q'):
        break
cap.release()
cv2.destroyAllWindows()
```


## Output

### i) Write the frame as JPG image
</br>
<img width="560" height="355" alt="Screenshot 2025-09-22 105820" src="https://github.com/user-attachments/assets/42adf864-f887-46db-8ec0-0a6d56fe4cf9" />


</br>


### ii) Display the video
</br>
<img width="493" height="350" alt="Screenshot 2025-09-22 105830" src="https://github.com/user-attachments/assets/b7408f67-9e7c-42f2-a3ed-d8c437175ce4" />


</br>


### iii) Display the video by resizing the window
</br>
<img width="280" height="418" alt="Screenshot 2025-09-22 105840" src="https://github.com/user-attachments/assets/c5c29324-87d4-42a0-b06a-c0988edae6a2" />


</br>



### iv) Rotate and display the video
</br>
<img width="311" height="416" alt="Screenshot 2025-09-22 105847" src="https://github.com/user-attachments/assets/f03b04c2-a16c-4a13-a35f-c32c8aab7f56" />


</br>





## Result
The image was successfully captured from the webcam, saved as a JPG file, and displayed as live video. The video was also shown in resized form and rotated, thus achieving all four image acquisition processes using OpenCV.
