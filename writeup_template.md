# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_writeup/grey_image.png "Grayscale"
[image2]: ./test_images_writeup/gaussian_smoothing.png "Gaussian Smoothing"
[image3]: ./test_images_writeup/edges.png "Canny"
[image4]: ./test_images_writeup/masked_edges.png "Region of Interest"
[image5]: ./test_images_writeup/hough_transfer.png "Hough Lines"
[image6]: ./test_images_writeup/final_result.png "Final Result"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps

    1. First I converted the image to Grayscale

![alt text][image1]

    2. Then I applied the Gaussian Smoothing with Kernel size of 5
![alt text][image2]

    3. Then I defined the Parameters (low threshold and high threshold) and applied Canny
![alt text][image3]

    4. Then I defined a four sided polygon to mask and then applied region of interest to get only required region of edges
![alt text][image4]

    5. Then I applied Hough Transform with transfer parameters. I also modified the draw_lines method to get right and left lane line. 

For each set of left and right lines, I identified the slope of the line and categorised negative and postive slope. Then I created a function fit_line() to calculate the lane. 

I applied the polyfit function to define the average slope and intercept of the line.

![alt text][image5]

    6. Then its time for final result. With the help of weighted_image method, we applied the result on the image.
![alt text][image6]



### 2. Identify potential shortcomings with your current pipeline


The potential shortcomings are the area of interest being hardcoded will not work for all lanes type. 

I tested with the optional video where the lane lines doesn't shows up properly.


### 3. Suggest possible improvements to your pipeline

One of the major improvements would be to calculate the region of interest so that each lanes are covered. Other could be the parameters of Hough Transform to get more accurate results.

