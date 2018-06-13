# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"
[image5]: ./test_images_output/solidWhiteCurve.jpg "LaneLines"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I applied a 5x5 size Gaussian smoothing. Thirdly, I used Canny edge detection to detect the edge of lines. To filter the lane lines from the image, I defined a regon of interest and runned Hough transformation to detect line segements at rigion. Finnally, I drawn the line segements with red color.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function. I seperated line segements by their slope,  that the slope of left line segements were less than zero while right line segements greater than zero. Then I filtered out the segements whose slope were out of the range for the lane lines and averaged the slope of left line and right line. From the rest line segements, I picked coordinates at 4/5 of the image height and calculated the width of left line and right line respetively. At last, I extrapolated the line from bottom of the image to the top positon of the lane.

![alt text][image5]

### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be the detection robustness, current pipeline requires tough condions, such as the clear lane mark and suitable lightness. It would not work well when too bright or too dark or too many shade on the rode, it also would happen when the lane lines are not very clear. And the pipeline would not work very well when rainy or snowy.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to combine some other features, such as previouse frames to filter noises, get the lanes information from the map, and optimaize using some mathematic algrorithm.

Another potential improvement could be to use deep learning, it might detect the lane lines better for many conditions.
