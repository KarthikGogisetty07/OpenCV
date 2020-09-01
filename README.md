# ADR-TaskPhase-openCV

# INTRODUCTION

The Goal of the codes in this repository is to get familiar with the basics and wide techniques used in OpenCV. Let us first look into some basic ideologies in an openCV.

### Basics:

At first we used commands to convert a color image into a grayscale, Now one has to remember that all the analysis in many OpenCV problem statements are done by converting the given image into grayscale and then converted back to color as in grayscale we only deal with two colors in general, hence quite easy and approachable. The first code emphasis on the process to convert into grayscale from a BGR form.

#### GRAYSCALE:

 ![BW_basics](https://user-images.githubusercontent.com/69350191/91662700-b7d67000-eb01-11ea-8e74-bee3503e9fd0.PNG)
 
Then I emphasised on the different shapes we can draw on the image that we loaded. While providing the thickness of the shapes drawn, in the last argument we code (-1), to completely fill the shapes. The different results that are obtained in the code are

#### DRAWING DIFFERENT SHAPES ON THE LOADED PIC : (WRITING ON PIC)

#### Line:

![LINE](https://user-images.githubusercontent.com/69350191/91662706-c6248c00-eb01-11ea-9a61-2285000fbfbe.PNG)

#### Rectangle:
![rectangle](https://user-images.githubusercontent.com/69350191/91645416-8064b680-ea62-11ea-8503-b9865e8c6419.PNG)

#### Circle:
![circle](https://user-images.githubusercontent.com/69350191/91645423-8f4b6900-ea62-11ea-99f9-588e71630bc5.PNG)

#### Polygon:
![poly](https://user-images.githubusercontent.com/69350191/91645434-9ffbdf00-ea62-11ea-88b1-a9c6dee215c1.PNG)

### Image-Blending
This is a technique used in cv to merge two pic of same sizes. The function cv.add(), adds all the pixel values of at every particular location of two images that are given as inputs and displays a much brighter image than the orignal pictures it is because the addition of pixels almost at every location is near or equal to 255 which depicts that it is bright or White.
#### Image-add:

![Addtest](https://user-images.githubusercontent.com/69350191/91645442-b5710900-ea62-11ea-9bd2-44ca8d219b22.PNG)

Where as in weighted addition technique each of the pic is given some weight (percentage) of its opaqueness. Hence, the pics overlay on each other according to the percentages assigned.
#### Image-adaptive-add:

![Blendtest](https://user-images.githubusercontent.com/69350191/91645451-c6ba1580-ea62-11ea-8724-9c8bbc1b4467.PNG)


Next, we have used bitwise operations just similar to logic gates that we study in Electronics. The motto was to imprint a loggo on a graphical image. Hence, first we consider the ROI (Region of Intrest) and then after collecting its coorinates we perform certain operations accordingly. In my case, the img2 consist of a logo of python and img1 consists of a graph. I have feed the rows and colomns of img2 to ROI in img1. Later converted the logo into grayscale for further analysis. The threshold functions helps in obtaining either a 1 (255) or 0 (000) in GrayScale with respect to the threshold value given. The 220 in the code acts as a threshold value and if the location has values greater than or equal to threshold then it's 1. Now the logo coordinates are obtained by asserting them accordingly. And that region is imprinted on the img1 after changing the foreground (fg) of img1 and background (bg) of img2 as show in the code. 
#### operations-Result:

![operations](https://user-images.githubusercontent.com/69350191/91645522-48aa3e80-ea63-11ea-97a0-d9101a72f21c.PNG)

### THRESHOLDING
For every pixel, a specific threshold value is set and checked. If the pixel value is smaller than the threshold, it is set to 0, otherwise it is set to a maximum value. The function cv.threshold is used to apply the thresholding. The first argument is the source image. The second argument is the threshold value which is used to classify the pixel values. The third argument is the maximum value which is assigned to pixel values exceeding the threshold. There are many types of thresholding techniques of which i will be discusing few for more information you can vist the source.
If we apply thresholding to a color picture you obtain different colours at different points according to the threshold set hence, it's prefered to convert into grayscale. In some situation where the picture is taken in dark locations and the has curved structure resulting in the light source to reach differently at every point, it is preffered to use an optimised technique called Adaptive Thresholding. Here, the algorithm determines the threshold for a pixel based on a small region around it. So we get different thresholds for different regions of the same image which gives better results for images with varying illumination. 

#### Original-Image:

![BOOKPAGE](https://user-images.githubusercontent.com/69350191/91645464-efdaa600-ea62-11ea-86b0-c0bd7c878553.PNG)

#### Thresholding-Color:

![thresholdColor](https://user-images.githubusercontent.com/69350191/91645539-6d9eb180-ea63-11ea-9300-3adf597fd82c.PNG)

#### Thresholding-Grayscale:

![threshold_B W](https://user-images.githubusercontent.com/69350191/91645545-860ecc00-ea63-11ea-989b-d02ff4f3cc1b.PNG)

#### THRESHOLD-Adaptive:

![adaptiveThreshold](https://user-images.githubusercontent.com/69350191/91645554-9d4db980-ea63-11ea-9dc4-d77e3a805671.PNG)

In the second Notebook we discussed about few techniques performed in openCV for Analysis. Color filtering is a processes of targeting one color of the picture and displaying it in specific (particular color). We convert the picure into HSV as HSV helps to differentiate intensity from color. We have choosen a numpy array to define the color value range for blue/red and then apply mask for tht particular value by converting them to grayscale as the computation is easy. The acquried region that has color is displayed back from the original picture. If you want to understand what 0xFF means in the code read this. The code then waits for the user to hit the ‘Esc’ button which will quit it and destroy all the windows to cleanup.

#### Original Image:

![Original](https://user-images.githubusercontent.com/69350191/91741196-fd626e00-ebd1-11ea-86fe-0b57d8d3cec7.png)

#### Mask:

![MASK-CF](https://user-images.githubusercontent.com/69350191/91741280-21be4a80-ebd2-11ea-9ca3-efba37974ca9.png)

#### Displayed Image:

![ResultCF](https://user-images.githubusercontent.com/69350191/91741335-31d62a00-ebd2-11ea-86b5-d739e1ca072e.png)

We are observing a lot of disturbance in the image due to external factors hence, We try reducing the noise in the image by smoothing the edges. This can be done using many fuctions to filter the image in openCV Now, let us discuss few of them. The very first basic method is 2D-Convolution. The convolution happens between source image and kernel. Kernel is another array, that is usually smaller than the source image, and defines the filtering action. A kernel could be a high pass, low pass, or a custom that can detect certain features in the image. Low pass filters take the average of the pixels in the specific kernel shape that is defined and replaces them with that particular number obtain it is usually used to reduce noise , While a high pass filter is used to detect edges which will be encounterd soon. Apply convolution between source image and kernel using cv2.filter2D() function and we end up with a smooth picture than the original one. 
We can observe the difference in the mask as well as the improvement in the result yet can be concluded not the best as it still has significant amount of noise.

#### Filtered Mask:

![mask2](https://user-images.githubusercontent.com/69350191/91741503-7235a800-ebd2-11ea-82e8-9bd49bc33f8e.png)

#### Result:


![Smooth](https://user-images.githubusercontent.com/69350191/91741641-a3ae7380-ebd2-11ea-8347-7f48a0e3abaa.png)

Now, there is a fuction in open CV called gaussian blur that takes the gaussian value of the region specified the height and width must be specied and must be odd. It helps in removing the noise depending on the intensity of light at different locations which more significant and appropriate method. There are other methods like Bilateral blur and Median blur which are also impactful according to a particular situation. Median blur is highly effective against salt-and-pepper noise in an image. Interestingly, in Gaussian filters, the central element is a newly calculated value which may be a pixel value in the image or a new value. But in median blurring, the central element is always replaced by some pixel value in the image. It reduces the noise effectively. Its kernel size should be a positive odd integer as well. The reason for taking odd kernels is to provide symmetry around the pixel value selected at that location which makes computation much faster and effective. The following picture is a result of applying gaussian filter.

#### Gaussian-Filter:


![Gausian_blur](https://user-images.githubusercontent.com/69350191/91742511-00f6f480-ebd4-11ea-9514-963c6c48a8b1.png)

There are few techniques that are named morphological techniques, that are more complex and high-level image processing methods. These methods are applicable only for grayscale images. let us first have a look at the original pic and its mask for all the analysis to be peformed in Grayscale. 

#### Original Picture:

![sharpnerorg](https://user-images.githubusercontent.com/69350191/91743407-60093900-ebd5-11ea-9fea-1002c7c9ee8a.png)

#### Mask:

The ROI taken is just sharpner hence the mask display only that particular pixel values in Grayscale, excluding my hand.

![maskofsharpner](https://user-images.githubusercontent.com/69350191/91743589-aced0f80-ebd5-11ea-91d6-2bb03c2e70ea.png)

Erossion - It is technque where the boundaries are cutdown and the region is made much thinner. This computation happens because the fuction considers a bright value only when all the values under the kernels are 1[255] and displays it is as white region. The basic idea of it is just like soil erosion, where the boundaries of images get eroded.

![erosionn](https://user-images.githubusercontent.com/69350191/91743668-cb530b00-ebd5-11ea-985f-1f17d37b7619.png)

Dilation - It is just opposite to Errosion where the boundaries are extended even if one value of the pixel under the kernel is 1. 

![dilution](https://user-images.githubusercontent.com/69350191/91743778-f9384f80-ebd5-11ea-978a-d978402d03be.png)

There few more techniques like clossing and opening which dont fit to the current situation. The opening operation is used basically in closing the disturbance in the background while a closing operation is performed to fill in the disturbances of the foreground object. 

#### Opening:

![opening](https://user-images.githubusercontent.com/69350191/91744082-85e30d80-ebd6-11ea-931d-a8145beef601.png)

#### Closing:

![closing](https://user-images.githubusercontent.com/69350191/91744137-9bf0ce00-ebd6-11ea-8d29-2da0fc56f5d9.png)

Next, we will be discusing about the edge detection in specific as said before usually a high-pass filter is used to detect the edges in a picture let us consider few of the fine techniques in OpenCV. The Gradient method is a very basic technique used to detect edges its principle lies finding the sudden change in the values of pixels [intensity]. Since this method depends on sudden changes in intensity and if the image has a lot of random noise, then it would detect that as an edge. This method can be done in three diffrenet ways either by provinding just x gradient that is considering the noise only in x- axis direction or y-axis direction or by laplacian method where both are the axis are considerd and computed.

#### Laplacian:

![laplacian](https://user-images.githubusercontent.com/69350191/91744789-9f388980-ebd7-11ea-9b33-9191e93b1cf6.png)

#### Sobel-x:

![sobel-y](https://user-images.githubusercontent.com/69350191/91745263-4f0df700-ebd8-11ea-95a8-ca6db29e8bd4.png)

#### Sobel-y:

![sobel-x](https://user-images.githubusercontent.com/69350191/91745301-6220c700-ebd8-11ea-9f1c-df9dea889b40.png)

The best function in openCV for edge detection is canny function which takes in the argument of input image and the range of threshold. As we can see in laplacian that all noises which need not be edges are still detected but canny algorithm is more intellegent sorting the true edges by following the principal of laplacian and hysterisis thresholding where a specific region is set above which or below which if detected by laplacian function is not considered as edges there by removing the false edges.
Technically, wo threshold values, minVal and maxVal. Any edges with intensity gradient more than maxVal are sure to be edges and those below minVal are sure to be non-edges, so discarded. Those who lie between these two thresholds are classified edges or non-edges based on their connectivity. If they are connected to "sure-edge" pixels, they are considered to be part of edges. Otherwise, they are also discarded.

![canny](https://user-images.githubusercontent.com/69350191/91746495-4a4a4280-ebda-11ea-9c59-4520c09bae76.png)

### Templet Matching
In this code we specified two picture one with a full background and foreground and the other with just the foreground of intrest to be found on the first image. As the name suggest your goal is to match the templet in your original pic. It can be a simple templete that just appears once in the image or a recurring one. OpenCV comes with a function cv2.matchTemplate() for this purpose. It simply slides the template image over the input image (as in 2D convolution) and compares the template and patch of input image under the template image. 

#### Original Image

![virat](https://user-images.githubusercontent.com/69350191/91856836-b4b7bd00-ec84-11ea-9741-142b2a40dc53.png)

#### Templet Picture

![face](https://user-images.githubusercontent.com/69350191/91856915-ce590480-ec84-11ea-90d4-1748e3f2b168.png)

#### After Templet Matching

![templetmatching](https://user-images.githubusercontent.com/69350191/91856992-ea5ca600-ec84-11ea-92a1-6f8513251e7f.png)

### Feature (Corner Detection)
In the code we tried getting the output of the corners that are presnt in an image, python-cv comes with many inbuilt functions. Let us discuss one of the finest technique ORB it is considered to be the fusion of all the other techniques that are presnt in open-cv, hence can be said the best corner detecting algorithm in open cv we specif the number of corners to be detected in an image along with distance between each of each of the corner. If the surrounding pixels have a varying intensity around one particular point it considers the point to be a corner i.e. It computes the intensity weighted centroid of the patch with located corner at center. The following shows the result i obtained and also choosing the color of a corner is important definetly you dont want your corner color to be white when your background is white which reduces the number of corners you observe, i even tried altering the nukmber of corners to be detected, intrestingly, the algorithm could not detect all the corners of squares and rectangles as i decreased the number of corners to be computed. Hence, by trial and error method i considerd an optimum number for my picture. 
#### Original-picture

![Shapes](https://user-images.githubusercontent.com/69350191/91858417-cac67d00-ec86-11ea-8df7-12f0a1f86b75.png)

#### Result

![corners](https://user-images.githubusercontent.com/69350191/91858474-df0a7a00-ec86-11ea-8ddd-1aeeec1e5d0e.png)

### Templete Matching 
This is an other intresting algorithm that helps detect your object which can be in different orientations direction from your templet picture, previously when we considerd in matching the face temple with orignal picture the oreintation was same for the pictures that are considerd in this method orientation and angles of the features of the object need not be constant and can varry, definetly you cannot expect all the features to match with the requried but yet almost 70% of the features are matched correctly. As usual we set a threshold limit as the computation is done in grayscale there is every possiblity that you can have save pixel values around one particular feature leading to a 10-20% of mismatches. In this code,  I considered a pillow with one orientation as my templete and passed an argument to detect it on my parent picture that has differnt objects along with object of intrest in different orientation. Intrestingly, the computation of matching the features was quites satisfying with threshold of 0.7 if i try decreasing or increasing it it was not so favorable and started to mismatch many features that it detected. 

#### Result:

![FeaturingMatching](https://user-images.githubusercontent.com/69350191/91859372-0150c780-ec88-11ea-9640-145b56d31c3d.png)

### Motion Detection
This was the finnest algorithm so far, firstly let us know about Background subtraction, also known as Foreground Detection. It is a technique in the fields of image processing and computer vision where an image's foreground is extracted for further processing (object-recognition, face-detection, etc.) Python-cv comes with different background subtraction technique algorithms out if which i have done using cv.createBackgroundSubtractorMOG2() algorithm, such well trained algorithms using different concepts for Deeplearning or ML, are extensively used for detecting dynamically moving objects from static cameras.This is a technique for separating out foreground elements from the background and hence, is done by generating a foreground mask which can further be processed using the algorithms we learnt to reduce the noise or detect edges if requried.
I have feed a small viedo clip and got some very intresting out output which almost nulified the background as shown few shoots of the viedo. 

#### Motion Detection:Results-


![Screenshot from 2020-09-01 00-42-40](https://user-images.githubusercontent.com/69350191/91861156-20e8ef80-ec8a-11ea-97ab-5d1ee7ca8488.png)

![Screenshot from 2020-09-01 00-43-44](https://user-images.githubusercontent.com/69350191/91861187-2a725780-ec8a-11ea-9440-f6addaf4212f.png)

![Screenshot from 2020-09-01 00-43-28](https://user-images.githubusercontent.com/69350191/91861231-35c58300-ec8a-11ea-9412-07485ac8d2a0.png)

![Screenshot from 2020-09-01 00-42-55](https://user-images.githubusercontent.com/69350191/91861267-3e1dbe00-ec8a-11ea-928d-c566b1d9e213.png)

### For more information and details about each algorithm please vist the documentation source mentioned.


## SOURCE

https://docs.opencv.org/master/d6/d00/tutorial_py_root.html

### Vidoes:

https://www.youtube.com/playlist?list=PLQVvvaa0QuDdttJXlLtAJxJetJcqmqlQq


