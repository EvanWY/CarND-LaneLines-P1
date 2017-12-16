# **Finding Lane Lines on the Road**

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/solidYellowLeft.jpg
[image2]: ./test_videos_output/solidYellowLeftScreenShot.png

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 

1. Converted the images to grayscale
2. Used gaussian blur to blur the image
3. Find edges using canny edge detector
4. Mask only the area that will have the lane mark
5. Transform to hough space to find lines

![alt text][image1]

In order to draw a single line on the left and right lanes, I modified the draw_lines() function with this method.

1. Use (x1-x2) * (y1-y2) to tell if a line is left or right lane
2. Keep the longest lines for both left and right lane
3. Use the lane from last frame to calculate the new lane, so that it's more stable

![alt text][image2]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the car direction change rapidly, because the lane tracking algorithm relies on previous frame data.

Another shortcoming is that it couldn't handle corner very well because it assumes that lane line are straight.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use a line finding algorithm that support detecting curve to replace hough.

Another potential improvement could be to make use of the color of the road.
