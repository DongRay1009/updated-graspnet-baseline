The detailed installation process will not be repeated here, so you can go to the original github repository to find it.
Since graspnet-baseline is based on an older version of the torch, newer versions of the torch no longer support some of the code. So here are some changes to make this part of the code work with the newer versions of the torch.

## Installation
Get the code.
```bash
git clone https://github.com/graspnet/graspnet-baseline.git
cd graspnet-baseline
```
Install packages via Pip. PS: You need to note that you need to use a version of python lower than 3.12, because open3d version is not supported, and I am using python 3.7. Also you need to install torch to match the cuda version, so that you can successfully install pointnet2 and knn later.
```bash
pip install -r requirements.txt
```
Compile and install pointnet2 operators (code adapted from [votenet](https://github.com/facebookresearch/votenet)).
```bash
cd pointnet2
python setup.py install
```
Compile and install knn operator (code adapted from [pytorch_knn_cuda](https://github.com/chrischoy/pytorch_knn_cuda)).
```bash
cd knn
python setup.py install
```
Install graspnetAPI for evaluation.
```bash
git clone https://github.com/graspnet/graspnetAPI.git
cd graspnetAPI
pip install .
```
or you can pip install
```bash
pip install graspnetAPI
```

## Testing

To verify that the installation was successful, create the folder logs/log_kn and download the following checkpoint-kn.tar, rename it to checkpoint.tar and place it in there

The pretrained weights can be downloaded from:

- `checkpoint-rs.tar`
[[Google Drive](https://drive.google.com/file/d/1hd0G8LN6tRpi4742XOTEisbTXNZ-1jmk/view?usp=sharing)]
[[Baidu Pan](https://pan.baidu.com/s/1Eme60l39tTZrilF0I86R5A)]
- `checkpoint-kn.tar`
[[Google Drive](https://drive.google.com/file/d/1vK-d0yxwyJwXHYWOtH1bDMoe--uZ2oLX/view?usp=sharing)]
[[Baidu Pan](https://pan.baidu.com/s/1QpYzzyID-aG5CgHjPFNB9g)]

`checkpoint-rs.tar` and `checkpoint-kn.tar` are trained using RealSense data and Kinect data respectively.


```bash
sh command_demo.sh
```
Then run the demo, and when the image from the original repository appears, it proves that the installation has been successful!

## Acknowledgements
Special thanks to chenxin-wang and fang-haoshu(https://github.com/graspnet/graspnet-baseline) for creating this amazing project. The modifications in this repository were inspired by their work.
