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
[image4]: ./test_images_output/solidWhiteCurve_hough.jpg "Hough"
[image5]: ./test_images_output/solidWhiteRight_fin.jpg "Final"


---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consists of the following steps. First, I converted the images to grayscale,
![alt text][image1]
then I defined a vertices to adjust my region of interest using the image.shape as an input to make sure it can be used with all the images. After that I applied the canny algorithm and the gaussian_blur using default values.
![alt text][image2]
To make it easier to determine the values for canny and the gaussian blur I cropped the image to reduce the area of interest. Using a for loop i than iterated over mutliples of the default values an observed the outputs to avaluate the pest values. Resulting in the following image:
![alt text][image3]
With the right values adjuste on canny and gauss algroithm I than use the hough function first with default values. To adjust the values  I followed a similar approach as befor and used a for loop. One by one I ajusted the faules evaluataing them after each iteration till I was convinced that the outcome is good enough like in the picture below.
![alt text][image4]

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by first sorting the lines to right and left sight using their gradient 
```markdown
delta = (y2-y1)/(x2-x1)
```
depending on their side the lines were appended to a list. Using a new function than each list of lines is used to calculate on single line. This seperate  funnctioncalculate_avg_line() calculates first the averagr of x1, y1 , x2 and y2 using all the lines as an input. To erase some noise only the lines left or right from the middle of the image are used. With the average x and y values I calculated their gradient and the centre between the points. The final line is than calculated by substracting the end points of the region of interset with the centre and deviding the difference with the gradient. With the ratio the final point of the line are caclulated using this formula:
```markdown
 point1 = (int(centre_x + (delta_x * factor_bottom)), int(centre_y + (delta_y * factor_bottom)))
 point2 = (int(centre_x+(delta_x * factor_top)), int(centre_y +(delta_y * factor_top)))
```
I tested than the algorithm on the sample picutres and was pleased with the performance:
![alt text][image5]

To finish off the project I copy pasted the algorithm in the process_image() function and let it run over the video. In general the result looks good to me even though the perfomance could be a bit better



### 2. Identify potential shortcomings with your current pipeline

The most obvious shortcoming is that the lines are not that stable they are jumping an flickering.

Another shortcoming could be that curves are not very well visualized.

If the lines are not seperated good enough this could lead to wrong calculations and therefor not detecting the correct lines.


### 3. Suggest possible improvements to your pipeline

To improve the flickering the algorithm needs to be more stable for instance taking the last position of the line also into the computation.

Also it  would be better to not only use the gradient of the lines to sperate them between right and left.

Another improvement would be to not only extracct lines and gather more information from picture.

Another potential improvement could be to ...
