In this exercise, an eye detection application written in python is use to perform eye detection
using Haar-Cascade Classifier from OpenCV-Python library module for faces detection followed by eye detection.

Outline of the program is:
- Load jpg image (preferably the size of the frontal face of image size of 300x300).
- Convert RGB image to greyscale image.
- Find where the face is in the image using Haar-Cascade Classifier trained for detection of frontal face.
- Using the face bounding box, cut a region from the bounding box (x, y, w, h) of the face to create an 
  area where the eyes are located. The width and height of the face bounding box is w and h respectively.
  The eye segment is used to locate exact location of the eye in the image and to minimise misclassification
  of eye with other objects. It is a rectangle of (x, (y + 0.15h), w, 0.4h)) .
  The top left corner coordinateof the eye bounding box is x and y+0.15h.  The width and height of
  the eye segment is w and 0.4h respectively. This area is approximately 
- Find where both eyes are located.

Discussion
Recent development in deep learning has improve the accuracy of detection of faces over traditional
method of computation. Thus, for the detection of the faces, Haar-Cascade Classifier is use in this
exercise. It uses Haar Wavelet to perform wavelet transform on the image to extract features
and these features are the input to a ada boosting decision tree classifier.

As seen in testimg04.jpg, it wrongly detect the dress the lady is wearing as a face. This could be
remedy by setting the parameter number of nearest neighbour to a higher number But this could
cause some image of people not able to satisty this condition and miss the detection. Thus, number
of nearest neighbour is set to 2. 

For images captured with people in front of the webcam, the camera take the image of the area in 
the region around the head. This could avoild misclassification by reducing multiple objects in the
image.

In testimg05.jpg, the face detector is not able to detect the eyes when someone is wearing a glass.
Similarly, constraining the web camera to having people in front without wearing sunglass can avoid
this issue.

In testimg06.jpg, faces of some people are not detected due to the close proximity of a group of 
people in the image. Constraining only 1 person when capturing the image will alleviate this problem.

It can be seen that Haar-Cascade Classifier is unable to detect faces in some scenario. However, for 
telemedicine application with webcam where the patient appear in front of the camera, the
performance of the Haar-Cascade Classifier is relatively good.

Future work:
- In cases where either no eye or 1 eye is detected using Haar-Cascade Classifier for eye detection,
additional processing is performed on the eye bounding box pixels using Histogram of Oriented 
Gradients (HOG) representation as feature selection for the classifier. Another method is to used
edge detection algorithm such as Canny Edge Detection, followed by HoughCircles to detect the iris.

The structure of this application is shown in the File directory below:
- -img
    - testimg01.jpg
    - testimg02.jpg
    - testimg03.jpg
    - testimg04.jpg
    - testimg05.jpg
    - testimg06.jpg
- -eye_detection.ipynb
- -frontalface.xml
- -eye.xml
- -readme.md