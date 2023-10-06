# Video-based-gait-analysis-for-dementia
MAX-GRNet: Human Pose Estimation from Video
| Architecture                                                                                               |                                           
|------------------------------------------------------------------------------------------------------------|
| ![Architecture](https://github.com/lisqzqng/Video-based-gait-analysis-for-dementia/blob/main/Full_MAX-GRNet.png)| 

| Qualitative Result                                                                                         | 
|------------------------------------------------------------------------------------------------------------| 
| ![Qualitative Result](https://github.com/lisqzqng/Video-based-gait-analysis-for-dementia/blob/main/sample_with_skeleton.gif)|

## Getting Started
Video-based-gait-analysis-for-dementia has been implemented and tested on Ubuntu 20.04, GeForce RTX 3090 with python >= 3.7 and cuda >= 11.0. It supports both GPU and CPU inference.

Clone the repo:
```bash
git clone https://github.com/lisqzqng/Video-based-gait-analysis-for-dementia.git
```

Get into the directory Video-based-gait-analysis-for-dementia/. Install the requirements using `conda`. If you donnot have `conda`, use following commands to install on linux:
```bash
# find the version you want on `https://repo.anaconda.com/miniconda/`
curl -O https://repo.anaconda.com/miniconda/Miniconda-3.7.3-Linux-x86_64.sh
# then follow the prompts. The defaults are generally good.
sh Miniconda-3.7.3-Linux-x86_64.sh
```
```bash
# conda
source scripts/install_conda.sh
```
( Please ignore the error related to tensorflow/tensorboard installation. )

Before eventually running the code, you need download the required data(i.e trained models, SMPL model parameters, etc.). To do this you can just run:

```bash
source scripts/prepare_data.sh
```
## Batch generating the 3D joints

Please refer to [the instructions](doc/batch_generation.md) for execution details.

## Running the Demo
We have prepared a demo code to run Video-based-gait-analysis-for-dementia on arbitrary videos. You can run the demo as following:

```bash
# Run on a local video
python demo.py --vid_file sample_video.mp4 --output_folder output/ --display
```
```bash
# Run on a YouTube video on CPU
python demo.py --vid_file https://www.youtube.com/xxxxx --output_folder output/ --display --cpu_only
```
```bash
# Run on video with mesh output
python demo.py --vid_file sample_video.mp4 --output_folder output/ --ckpt checkpoint/max-grnet.pth.tar
```

Refer to [`doc/demo.md`](doc/demo.md) for more details about the demo code.

## References
This project mainly benefits from the following resources: 
  - Pretrained HMR and some functions are borrowed from [SPIN](https://github.com/nkolot/SPIN).
  - SMPL models and layer is from [SMPL-X model](https://github.com/vchoutas/smplx).
  - GAN-based pose estimation structure is referred from [VIBE](https://github.com/mkocabas/VIBE).
  - Pretrained Part Attention model and structures are borrowed from [PARE](https://github.com/mkocabas/PARE).
