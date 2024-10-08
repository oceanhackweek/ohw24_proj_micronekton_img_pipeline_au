# Micronekton Detection Documentation 

## Steps for deployment of FathomNet model 

[FathomNet/MBARI-midwater-supercategory-detector](https://huggingface.co/FathomNet/MBARI-midwater-supercategory-detector)

### Create and activate Conda environment

#### You only need to create your Conda environment once - proceed to the "Run Model" step if you have already done this 

> in a terminal window
> navigate into the folder you want to create a virtual environment in
  
```
$ module use /g/data/hh5/public/modules
$ module load conda/analysis3
$ python3 -m venv NAME_OF_ENVIRONMENT --system-site-packages 
$ source NAME_OF_ENVIRONMENT/bin/activate
```

> install any missing libraries

```
$ (NAME_OF_ENVIRONMENT) $ pip install ultralytics
```

### Clone `yolov5` into the Conda environment

> in a terminal window

```
$ git clone https://github.com/ultralytics/yolov5
$ cd yolov5/
$ pip install -r requirements.txt
```

#### Check that `yolov5` has been cloned and all packages are working in  Conda environment

```
$ cd (NAME_OF_ENVIRONMENT)
$ python
>>> import torch
>>> model = torch.hub.load("ultralytics/yolov5", "yolov5s")  
```
> return to the terminal window

```
$ exit()
```

### Prepare to run the model

> download [weights file](https://huggingface.co/FathomNet/MBARI-midwater-supercategory-detector/blob/main/best.pt)
>
> upload the imagery you want to run the model over and use the path when running the model script below 

### Run the model 

> in a terminal window

```
$ cd NAME_OF_ENVIRONMENT
$ source bin/activate
$ cd ../yolov5/
$ python detect.py --weights /path/to/best.pt --source /path/to/images-or-video --save-txt --save-csv --save-crop
```

### Outputs

> #### Outputs saved into ..yolov5/runs/detect/exp(n) where n is the run number
>
> ##### To move the outputs to a different location

```
$ cd runs/detect/
$ rsync -ravzP ./exp /path/to/DESTINATION
```


> 1.  Original image with bounding box predictions

![Full size image with prediction](Images/OBL00162.JPG "image with bounding box prediction")

> 2. Cropped bounding box of predicted classes for each image

![cropped bounding box](Images/crop_OBL00162.jpg "bounding box image for prediction above") 

> 3. .txt file with all the bounding box information for each image

[link to text file for this image](/Images/OBL00162.txt)

> 4. csv file with predictions and confidence levels for each image in the processed batch

[link to csv file for processed images in this batch](/Images/predictions.csv)






