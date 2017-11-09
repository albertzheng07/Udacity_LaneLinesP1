# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

[image2]: ./examples/Edge.jpg "Edge"



---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

I designed my pipeline using the series of helper functions provided. 

Step 1) Similiar to the lesson, I started off with grayscaling the image and then doing a gaussian blur for smoothing with a selected kernal size of 3.

![alt text][image1]


Step 2) I called the canny function to detect the edges on the smoothed and gray scaled image. After some tweaking based on the output of the edge output, I decided on a high threshold of 150 and a low threshold of 50. 

![alt text][image2]


Step 3) 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
