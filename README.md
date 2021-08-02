## Guide to train

### Github repo for yolov5
[yolov5](https://github.com/ultralytics/yolov5)

### Installation 
Make sure you have python and pip install

```bash
$ git clone https://github.com/ultralytics/yolov5
$ cd yolov5
$ pip install -r requirements.txt
```
## You should read these
[Train Custom Data with yolov5](https://github.com/ultralytics/yolov5/wiki/Train-Custom-Data)
[Tips for Best Results](https://github.com/ultralytics/yolov5/wiki/Tips-for-Best-Training-Results)

### Quick guide to train

Clone this repo and yolov5 repo
```bash
$ git clone https://github.com/kychongdev/datasets
```
Copy the datasets.yaml inside datasets/yolov5 into yolov5 repo

Your file structure should look like this
```
├── datasets 
│   ├──1080x960
│   ├──Original
│   └──yolov5
│       ├──images
│       ├──labels
│       └──datasets.yaml (Copy this to yolov5)
└── yolov5
    ├── datasets.yaml (Copy from above)
    └── all other files
```
Cd into yolov5 repo and run this command to train <br/>
```bash
$ cd yolov5
$ python train.py --img 640 --batch 16 --epochs 300 --data datasets.yaml --weights yolov5s.pt
```

By far, this is the best to train for my spec. You can adjust if your pc can sustain.

- Increase the img size is going to make training time increase A LOT.
- You can adjust batch higher in multiple of 2 [16,32,64,128].
- Higher epochs might give you better results but do not guarantee.
- You can choose the pre-trained weights, check out their documentation for other weights. 
- Check out the best tips if you want to adjust more.



## My learning experience:
- You do not have to adjust the image. The library itself will do it for you. You can specify the size and it will transform for you. In this case, its 640. 
- If you want to crop the picture for more data and train, I suggest you don't do it. I tried with cropped 4k into 4x 1080p picture. The results is way worse and train much longer.
- If you can train higher batch size, do it. 
- Start with epochs 300. I tested with several: 3 and 20 is usable. 100 is not accurate. 300 is significantly better.
- Remember check your pc usage. I think if you do not have CUDA, it won't utilize GPU. (It should run on GPU)

## Current Progress
Check out the OneDrive for the results we had trained. 
Right now we only have 28 images to train which is not ideal.  

- Should add more image, including empty label in image to reduce False Positives(2/28) <- Right now
- Could try to convert pt format into ONNX format to run OpenVino on it. Right now this does not utilize OpenVino at all

