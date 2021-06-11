# **Finding Lane Lines on the Road** 

## Writeup Finding Lanes by Max Polster

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/solidWhiteCurve_gray.jpg "Grayscale"
[image2]: ./test_images_output/solidWhiteCurve_gaus.jpg "Canny"
[image3]: ./test_images_output/solidWhiteCurve_gaus_corpped.jpg "Cropped"


---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consists of the following steps. First, I converted the images to grayscale,
![alt text][image1]
then I defined a vertices to adjust my region of interest using the image.shape as an input to make sure it can be used with all the images. After that I applied the canny algorithm and the gaussian_blur using default values.
![alt text][image2]
To make it easier to determine the values for canny and the gaussian blur I cropped the image to reduce the area of interest. Using a for loop i than iterated over mutliples of the default values an observed the outputs to avaluate the pest values. Resulting in the following image:
![alt text][image3]

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 



### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
