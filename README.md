# Introduction
The objective of this project is to write a code that helps to identify lane lines on the road. First lane detection will be made from different images of raods and next the code will be applied in a vedeo stream which is a sereis of images to detect lane lines. 
The pipeline or series of steps to acheive the above objective are list below

1. Convert the image into grayscale
2. Perfoming Gaussian blurring (smoothening) on the grayscale image
3. Canny edge detection on the blurred  image
4. Define region of interest and mask out portion of the image
6. Apply Hough transform
7. Draw line on the original image
8. 




# Reflection

The open souce computer vision software (OpenCV) was mostly used to  impliment the above pipeline. The first step in the lane detection pipeline is to convert the color image with dimension of WxH*3 (where W is width and H is hight and 3 the color(RGB) or depth) into grayscale image of dimension W*H*1. This process helps us to identify edges based of difference in brightness of neighboring pixels(i.e by computing the gradient , (df/dx,df/dy) ). 

We donot need to do the gradient calculation by ourselves, the OpenCV library called Canny() can help us to identify edges on the gray image. But before performing the canny edge detection we need to smooth the gray image using the OpenCV library (Gaussian_blur()), the function can take n*n pixel and then average the pixel values which gives us blurred gray image, in the process the places with a strong gradient standsout whihc make the edge detection simple. After canny edge detection is performed masking out the undesired area was done by specifies verties on the image. 

The last steps are most important in detection lanes. The Hough transform takes in the edge detected image above and converts them into many line segement which instread are composed of points. By manupualting the parameter of Hough transform we can identify line /lanes of our interest. However the Hough transform alone couldn't help us to detect the left line and right line of a lane. To do that we need a help function which takes all the lines detected by the Hough transform and identify the righ and left line of a lane by based on thier slope and finally extrapolate the line. This step in the pipeline is the most time consume and import step in the lane detection process.


