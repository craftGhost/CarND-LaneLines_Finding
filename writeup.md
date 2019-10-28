# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

**My pipeline consisted of 7 steps.**

1. Converted the images to grayscale.

2. Applied gaussian smoothing.

3. Applied Canny edge detection.

4. Determined region of interests, it looks like a trapezoid.

5. Applied the Hough transform and created an image with hough lines drawn on it.

6. Created a "color" binary image to combine with line image.

7. Looped through all the images, saved all the processed images into assigned directory /test_images_output. (check the folder for result images)

**About draw_lines() function:**

1. Seperated lines to left or right by calculating their slopes, and excluded lines are almost vertical or horizontal.

2. For lines on the left, calculated their average x, y, and slope. Used y = mx + b to calculate average b. Did the same with lines on the right.

3. Used our threshold of region of interest y_min and y_max (lower and upper y of trapezoid) to calculated corresponding x1 and x2 since we already knew x = (y - b)/m.

4. Passed the variables x1, y_min, x2, y_max we obtained into cv2.line() to draw left and right lines individually on the image.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


1. The pipeline may not work well if there is shadow on the road or the environmental brightness is low.

2. It doesn't work for curved lane lines.

### 3. Suggest possible improvements to your pipeline

1. Improve the edge detection feature. Maybe HSV color space is better than RGB to work in low brightness environment.

2. We need some new techniques like distort the image to make it work for curved lane lines.