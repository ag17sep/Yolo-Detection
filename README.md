# A PyTorch implementation of a YOLO v3 Object Detector

This is my implementation of the YOLOv3 Paper 

This repository contains code for a object detector based on [YOLOv3: An Incremental Improvement](https://pjreddie.com/media/files/papers/YOLOv3.pdf), implemented in PyTorch. The code is based on the official code of [YOLO v3](https://github.com/pjreddie/darknet), as well as a PyTorch 
port of the original code, by [marvis](https://github.com/marvis/pytorch-yolo2). I've also tried to keep the code minimal, and 
document it as well as I can. 

## Requirements
1. Python 3.5
2. OpenCV
3. PyTorch 1.1.0

## Running the detector

### On single or multiple images

Clone, and `cd` into the repo directory. The first thing you need to do is to get the weights file
This time around, for v3, authors has supplied a weightsfile only for COCO [here](https://pjreddie.com/media/files/yolov3.weights), and place 

the weights file into your repo directory. Or, you could just type (if you're on Linux)

```
wget https://pjreddie.com/media/files/yolov3.weights 
python detect.py --images imgs --det det 
```


`--images` flag defines the directory to load images from, or a single image file (it will figure it out), and `--det` is the directory
to save images to. Other setting such as batch size (using `--bs` flag) , object threshold confidence can be tweaked with flags that can be looked up with. 

```
python detect.py -h
```

### Speed Accuracy Tradeoff
You can change the resolutions of the input image by the `--reso` flag. The default value is 416. Whatever value you chose, rememeber **it should be a multiple of 32 and greater than 32**. Weird things will happen if you don't. You've been warned. 

```
python detect.py --images imgs --det det --reso 320
```

### On Video
For this, you should run the file, video_demo.py with --video flag specifying the video file. The video file should be in .avi format
since openCV only accepts OpenCV as the input format. 

```
python video.py --video video.avi
```

### Detection across different scales
YOLO v3 makes detections across different scales, each of which deputise in detecting objects of different sizes depending upon whether they capture coarse features, fine grained features or something between. You can experiment with these scales by the `--scales` flag. 

```
python detect.py --scales 1,3
```


