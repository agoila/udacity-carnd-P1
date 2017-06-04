# **Finding Lane Lines on the Road** 

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on the work in a written report


[//]: # (Image References)

[image1]: ../resized_images/solidWhiteCurve1.jpg "Original"
[image2]: ../examples/grayscale.jpg "Grayscale"
[image3]: ../resized_images/solidWhiteCurve2.jpg "Canny detected lines"
[image4]: ../resized_images/solidWhiteCurve4.jpg "Region Masking"
[image5]: ../resized_images/solidWhiteCurve3.jpg "Hough Transform"
[image6]: ../resized_images/solidWhiteCurve5.jpg "Final image"

---

### The Pipeline

There were 5 broad steps to my pipeline. For every input image:

* Convert to **grayscale**.
* Apply **Gaussian smoothing/blurring**, using a 5x5 kernel.
* Run **Canny Edge Detection**.
* Apply **Region Masking**.
* Run **Hough Line Transform**.

### The draw_lines() method

In order to draw a single line on the left and right lanes, I modified the draw_lines() function using the following method:

* Run a for-loop over the output of the Hough Lines function (**cv2.HoughLinesP()**) to read in the points (x,y).
* Sort the points into left and right x,y lists based on a pre-defined range of slopes (slope_l, slope_r).
* Average out the x and y points, and calculate the mean slopes. 
* Calculate the y-intercepts from the means calculated above, using equation: **b = y - mx**
* With the ROI y-coordinates as reference, calculate the corresponding x-coordinates using the intercepts and mean slopes calculated before (**x = (y - b) / m**)
* With the new (x,y) points for left and right side, draw the respective lines using **cv2.line()**.

Following are the images showing the sequence of steps followed in the pipeline: 

#### Original image
![alt text][image1]

#### Grayscale conversion
![alt text][image2]

#### Canny Edge Detection
![alt text][image3]

#### Region Masking
![alt text][image4]

#### Hough Line Transform
![alt text][image5]

#### Final processed image
![alt text][image6]


### Potential shortcomings


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### Possible further improvements

A possible improvement would be to ..

Another potential improvement could be to ...

