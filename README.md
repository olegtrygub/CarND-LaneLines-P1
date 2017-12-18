# **Finding Lane Lines on the Road** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1. Pipeline description:

I used examples from the quizes in the lectures. 

My pipeline consisted of the next steps:
1. Converting to grayscale
2. Applying Gaussian blur
3. Running canny edge detection algorithm
4. Creating the mask
5. Line detection after applying hough transformation
6. Combining lines with the image

In order to draw a single line on the left and right lanes, I modified the draw_lines() function:
1. coordinates (k, b) of lines are calculated in the form of y = kx + b
2. lines are separated by the slope into 2 arrays
3. (k, b) parameters of lines are averaged using line length as weights


![example1](/test_images_output/solidWhiteCurve.jpg)
![example2](/test_images_output/solidWhiteRight.jpg)
![example3](/test_images_output/solidYellowCurve.jpg)
![example4](/test_images_output/solidYellowCurve2.jpg)
![example5](/test_images_output/solidYellowLeft.jpg)
![example6](/test_images_output/whiteCarLaneSwitch.jpg)



### 2. Project shortcomings

The main shortcoming would be what would happen when the lanes are not straight, as averaging of lines assumes they are more or less aligned, so identifiying lanes in the turn would be problematic, as lane closer to the car and further are not aligned.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be not to detect images on each frame in isolation, but use groups of images, as the next image provides some info about the lanes visible in the previous. 

Exploring more sophisticated shapes than straight lines also might improve lane detection for turns.
