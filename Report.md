# **Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

### Reflection

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
