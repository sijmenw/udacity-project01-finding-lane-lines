# **Finding Lane Lines on the Road**
---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

The work can be found in P1.ipynb

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. Steps were completed in the following order:
1. to grayscale
2. apply gaussian blur
3. apply canny
4. apply ROI
5. apply hough
6. combine hough lines with original image to produce result

[image1]: ./example.png "Example"

I modified the draw_line function to include the following steps:
for each proposed line piece, the slope is calculated.

if 0.4 < slope < 2.5, the line piece is in group 'left'
if -0.4 > slope > -2.5, the line piece is in group 'right'

for each group, the average slope is calculated as well as the middle point of all start and end points of all line pieces

the slope and the average point are then used to create a line y = mx + b for both the left and the right lane

the beginning and ending points for each of the lines are calculates such that they do not exceed the ROI.

The lines are then drawn on the image.

### 2. Identify potential shortcomings with your current pipeline
The lines shock a lot between images, it seems noise is still playing a fairly large role and messing with the accuracy


### 3. Suggest possible improvements to your pipeline
the detection could be improved by adding a layer of outlier detection to prevent non-line parts from messing with the results

another improvement could be to use lines detected in earlier frames to predict the location of the next
