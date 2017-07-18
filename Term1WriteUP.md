# **Term 1 - Self Driving Car Engineer Program - UDACITY- Finding Lane Lines on the Road** 

## REPORT 

### This File contains the all the steps and routines used to reach the goals of this first Term.

---

**Finding Lane Lines on the Road**

The mains goals  are the following:

* Make a pipeline that finds lane lines on the road in image and movies.
* Reflect about the challenges and issues that´s envolves in a real situation of computer vision and image treatment. 


[//]: # (Image References)

[image1]: ./examples/solidWhiteCurve.jpg_traced.jpg
[image2]: ./examples/960by540.jpg
[image3]: ./examples/1280by720.jpg

---

### Reflection

### 1. The Pipeline and how was coded Draw_Lines() function

The pipeline consist in two separated functions ( trace_lanes() and trace_lanes_video() ). Both functions are based in Helper functions, but with different input arguments due fl_image pass as argument an colour image. 
The main pipeline for both functions consist in these basic steps.

1.Grayscale the image.

2.Pass through a Gaussian filter.

3.Apply the Canny Function.

4.Create a Mask and a Polygon of  Interest.

5.Appy the Hough Function.

6.Create a weighted image between the main image and the Hough lines.

Since the beginning I was searching for a draw_lines() function to plot solid lines, even in the test images.
For the new draws_lines() function , the basic steps are.

1.Classification of the incoming data in righ ou left lane, considering the line slope (y2-y1)/(x2-x1) , and the x value ( > or < of a calculated threshold in function of image size)

2.To be more accurate and to mitigate noise, is used the PolyFit function to find the coefficients of the line given two image coordinates. 

3.Plotting the lines using the Y´s as the bottom limit of the image and how long we want the lines, and the X´s calculated as function of Y and the PolyFit returned coefficients. 

                                           Image plotted with solid lines

![alt text][image1]


### 2. The Resolution Issue.

The main shortcoming is the fact of the pipeline as is coded just will work for 960X540 movies. Due this “limitation” , the file “challenge.mp4” doesn´t work (1280X720). To make the code more robust is recommended to create the Masks , Polygon of Interest and and Y´s levels for line plotting in function of movie resolution. In practice, this situation could occur when we change the camera of a self driving car. 

                                           Footage taken from a 960X540 movie
![alt text][image2]

                                           Footage taken from a 1024X720 movie
![alt text][image3]




### 3. Improvements to the code

To not take the risk of lose my term submission deadline the improvements described above for the Optional Challenge are already in progress and as soon as possible the code, as well this assignment will be updated , with images and comments about the changes. 
