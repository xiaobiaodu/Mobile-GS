<h2 align="center"> <a href="https://xiaobiaodu.github.io/mobile-gs-project/">Mobile-GS: Real-time Gaussian Splatting for Mobile Devices</a></h2>
<h5 align="center"> If you like our project, please give us a star ⭐ on GitHub for latest update.  </h2>

<h5 align="center">

[![project](https://img.shields.io/badge/Webpage-blue)](https://xiaobiaodu.github.io/mobile-gs-project/)
[![arXiv](https://img.shields.io/badge/Arxiv-2603.11531-b31b1b.svg?logo=arXiv)](https://arxiv.org/abs/2603.11531)
<!-- [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://github.com/xiaobiaodu/DreamCar/blob/master/LICENSE)  -->


<img src="assets/method.png"/>


## 😮 Highlights

![teaser](./asset/teaser.png)



## 🚩 **Updates**

Welcome to **watch** 👀 this repository for the latest updates.

✅ **[2026.3.13]** : Release [project page](https://xiaobiaodu.github.io/mobile-gs-project/).

✅ **[2026.3.13]** : Code Release. 






## Setup

For installation:
We recommend to use cuda 12.1 with python 3.11 for easy setup.
```shell
pip install torch==2.5.1 torchvision==0.20.1 torchaudio==2.5.1 --index-url https://download.pytorch.org/whl/cu118
pip install -r requirements.txt
```
#### Install [TMC (GPCC)](https://github.com/MPEGGroup/mpeg-pcc-tmc13), and add tmc3 to your environment variable or manually specify its location in [the code](https://github.com/maincold2/OMG/blob/main/utils/gpcc_utils.py) (lines 243 and 258, this script is sourced from [HAC++](https://github.com/YihangChen-ee/HAC-plus)).
If you have trouble in installing cuml, please refer to the [CUML Installation Guide](https://docs.rapids.ai/install/).

We used [Mip-NeRF 360](https://jonbarron.info/mipnerf360/), [Tanks & Temples, and Deep Blending](https://repo-sam.inria.fr/fungraph/3d-gaussian-splatting/datasets/input/tandt_db.zip).

## Running

### Pre-training (Mini-Splatting)

```shell
#for outdoor scenes (e.g., Mip-NeRF 360 outdoor and T&T scenes)
python pretrain.py -s <path to COLMAP>  -m  <model path> --eval --imp_metric outdoor --sh_degree 3   --iterations 30000
#for indoor scenes (e.g., Mip-NeRF 360 indoor and DB scenes)
python pretrain.py -s <path to COLMAP>  -m  <model path> --eval --imp_metric indoor --sh_degree 3   --iterations 30000

```

### Fine-tune
```shell
python train.py -s  <path to COLMAP> -m <model path>  --eval --start_checkpoint  <model path>/chkpnt30000.pth 

```

## Evaluation
```shell
python render.py -s <path to COLMAP> -m <model path> --decode
python metrics.py -m <model path> 
```
#### --decode
Rendering with the compressed file (comp.xz), otherwise using the ply file. The results are the same regardless of this option.



## 👍 **Acknowledgement**
This work is built on many amazing research works and open-source projects, thanks a lot to all the authors for sharing!
* [Mini-Splatting](https://github.com/fatPeter/mini-splatting)
* [OMG](https://github.com/cvlab-columbia/zero123)




## BibTeX
```
@misc{du2026mobile-gs,
      title={Mobile-GS: Real-time Gaussian Splatting for Mobile Devices}, 
      author={Xiaobiao Du and Yida Wang and Kun Zhan and Xin Yu},
      year={2026},
      eprint={2603.11531},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2603.11531}, 
}
```
