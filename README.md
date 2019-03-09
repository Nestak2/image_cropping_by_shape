# image_cropping_by_shape
A script for image cropping by detection of a particular shape

The script is intended to do precise cropping of objects in images, correcting for misalignment and rotation of the objects, as well as doing a perspective transformation of the images. It might be of help for people preprocessing images for training of neural networks. 

## Methodology:
The script works by detecting 4 squares, that are indicating the location of an object of interest and allow the provided image to be cropped around the object of interest. For this to work, the user has to use a rectangular tray having a square in each of its corners and the user has to place his object of interest inside this tray. A tray template is also provided here, it can be printed out and used.

The squares are intended to be obvious indicators sticking out from inhomogeneous and diverse backgrounds. This might not be necessary for most users, who might be taking pictures with their desks as background, for example. For these users, it is suggested to use the codes provided in our references

## Usage:
Place your objects of interest on the tray. Take pictures of your object of interest, make sure that the squares are visible in the images and there is no peculiar lighting on the squares. Store your images in a folder.

The script requires you to provide input in the preamble of the code - you will need to specify a file path to your input images, to an output-folder for the intermediate output and s.o.

You will also need to specify the location of your object of interest in respect to the coordinate system of the four squares. E.g., if your object of interest is located inside the squares and stretches out from 10% of the width until 90% of the width between the squares and also from 20% of the height until 80% of the height (according to the code
`image_AOI = im_squares[int(0.2*height_im):int(0.8*height_im), int(0.1*width_im):int(0.9*width_im)]` )
then you should specify this in the preamble as 

```python
x0, x1 = 0.2, 0.8
y0, y1 = 0.1, 0.9
```

There are more parameters that the user can adjust in the preamble, but the default ones should work in most cases of images taken with smartphones. 

## Necessary packages:
numpy: version 1.15.2

argparse: version 1.1

cv2: version 4.0.0

imutils: version 0.5.2

shutil: version ?


## Authours:
Created at the i-sense research group in London. Big parts of the code were taken from templates by Adrian Rosenbrock and from the free software OpenNoteScanner (see references below). 

## References:
Big parts were taken from this two articles https://www.pyimagesearch.com/2014/08/25/4-point-opencv-getperspective-transform-example/,
https://www.pyimagesearch.com/2014/09/01/build-kick-ass-mobile-document-scanner-just-5-minutes/

This is a code of a free smartphone application in java that has the same functionality as the script here, but without using the squares (so, for less "noisy" backgrounds of the images) https://github.com/ctodobom/OpenNoteScanner
