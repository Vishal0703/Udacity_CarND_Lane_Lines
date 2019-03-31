# **Finding Lane Lines on the Road** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

Overview
---

When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

## Reflection

### 1. Pipeline...

The actual pipeline is draw_lane_lines(), where the modifications to image are as follows:

1. Grayscaling the image
2. Applying gaussian Blur and Canny Edge Detection
3. Using ROI masking and removing the rest of the image.
4. Finding possible lines using Hough Transform
5. Using draw_lines() function to draw the lines...

#### draw_lines():

1. Divide the lines found by Hough transform into positive and negative classe based on their slopes.

For positive class:

2. Select the longest line.
3. Find all lines with their slopes within a certain window of the slope of the longest line. (window = 0.01 used).
4. Use the line_maker() ofunction n all of them to find the extrapolated end points of the lines.
5. Use cv2.line() to draw those lines into the images.

Repeat step 2-5 for negative class too.

#### line_maker():

Extrapolates a given line such that its end points lie on the image's top and bottom boundaries. Given 2 points 
of the line, it first calculates which point is nearest to which edge and extrapolates them.

### 2. Potential shortcomings with the current pipeline

1. Will be bad if both the lanes are pointing to one side, i.e. if the road has left curvature or right curvature.
2. The method only finds straight lines.

### 3. Possible improvements to the current pipeline

Possible improvements would be:

1. Use the image centre as the referral point for dividing the lines into left_line and right_line buckets.
2. Use a 2-D curve to fit the lines rather than a 1-D line.

The Project
---

## If you have already installed the [CarND Term1 Starter Kit](https://github.com/udacity/CarND-Term1-Starter-Kit/blob/master/README.md) you should be good to go!   If not, you should install the starter kit to run this project. ##

**Step 1:** Set up the [CarND Term1 Starter Kit](https://classroom.udacity.com/nanodegrees/nd013/parts/fbf77062-5703-404e-b60c-95b78b2f3f9e/modules/83ec35ee-1e02-48a5-bdb7-d244bd47c2dc/lessons/8c82408b-a217-4d09-b81d-1bda4c6380ef/concepts/4f1870e0-3849-43e4-b670-12e6f2d4b7a7) if you haven't already.

**Step 2:** Open the code in a Jupyter Notebook

 If you are unfamiliar with Jupyter Notebooks, check out [Udacity's free course on Anaconda and Jupyter Notebooks](https://classroom.udacity.com/courses/ud1111) to get started.

Jupyter is an Ipython notebook where you can run blocks of code and see results interactively.  All the code for this project is contained in a Jupyter notebook. To start Jupyter in your browser, use terminal to navigate to your project directory and then run the following command at the terminal prompt (be sure you've activated your Python 3 carnd-term1 environment as described in the [CarND Term1 Starter Kit](https://github.com/udacity/CarND-Term1-Starter-Kit/blob/master/README.md) installation instructions!):

`> jupyter notebook`

A browser window will appear showing the contents of the current directory.  Click on the file called "P1.ipynb".  Another browser window will appear displaying the notebook.  Follow the instructions in the notebook to run the project.  

