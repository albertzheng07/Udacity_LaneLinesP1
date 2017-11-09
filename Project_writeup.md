# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/Gaussian_Blur.jpg "Gaussian Blur"

[image2]: ./examples/Edge.jpg "Edge"

[image3]: ./examples/Hough.jpg "Hough"

[image4]: ./test_images_step1_output/solidWhiteCurve.jpg "Initial Output"

[image5]: ./test_images_extrap_output/solidWhiteCurve.jpg "Final Output"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

I designed my pipeline using the series of helper functions provided. 

Step 1) Similiar to the lesson, I started off with grayscaling the image and then doing a gaussian blur for smoothing with a selected kernal size of 3. Here is the image after applying the gaussian smoothing.

![alt text][image1]


Step 2) I called the canny function to detect the edges on the smoothed and gray scaled image. After some tweaking based on the output of the edge output, I decided on a high threshold of 150 and a low threshold of 50. 

![alt text][image2]


Step 3) I built a mask based on the detecting the lines only in the frame of the image which mattered similar to the image output expectation. 

Step 4) After applying a mask, I ran the hough transform to detect lines within region of interest. I ended up tweaking the distance resolution and increasing the thresholds requiring minimum number of pixels for a line and the gap between pixels. I tuned the line detection based on the output of the image similar to the example below.

![alt text][image3]

Step 5) I drew the lines on the final image to produce the final result. 

![alt text][image4]

Step 6) I modified the draw lines function to produce an extrapolated set of lines to connect the initially seperated lines. My method was to find the slopes of the lines found and then seperate the slopes into their direction whether they be positive or negative. After finding the slope direction, I took the end points of all the slopes and selected it as the final line to draw.

![alt text][image5]



### 2. Identify potential shortcomings with your current pipeline

One possible short coming is the robustness of the mask. If the lines were not always within the same mask region, the mask would filter out the lines of interest.

I noticed some jumps in some of the lines frame to frame in the video output. My line extrapolation isn't very robust to erroneous detection of a slope not making physical sense. It will simply just try to pick the end points of whichever points that are found. Ideally, this should only capture line segments that would have slopes that are within expectation of how lines would look on a highway. I ran out of time to average the lines and found that taking the end points of all the slopes for sufficient for the implementation.


### 3. Suggest possible improvements to your pipeline

One possible improvement is to make the mask more dynamic in order to detect the region of interest. There could be a better convergence on selecting the mask rather than tweaking it manually. There's also a lot of manual tweaking to ensure the line segments look valid regarding the number of values picked. If there was a way to setup a metric in order to validate that a line is indeed captured, an optimization could be written to minimize this cost in order to come up with the parameters computationally.
