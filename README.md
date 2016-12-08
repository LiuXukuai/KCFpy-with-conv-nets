# KCF tracker in Python

Python implementation of
> [High-Speed Tracking with Kernelized Correlation Filters](http://www.robots.ox.ac.uk/~joao/publications/henriques_tpami2015.pdf)<br>
> J. F. Henriques, R. Caseiro, P. Martins, J. Batista<br>
> TPAMI 2015

It is fix version for python 3 of [KCFpy](https://github.com/uoip/KCFpy).


It is translated from [KCFcpp](https://github.com/joaofaro/KCFcpp) (Authors: Joao Faro, Christian Bailer, Joao F. Henriques), a C++ implementation of Kernelized Correlation Filters. Find more references and code of KCF at http://www.robots.ox.ac.uk/~joao/circulant/

### Requirements
- Python 2.7 or 3
- NumPy
- Numba (needed if you want to use the hog feature)
- OpenCV (ensure that you can `import cv2` in python)



### Use
Download the sources and execute
```shell
git clone https://github.com/Sshanu/KCFpy.git
cd KCFpy
python run_updated.py
```
It will open the default camera of your computer, you can also open a video
```shell
python run_updated.py inv test.avi  
```
Try different options (hog/gray, fixed/flexible window, singlescale/multiscale) of KCF tracker by modifying the arguments in line `tracker = kcftracker.KCFTracker(False, True, False)  # hog, fixed_window, multiscale` in run.py.

### Peoblem
I have struggled to make this python implementation as fast as possible, but it's still 2 ~ 3 times slower than its C++ counterpart, furthermore, the use of Numba introduce some unpleasant delay when initializing tracker (***NEW:*** the problem has been solved in [KCFnb](https://github.com/uoip/KCFnb) by using AOT compilation).

***NEWER:*** I write a python wrapper for KCFcpp, see [KCFcpp-py-wrapper](https://github.com/uoip/KCFcpp-py-wrapper), so we can benefit from C++'s speed in python now.
