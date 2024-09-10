Pixel-Learnable 3DLUT with Saturation-Aware Compensation for Image Enhancement

## Data Preparation

PPR10K Dateset：

Download raw portrait photos and retouching target from [baiduyun](https://pan.baidu.com/s/1FMNZ6QTII6dkwj4YY_faYA) (code:pprd).

MIT-Adobe FiveK Dataset：

Download raw portrait photos and retouching target from [baiduyun](https://pan.baidu.com/s/12FwCfEWKrJ7FMkPdqW47Mg) (code:fv5k).

HDR+ Dateset：

Download raw portrait photos and retouching target from [baiduyun](https://pan.baidu.com/s/1fV2uwrZLy9KE1BNnkl0XzQ) (code:hdrp).
~~~~
Please ensure the data structure is as below

├── ppr
   ├── train
       ├── source_aug
           ├── 0_0.tif
           ├── 0_0_1.tif
           └── ...
       ├── target
           ├── 0_0.tif
           ├── 0_1.tif
           └── ...
   └── val
       ├── source
           ├── 1356_0.tif
           ├── 1356_1.tif
           └── ...
       ├── target
           ├── 1356_0.tif
           ├── 1356_1.tif
           └── ...
           
├── FiveK
   ├── train_input
           ├── 1_0.tif
           └── ...
   ├── train_target
           ├── 1_0.tif
           └── ...
   ├── test_input
           ├── 4501_0.tif
           └── ...
   ├── test_target
           ├── 4501_0.tif
           └── ...
           
└── hdr
   ├── train_input
           ├── 193_0.tif
           └── ...
   ├── train_target
           ├── 193_0.tif
           └── ...
   ├── test_input
           ├── 196_0.tif
           └── ...
   ├── test_target
           ├── 196_0.tif
           └── ...
~~~~
##Environment Preparation
Requirements
```
pip install -r requirements.txt
conda install pytorch=1.8 torchvision cudatoolkit=10.2 -c pytorch
pip install matplotlib scikit-learn scikit-image opencv-python yacs joblib natsort h5py tqdm
pip install einops gdown addict future lmdb numpy pyyaml requests scipy tb-nightly yapf lpips
```


Build. Modify the CUDA path in trilinear_cpp/setup.sh adaptively and
```
cd trilinear
sh trilinear/setup.sh
```

## Training

To train our method on the dataset, please run this command:
```train
python train.py --data_path [path_to_dataset] --gpu_id [gpu_id] --output_dir [path_to_save_models]
```


## Evaluation

To evaluate our model on the dataset, run:

Generate the retouched results:
```eval
python validation.py --data_path [path_to_dataset] --gpu_id [gpu_id] --model_dir [path_to_models]
```





