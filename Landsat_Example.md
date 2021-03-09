# Case Study: Landsat

A recent Landsat dataset showing how the river changes:

* https://earthobservatory.nasa.gov/images/147999/river-colors-are-changing

Download two Landsat image files of the Rio Grande from 1986 and 2021.

```
# 1986
wget https://eoimages.gsfc.nasa.gov/images/imagerecords/147000/147999/riogrande_tm5_1986163_lrg.jpg

# 2021
wget https://eoimages.gsfc.nasa.gov/images/imagerecords/147000/147999/riogrande_oli_2020161_lrg.jpg
```

|1986| 2021 |
|:--|:--|
|![](https://eoimages.gsfc.nasa.gov/images/imagerecords/147000/147999/riogrande_tm5_1986163_lrg.jpg)|![](https://eoimages.gsfc.nasa.gov/images/imagerecords/147000/147999/riogrande_oli_2020161_lrg.jpg)|



# Import images and subset to the lake in the top left corner

Import any needed python libraries.



```python
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline
import imageio
import skimage.color
import skimage.transform
import scipy.ndimage as ndimage
```

Load both images


```python
image_1986 = np.asarray(imageio.imread("riogrande_tm5_1986163_lrg.jpg"))
image_2021 = np.asarray(imageio.imread("riogrande_oli_2020161_lrg.jpg"))

%whos
```

    Variable     Type        Data/Info
    ----------------------------------
    image_1986   ndarray     1848x1848x3: 10245312 elems, type `uint8`, 10245312 bytes (9.77069091796875 Mb)
    image_2021   ndarray     1848x1848x3: 10245312 elems, type `uint8`, 10245312 bytes (9.77069091796875 Mb)
    imageio      module      <module 'imageio' from '/<...>ges/imageio/__init__.py'>
    ndimage      module      <module 'scipy.ndimage' f<...>ipy/ndimage/__init__.py'>
    np           module      <module 'numpy' from '/Us<...>kages/numpy/__init__.py'>
    plt          module      <module 'matplotlib.pyplo<...>es/matplotlib/pyplot.py'>
    preproc      function    <function preproc at 0x7fe0e87343b0>
    skimage      module      <module 'skimage' from '/<...>ges/skimage/__init__.py'>


Subset the image to the lake in the top left corner.


```python
plt.figure(figsize=(8,4))

plt.subplot(1,2,1)
plt.imshow(image_1986)
plt.axis('off')
plt.title("1986")

plt.subplot(1,2,2)
plt.imshow(image_2021)
plt.axis('off')
plt.title("2021")

plt.show()
```


    
![png](imgs/output_6_0.png)
    


Focus on the body of water.


```python
plt.figure(figsize=(5,4))

plt.subplot(1,2,1)
plt.imshow(image_1986[1:900,1:500])
plt.axis('off')
plt.title("1986")

plt.subplot(1,2,2)
plt.imshow(image_2021[1:900,1:500])
plt.axis('off')
plt.title("2021")

plt.show()
```


    
![png](imgs/output_8_0.png)
    



```python
def preproc(image):
    result = image[1:900, 1:500]
#    result[:,:,1]=0
    return(result[:,:,1:2])

plt.figure(figsize=(5,4))

plt.subplot(1,2,1)
plt.imshow(preproc(image_1986))
plt.axis('off')
plt.title("1986")

plt.subplot(1,2,2)
plt.imshow(preproc(image_2021))
plt.axis('off')
plt.title("2021")

plt.show()
```


    
![png](imgs/output_9_0.png)
    


Identify body of water, sum up area.


```python

```
