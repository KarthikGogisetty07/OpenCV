# ADR-TaskPhase-openCV

"The Goal of the code in this repository is to get familiar with the basics of OpenCV in python."

##### SOURCE
https://docs.opencv.org/master/d6/d00/tutorial_py_root.html

##### VIEDOS
https://www.youtube.com/watch?v=Z78zbnLlPUA&list=PLQVvvaa0QuDdttJXlLtAJxJetJcqmqlQq&index=1&ab_channel=sentdex
https://www.youtube.com/watch?v=U6uIrq2eh_o&list=PLQVvvaa0QuDdttJXlLtAJxJetJcqmqlQq&index=3&ab_channel=sentdex
https://www.youtube.com/watch?v=U6uIrq2eh_o&list=PLQVvvaa0QuDdttJXlLtAJxJetJcqmqlQq&index=3&ab_channel=sentdex
https://www.youtube.com/watch?v=1pzk_DIL_wo&list=PLQVvvaa0QuDdttJXlLtAJxJetJcqmqlQq&index=4&ab_channel=sentdex
https://www.youtube.com/watch?v=_gfNpJmWIug&list=PLQVvvaa0QuDdttJXlLtAJxJetJcqmqlQq&index=5&ab_channel=sentdex
https://www.youtube.com/watch?v=jXzkxsT9gxM&list=PLQVvvaa0QuDdttJXlLtAJxJetJcqmqlQq&index=6&ab_channel=sentdex

## INTRODUCTION

At first we used commands to convert a color image into a grayscale, Now one has to remember that all the analysis in many OpenCV problem statements are done by converting the given image into grayscale and then converted back to color as in grayscale we only deal with two colors in general, hence quite easy and approachable. The first code emphasis on the process to convert into grayscale from a BGR form. 
#### IMAGE_GRAYSCALE
![BW_basics](https://user-images.githubusercontent.com/69350191/91645382-44315600-ea62-11ea-9f58-58c8a3f3ade1.PNG)

Second Part of the notebook emphasis on the different shapes we can draw on the image that we loaded. The different results that are obtained in the code are:
#### IMAGES
![LINE](https://user-images.githubusercontent.com/69350191/91645402-69be5f80-ea62-11ea-8cfb-1d6fcd9d41a3.PNG)

![rectangle](https://user-images.githubusercontent.com/69350191/91645416-8064b680-ea62-11ea-8503-b9865e8c6419.PNG)

![circle](https://user-images.githubusercontent.com/69350191/91645423-8f4b6900-ea62-11ea-99f9-588e71630bc5.PNG)

![poly](https://user-images.githubusercontent.com/69350191/91645434-9ffbdf00-ea62-11ea-88b1-a9c6dee215c1.PNG)

### IMAGE-BLENDING
This is a technique used in cv to merge two pic of same sizes. The function cv.add(), adds all the pixel values of at every particular location of two images that are inputed and displays a much brighter image than the orignal pictures it is because the addition of pixels almost at every location is near or equal to 255 which depicts that it is bright/White.
#### IMAGE

![Addtest](https://user-images.githubusercontent.com/69350191/91645442-b5710900-ea62-11ea-9bd2-44ca8d219b22.PNG)

Where as in weighted addition technique each of the pic is given some weight (percentage) of its opaqueness. Hence, the pics overlay on each other according to the percentages assigned.
#### IMAGE

![Blendtest](https://user-images.githubusercontent.com/69350191/91645451-c6ba1580-ea62-11ea-8724-9c8bbc1b4467.PNG)


Next, we have used bitwise operations just similar to logic gates that we study in Electronics. The motto was to imprint a loggo on a graphical image. Hence, first we consider the ROI (Region of Intrest) and then after collecting its coorinates we perform certain operations accordingly. In my case, the img2 consist of a logo of python and img1 consists of a graph. I have feed the rows and colomns of img2 to ROI in img1. Later converted the logo into grayscale for further analysis. The threshold functions helps in obtaining either a 1 (255) or 0 (000) in GrayScale with respect to the threshold value given. The 220 in the code acts as a threshold value and if the location has values greater than or equal to threshold then it's 1. Now the logo coordinates are obtained by asserting them accordingly. And that region is imprinted on the img1 after changing the foreground (fg) of img1 and background (bg) of img2 as show in the code. 
#### IMAGE

![operations](https://user-images.githubusercontent.com/69350191/91645522-48aa3e80-ea63-11ea-97a0-d9101a72f21c.PNG)

### THRESHOLDING
For every pixel, a specific threshold value is set and checked. If the pixel value is smaller than the threshold, it is set to 0, otherwise it is set to a maximum value. The function cv.threshold is used to apply the thresholding. The first argument is the source image. The second argument is the threshold value which is used to classify the pixel values. The third argument is the maximum value which is assigned to pixel values exceeding the threshold. There are many types of thresholding techniques of which i will be discusing few for more information you can vist the source.
If we apply thresholding to a color picture you obtain different colours at different points according to the threshold set hence, it's prefered to convert into grayscale. In some situation where the picture is taken in dark locations and the has curved structure resulting in the light source to reach differently at every point, it is preffered to use an optimised technique called Adaptive Thresholding. Here, the algorithm determines the threshold for a pixel based on a small region around it. So we get different thresholds for different regions of the same image which gives better results for images with varying illumination. 

#### ORIGINAL-IMAGE

![BOOKPAGE](https://user-images.githubusercontent.com/69350191/91645464-efdaa600-ea62-11ea-86b0-c0bd7c878553.PNG)

#### THRESHOLD-COLOR

![thresholdColor](https://user-images.githubusercontent.com/69350191/91645539-6d9eb180-ea63-11ea-9300-3adf597fd82c.PNG)

#### THRESHOLD-GRAYSCALE

![threshold_B W](https://user-images.githubusercontent.com/69350191/91645545-860ecc00-ea63-11ea-989b-d02ff4f3cc1b.PNG)

#### THRESHOLD-ADAPTIVE

![adaptiveThreshold](https://user-images.githubusercontent.com/69350191/91645554-9d4db980-ea63-11ea-9dc4-d77e3a805671.PNG)
