# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # "Image References"

[initial]: img/initial.png
[edges]: img/edges.png
[hough]: img/hough.png
[final]: img/final.png

---

This is a simple project using Python and OpenCV to detect lanes on a road solely from an image.

### Reflection

### 1. Describe your pipeline.

![alt text][initial]

First, images were converted to grayscale, blurred and the Canny Edge Detection algorithm was applied. To simplify detection, a bounding polygon was used to mask away parts of the image that did not contain lanes. This was drawn based on the examples and test images provided.

![alt text][edges]

From here the Hough transform was used to locate the lane markers within the boundary from the previous step.

![alt text][hough]

Finally the `draw_lines` function finds the average linear equation of all the lines on each side. These new equations are used to calculate end points for these average lines, which are drawn in red on the initial image.

![alt text][final]



### 2. Identify potential shortcomings with your current pipeline.

This pipeline has been fit to the limited examples and test data. Specifically the Hough parameters are fit to produce long lines. 

* Only lines are used and only two points are used to draw those lines. Very long, sweeping curves have a chance at being handled, but a sharp turn or bend in the road will cause the lines to be incorrect.
* All conditions are perfect in this data, and the pipeline assumes that. Nighttime, snow, road color, construction, non-ideal human drivers are small subset of the possible ways the real world could throw off this simple detection.


### 3. Suggest possible improvements to your pipeline.

* Fit lanes to curves or ellipses rather than linear equations for a more realistic model.
* Use other image processing techniques to condition the image to be more robust to different looking roads.
* Attempt briefly maintain or predict line position if no lane markers can be found.
* Classify type of lane marker: yellow lines, white lines, solid, dashed, etc.
* Support seeing temporary lane markers. Cones or other objects often indicate lanes in construction or other situations.