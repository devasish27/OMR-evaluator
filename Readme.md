# Optical Mark Recognition (OMR):
It is a technology that allows computers to read and interpret human-marked forms. OMR is used in a variety of applications,
including surveys, exams, and ballots. OMR evaluation is the process of determining whether a scanned OMR form has been correctly filled out. This is done 
by comparing the scanned image of the form to a template of the correctly filled out form. There are a number of different methods that can be used 
for OMR evaluation. One common method is to use a template matching algorithm. This algorithm compares the scanned image of the form to the template 
and determines whether the two match. Another method that can be used for OMR evaluation is to use a neural network. 

A neural network is a type of machine learning algorithm that can be trained to recognize patterns in data. In the case of OMR evaluation, a neural network
can be trained to recognize the correct markings on an OMR form. Here are some of the benefits of OMR evaluation: It is a fast and efficient way to evaluate 
OMR forms. It is accurate and reliable. It can be used to evaluate a variety of different OMR forms. 
Here are some of the challenges of OMR evaluation: The quality of the scanned image can affect the accuracy of the evaluation. 
The template must be accurate and up-to-date. The method that is used for evaluation must be appropriate for the specific application.


OMR sheet scanner and test grader using OMR, Python, and OpenCV The goal of this blog post is to build a bubble sheet scanner and test grader using Python 
and OpenCV. To accomplish this, our implementation will need to satisfy the following 7 steps.
OpenCV is the huge open-source library for the computer vision, machine learning, and image processing and now it plays a major role in real-time operation which
is very important in today’s systems. By using it, one can process images and videos to identify objects, faces, or even handwriting of a human.
When it integrated with various libraries, such as NumPy, python is capable of processing the OpenCV array structure for analysis. 

To Identify image pattern and its various features we use vector space and perform mathematical operations on these features Optical Mark Reader (OMR) is 
the technology of electronically extracting data from marked fields such as checkboxes or bubbles from pre-printed forms. 

OMR technology scans a printed form and reads from predefined positions. It records the data where marks are made on the form. 
This is widely used for processing the large number of hand-filled forms which have to be processed quickly and with great accuracy The code first loads 
the answer key and student response images as grayscale images. Then, it performs image processing to extract the OMR bubbles. 
This is done by thresholding the images to convert them to binary images, and then finding contours in the images. The contours are sorted
from left to right, and then the selected answers are compared by comparing the centroid positions of the contours. 

# ALGORITHM :

1. Perform Image Pre-processing: 
  a. Convert the image to grayscale. 
  b. Apply Gaussian blurring to reduce noise and smoothen the image. 
  c. Use erosion and dilation to remove noise near black marks. This can be achieved using morphological operations like cv2.erode() and cv2.dilate().

2. Crop the Image: 
  a. Find the bounding boxes of the black marks using the contours (to be done in step 3). 
  b. Crop the image based on the bounding boxes to extract the regions containing the black marks. 

3. Find Contours and Centroids:
  a. Threshold the pre-processed image to create a binary image. 
  b. Find contours in the binary image using cv2.findContours().
  c. Calculate the centroids of the contours using cv2.moments(). 

4. Find Angle of Rotation: 
  a. Sort the contours based on their y-coordinate to identify the top and bottom black marks. 
  b. Calculate the angle between the line connecting the centroids of the top and bottom marks and the horizontal axis.

5. Rotate the Original Image: 
  a. Rotate the original image by the calculated angle using cv2.warpAffine().

6. Check Key with Responses: 
  a. Pre-process the rotated image for reading responses (if required). 

7. Mark Correct, Incorrect, and Unanswered Responses: 
a. Compare the candidate's responses with the correct answers from the key. 
b. Mark the responses in the image with green for correct, red for wrong, and yellow for unanswered. 

8. Count Correct, Incorrect, and Unanswered Responses: 
a. Loop through the responses and compare with the key. b. Keep a count of correct, incorrect, and unanswered responses.
