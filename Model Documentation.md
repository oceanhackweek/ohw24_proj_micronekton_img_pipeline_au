# Micronekton detection documentation 

## Steps for deployment of FathomNet model 

Link to Model: (FathomNet/MBARI-midwater-supercategory-detector) 

1. Create and activate Conda environment 
- in terminal
  
```$ module use /g/data/hh5/public/modules
$ module load conda/analysis3
$ python3 -m venv NAME_OF_ENVIRONMENT --system-site-packages 
$ source NAME_OF_ENVIRONMENT/bin/activate
```

- install any missing libraries

```(NAME_OF_ENVIRONMENT) $ pip install ultralytics
```

2. Clone yolov5 into the Conda environment 
- in terminal
```
$ git clone https://github.com/ultralytics/yolov5
$ cd yolov5/
$ pip install -r requirements.txt
```

3. Check that yolov5 has been cloned and all packages are working in your Conda environment 
```
$ cd (NAME_OF_ENVIRONMENT)
$ python
>>> import torch
>>> model = torch.hub.load("ultralytics/yolov5", "yolov5s")  
```

3. Prepare to run the model

- download weights file (https://huggingface.co/FathomNet/MBARI-midwater-supercategory-detector/blob/main/best.pt)
- upload imagery to run against model and copy this path (to your imagery) 

4. Run the model 
- in terminal
```$ cd NAME_OF_ENVIRONMENT
$ source bin/activate
$ cd ../yolov5/
$ python detect.py --weights /path/to/best.pt --source /path/to/images-or-video --save-txt --save-csv --save-crop
```

5. Output
Outputs saved into ..yolov5/runs/detect/exp(n) where n is the run number
* original images with bounding box predictions
* .txt bounding box information for each image
* .csv predictions per image
* crops of predicted classes for each image



  








 

### list 

normal text 
- list
- subsequent item


