# **Finding Lane Lines on the Road** 

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on the work in a written report


[//]: # (Image References)

[image1]: ../examples/grayscale.jpg "Grayscale"

---

### Reflection

### The Pipeline

There were 5 broad steps to my pipeline. For every input image:

* Convert to **grayscale**.
* Apply **Gaussian smoothing/blurring**, using a 5x5 kernel.
* Run **Canny Edge Detection**.
* Apply **Region Masking**.
* Run **Hough Transform**.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function using the following method:

* Run a for-loop over the output of the Hough Lines function (**cv2.HoughLinesP()**) to read in the points (x,y).
* Sort the points into left and right x,y lists based on a pre-defined range of slopes (slope_l, slope_r).
* Average out the x and y points, and calculate the mean slopes. 
* Calculate the y-intercepts from the means calculated above, using equation: **b = y - mx**
* Using the ROI y-coordinates as reference, calculate the corresponding x-coordinates with intercepts and mean slopes calculated before.
* With the new (x,y) points for left and right side, draw the respective lines using **cv2.line()**.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...

