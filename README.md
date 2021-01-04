# Digital_Image_processing_Exp_1-Reading-and-displaying-images-using-different-modules_PIL_Matplotlib.

# AIM: 
WAP to Read, save, display images using the following

PIL
Matplotlib
Scikit Image

# Requirements: setting up all the libraries after installing Python.

# Source code:

Reading, saving, and displaying an image using PIL

im = Image.open("../images/parrot.png") # read the image, provide the correct path

print(im.width, im.height, im.mode, im.format, type(im))

# 453 340 RGB PNG <class 'PIL.PngImagePlugin.PngImageFile'>

im.show() # display the image

453 340 RGBA PNG <class 'PIL.PngImagePlugin.PngImageFile'>



im_g = im.convert('L') # convert the RGB color image to a grayscale image

im_g.save('../images/parrot_gray.png') # save the image to disk

Image.open("../images/parrot_gray.png").show() # read the grayscale image from disk and show



# Reading, saving, and displaying an image using Matplotlib

im = mpimg.imread("../images/hill.png") # read the image from disk as a numpy ndarray

print(im.shape, im.dtype, type(im)) # this image contains an α channel, hence num_channels= 4

# (960, 1280, 4) float32 <class 'numpy.ndarray'>

plt.figure(figsize=(10,10))

plt.imshow(im) # display the image

plt.axis('off')

plt.show()

(960, 1280, 4) float32 <class 'numpy.ndarray'>








im1 = im

im1[im1 < 0.5] = 0 # make the image look darker

plt.imshow(im1)

plt.axis('off')

plt.tight_layout()

plt.savefig("../images/hill_dark.png") # save the dark image

plt.close()

im = mpimg.imread("../images/hill_dark.png") # read the dark image

plt.figure(figsize=(10,10))

plt.imshow(im)

plt.axis('off') # no axis ticks

plt.tight_layout()

plt.show()








# Reading, saving, and displaying an image using scikit-image


im = imread("../images/parrot.png") # read image from disk, provide the correct path

print(im.shape, im.dtype, type(im))

hsv = color.rgb2hsv(im) # from RGB to HSV color space

hsv[:, :, 1] = 0.5 # change the saturation

im1 = color.hsv2rgb(hsv) # from HSV back to RGB

imsave('../images/parrot_hsv.png', im1) # save image to disk

im = imread("../images/parrot_hsv.png")

plt.axis('off'), imshow(im), show()

(340, 453, 3) uint8 <class 'numpy.ndarray'>

C:\Users\Sandipan.Dey\Anaconda\envs\ana41py35\lib\site-packages\skimage\util\dtype.py:130: UserWarning: Possible precision loss when converting from float64 to uint8

 .format(dtypeobj_in, dtypeobj_out))
 
((0.0, 1.0, 0.0, 1.0), <matplotlib.image.AxesImage at 0x24b3a12e940>, None)
