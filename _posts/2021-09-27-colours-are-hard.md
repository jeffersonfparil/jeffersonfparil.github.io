# Colours are hard

[2021-09-27]

We, humans sense light and colours in RGB, i,e, using **R**ed, **G**reen, and **B**lue light sensors of our eyes. But we consciously understand light better in HSV, i.e. **H**ue, **S**aturation, and **V**alue.

![](/img/2021-09-27.svg)

For example, when I tell you that a colour pixel is `[100, 160, 35]` to represent the red, green, and blue 8-bit colour channels, what colour do you picture? Contrast that with `[0.25, 0.64, 0.38]` to represent the hue, saturation, and value of a pixel. We know that for hue, i.e. the colour wheel goes across the 3 primary colours where red is at position 0, green at a third of the way (i.e. ~33% or 120°), and blue at two-thirds of the way (i.e. ~67% or 240°). The colours transitions from red, orange, yellow, yellow-green, green, cyan, blue, violet, magenta, then back to red. Now since we have 25% hue value or  90° along the colour, then we can say that the pixel is yellow-greenish.

Python script to generate the RGB and HSV colour representations:

```{python}
########################
### Import libraries ###
########################
import numpy as np
from skimage import color
import matplotlib; matplotlib.use('TkAgg')
from matplotlib import pyplot as plt

###########
### RGB ###
###########
### range of channel values
n_x_cols = 256
n_y_rows = 256
n_z_planes = 5
### vector of channel values
vec_R = np.uint8(np.arange(0, 256, 1))
vec_G = np.uint8(np.arange(0, 256, 1))
vec_B = np.uint8(np.arange(0, 256, int(256/n_z_planes)))
### initialise colour image
mat_RG = np.uint8(np.zeros((n_x_cols, n_y_rows, 3)))
### set values along the red channel
for x in range(n_x_cols):
  mat_RG[:,x,0] = vec_R[x] ### red
### set values along the green channel
for y in range(n_y_rows):
  mat_RG[y,:,1] = vec_G[y] ### green
### set values along the blue channels and save the image
for z in range(len(vec_B)):
  mat_RG[:,:,2] = vec_B[z] ### blue
  ### plot
  plt.imshow(mat_RG, origin='lower')
  plt.ylabel("Green")
  plt.xlabel("Red")
  # plt.show(block=False)
  plt.savefig("RGB-"+str(vec_B[z])+".svg")

###########
### HSV ###
###########
### range of channel values
n_x_cols = 100
n_y_rows = 100
n_z_planes = 10
### vector of channel values
vec_H = np.arange(0, 100, 1)/100
vec_S = np.arange(0, 100, 1)/100
vec_V = np.arange(0, 100, int(100/n_z_planes))/100
vec_V = np.append(vec_V, 1.0)
### initialise colour image
mat_HS = np.zeros((n_x_cols, n_y_rows, 3))
### set values along the hue channel
for x in range(n_x_cols):
  mat_HS[:,x,0] = vec_H[x] ### hue
### set values along saturation channel
for y in range(n_y_rows):
  mat_HS[y,:,1] = vec_S[y] ### saturation
### set values along the values channel and save the image
for z in range(len(vec_V)):
  mat_HS[:,:,2] = vec_V[z] ### value
  ### plot
  plt.imshow(color.hsv2rgb(mat_HS), origin='lower')
  plt.xlabel("Hue")
  plt.ylabel("Saturation")
  # plt.show(block=False)
  plt.savefig("HSV-"+str(vec_V[z])+".svg")
```