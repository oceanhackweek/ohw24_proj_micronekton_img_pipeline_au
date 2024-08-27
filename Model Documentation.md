# Micronekton detection documentation 

## Steps for deployment of FathomNet model 
[Here](FathomNet/MBARI-midwater-supercategory-detector) 

### Create conda environment 
- in terminal
```
$ module use /g/data/hh5/public/modules
$ module load conda/analysis3
$ python3 -m venv NAME_OF_ENVIRONMENT --system-site-packages 
$ source NAME_OF_ENVIRONMENT/bin/activate
Then you can install any missing libraries
(NAME_OF_ENVIRONMENT) $ pip install ultralytics
```

## Clone yolov5 into the conda environment 
- in terminal
$ python
>>> git clone https://github.com/ultralytics/yolov5
cd yolov5
pip install -r requirements.txt

- to check that yolov5 has been cloned and is working
import torch
model = torch.hub.load("ultralytics/yolov5", "yolov5s")  # or yolov5n - yolov5x6, custom

## Preparation to run model
- download weights file [Here](https://huggingface.co/FathomNet/MBARI-midwater-supercategory-detector/blob/main/best.pt)
- upload imagery to run against model

## Run model 
- in terminal
$ cd NAME_OF_ENVIRONMENT
$ source bin/activate
$ cd ..yolov5
$ python detect.py --weights /path/to/best.pt --source /path/to/images-or-video

## Output










 

### list 

normal text 
- list
- subsequent item


