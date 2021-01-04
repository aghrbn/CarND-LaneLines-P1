# **Finding Lane Lines on the Road** 


### This document is the description of the lane finding project 


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"
[image2]: ./test_images_output/solidWhiteCurve.jpg "Processed Image"


### Reflection

### 1. Description of the pipeline

The pipeline consisted of 5 steps:

* First, the image is converted to grayscale since Canny edge detector works on grayscale
* Gaussian blur filter is then applied to smooth the image and reduce noise
* Canny edge detection is applied to the blured image to detect edges in the image
* A region of interest is created in the image to contain the lanes of interest only
* The Hough transform is applied to the region of interest to detect lanes

An example of the processed image with the pipeline is shown below:

![alt text][image2]

In order to draw a single line on the left and right lanes, the following steps were taken:

* The lines detected by the Hough function are sent as an input to the function
* For each line, the slope of the line and its intercept is calculated
* The slopes are filtered based on a threshold to eliminate outliers
* The left and right lines are captured by determining if the slope is negative or or positive
* The average of the slopes and intercepts are taken
* A final line is drawn based on the average values



### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the car is approaching sharp turns on the road. The algorithm may fail because it is not designed to detect curves. 


### 3. Suggest possible improvements to your pipeline

A smarter way to extrapolate the lines would be better. Also, lines are shaking in the video. A stable line is better.


