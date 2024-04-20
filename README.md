# SuperResolution_AMFFN_TGRS2023
"Lightweight Remote-Sensing Image Super-Resolution via Attention-Based Multilevel Feature Fusion Network," in IEEE Transactions on Geoscience and Remote Sensing, vol. 61, pp. 1-15, 2023

## Requirements
- Python 3.8
- Pytorch=1.12.0
- torchvision=0.13.0
- matplotlib
- opencv-python
- scipy
- tqdm
- scikit-image
- thop

## Installation
Clone or download this code and install aforementioned requirements 
```
cd codes
```

## Dataset
We used the UCMerced and RSSCN7 dataset for both training and testing.
Download the UCMerced dataset [[Google Drive](https://drive.google.com/file/d/1ckE3ZrmzhU7EOnHXXogRAG2Ho7rU4kCd/view?usp=drive_link)], 
and RSCNN7 dataset [[Google Drive](https://drive.google.com/file/d/1vNy-EF-g_x9mY2yq1_DTQdqWRW7aqNsF/view?usp=drive_link)].

These datasets are for training and testing which have been split them into train/val/test data. In every dataset, the original images would be taken as the HR references and the corresponding LR images are generated by bicubic down-sample. 

## Download the results
We share the trained AMFFN model [[Google Drive](https://drive.google.com/file/d/10ajvtXeLAUPb_NmghfRTFLpk0kDXI1Go/view?usp=drive_link)].
We also share the super-resolved results generated by our AMFFN. Then, researchers can compare their algorithms to our AMFFN without performing inference.
Results are available at [[Google Drive](https://drive.google.com/file/d/1s90xW2JgORLvx3rmqqs_zNUcDBOKKxbH/view?usp=drive_link)].

## Train
The train/val data pathes are set in [data/__init__.py](codes/data/__init__.py) 
```
# x8
python demo_train.py --model=AMFFN --dataset=UCMerced --scale=8 --image_size=256 --patch_size=192 --ext=img --save=AMFFNx8_UCMerced
# x4
python demo_train.py --model=AMFFN --dataset=UCMerced --scale=4 --image_size=256 --patch_size=192 --ext=img --save=AMFFNx4_UCMerced
# x3
python demo_train.py --model=AMFFN --dataset=UCMerced --scale=3 --image_size=255 --patch_size=144 --ext=img --save=AMFFNx3_UCMerced
# x2
python demo_train.py --model=AMFFN --dataset=UCMerced --scale=2 --image_size=256 --patch_size=96 --ext=img --save=AMFFNx2_UCMerced
```

## Test 
The test data path and the save path can be edited in [demo_deploy.py](codes/demo_deploy.py)

```
# x8
python demo_deploy.py --model=AMFFN --scale=8
# x4
python demo_deploy.py --model=AMFFN --scale=4
# x3
python demo_deploy.py --model=AMFFN --scale=3
# x2
python demo_deploy.py --model=AMFFN --scale=2
```

## Evaluation 
Compute the evaluated results in term of PSNR and SSIM, where the SR/HR paths can be edited in [calculate_PSNR_SSIM.py](codes/metric_scripts/calculate_PSNR_SSIM.py)

```
cd metric_scripts 
python calculate_PSNR_SSIM.py
```

## Citation 
If you find this work helpful, please consider citing the following paper:
``````
@ARTICLE{10328614,
  author={Wang, Hongyuan and Cheng, Shuli and Li, Yongming and Du, Anyu},
  journal={IEEE Transactions on Geoscience and Remote Sensing}, 
  title={Lightweight Remote-Sensing Image Super-Resolution via Attention-Based Multilevel Feature Fusion Network}, 
  year={2023},
  volume={61},
  number={1},
  pages={1-15}
}


## Acknowledgements 
This code is built on [HSENet (Pytorch)](https://github.com/Shaosifan/HSENet), [CTNet (Pytorch)](https://github.com/BITszwang/CTNet) and [HAUNet (Pytorch)](https://github.com/likakakaka/HAUNet_RSISR).  We thank the authors for sharing the codes.

## Citation  
[1] H. Wang, S. Cheng*, Y. Li and A. Du, "Lightweight Remote-Sensing Image Super-Resolution via Attention-Based Multilevel Feature Fusion Network," in IEEE Transactions on Geoscience and Remote Sensing, vol. 61, pp. 1-15, 2023 (https://github.com/cslxju/SuperResolution_AMFFN_TGRS2023)




















