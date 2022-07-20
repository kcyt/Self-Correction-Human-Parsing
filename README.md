# Self Correction for Human Parsing

![Python 3.6](https://img.shields.io/badge/python-3.6-green.svg)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)

An out-of-box human parsing representation extractor.

Our solution ranks 1st for all human parsing tracks (including single, multiple and video) in the third LIP challenge!

![lip-visualization](./demo/lip-visualization.jpg) 

Features:
- [x] Out-of-box human parsing extractor for other downstream applications.
- [x] Pretrained model on three popular single person human parsing datasets.
- [x] Training and inferecne code.
- [x] Simple yet effective extension on multi-person and video human parsing tasks.

## Requirements

```
conda env create -f environment.yaml
conda activate schp
pip install -r requirements.txt
```

## Simple Out-of-Box Extractor
IntegratedPIFu uses this extractor to get the pseudo groundtruth human parsing maps.


**Pascal-Person-Part** ([exp-schp-201908270938-pascal-person-part.pth](https://drive.google.com/file/d/1E5YwNKW2VOEayK9mWCS3Kpsxf-3z04ZE/view?usp=sharing))

* mIoU on Pascal-Person-Part validation: **71.46** %.

* Pascal Person Part is a tiny single person human parsing dataset with 3000+ images. This dataset focus more on body parts segmentation. Pascal Person Part has 7 labels, including 'Background', 'Head', 'Torso', 'Upper Arms', 'Lower Arms', 'Upper Legs', 'Lower Legs'.


## Model Preparation

Make a checkpoints directory: `mkdir checkpoints`

Then, download the trained model (trained on the pascal dataset) from https://drive.google.com/uc?id=1E5YwNKW2VOEayK9mWCS3Kpsxf-3z04ZE 

Put the downloaded file (exp-schp-201908270938-pascal-person-part.pth) into the checkpoints folder.


## Running to generate human parsing maps for IntegratedPIFu
```
python simple_extractor.py --integratedpifu-dir [PATH_TO_IntegratedPIFu Folder]
```






## Citation

Please cite our work if you find this repo useful in your research.

```latex
@article{li2020self,
  title={Self-Correction for Human Parsing}, 
  author={Li, Peike and Xu, Yunqiu and Wei, Yunchao and Yang, Yi},
  journal={IEEE Transactions on Pattern Analysis and Machine Intelligence}, 
  year={2020},
  doi={10.1109/TPAMI.2020.3048039}}
```

## Visualization

* Source Image.
![demo](./demo/demo.jpg)
* LIP Parsing Result.
![demo-lip](./demo/demo_lip.png)
* ATR Parsing Result.
![demo-atr](./demo/demo_atr.png)
* Pascal-Person-Part Parsing Result.
![demo-pascal](./demo/demo_pascal.png)
* Source Image.
![demo](./mhp_extension/demo/demo.jpg)
* Instance Human Mask.
![demo-lip](./mhp_extension/demo/demo_instance_human_mask.png)
* Global Human Parsing Result.
![demo-lip](./mhp_extension/demo/demo_global_human_parsing.png)
* Multiple Human Parsing Result.
![demo-lip](./mhp_extension/demo/demo_multiple_human_parsing.png)


## Related
Our code adopts the [InplaceSyncBN](https://github.com/mapillary/inplace_abn) to save gpu memory cost.

There is also a [PaddlePaddle](https://github.com/PaddlePaddle/PaddleSeg/tree/develop/contrib/ACE2P) Implementation of this project.
