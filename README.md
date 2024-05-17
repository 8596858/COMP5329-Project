# COMP5329-Project

## Dependencies

- Python 3.10
- PyTorch 2.1.2
- NVIDIA GPU + [CUDA](https://developer.nvidia.com/cuda-downloads)

## install:
```bash
# Clone the github repo and go to the default directory 'COMP5329-Project'.
git clone https://github.com/8596858/COMP5329-Project.git
conda create -n NewSR python=3.10
conda activate NewSR
pip install -r requirements.txt
cd causal-conv1d
python setup.py install
cd ..
cd mamba
python setup.py install
cd ..
python setup.py develop
```

## datasets and pretrained models:
[Google Drive](https://drive.google.com/drive/folders/19P2tB8aBen5DE8Zis_ZsGO-VglqlM80G?usp=sharing)

## Main Contribution:
Channel Mamba Block: in basicsr/archs/new_arch.py class Channel_Mamba_Block.\
Mamba Channel Recursion Module: in basicsr/archs/new_arch.py class ResidualGroup.

## train:
```shell
python basicsr/train.py -opt options/Train/train_x2.yml
python basicsr/train.py -opt options/Train/train_x3.yml
python basicsr/train.py -opt options/Train/train_x4.yml
```

## test:
```shell
python basicsr/test.py -opt options/Test/test_x2.yml
python basicsr/test.py -opt options/Test/test_x3.yml
python basicsr/test.py -opt options/Test/test_x4.yml
```

## Ablation study:
```shell
# The ablation study on CMB and MCRM
# The model with the whole structure
python basicsr/test.py -opt options/Test/test_ablation_STB_CMB_MCRM.yml
# The model without the MCRM
python basicsr/test.py -opt options/Test/test_ablation_STB_CMB.yml
# The model without the CMB
python basicsr/test.py -opt options/Test/test_ablation_STB_STB_MCRM.yml
# The model without the MCRM and CMB
python basicsr/test.py -opt options/Test/test_ablation_STB_STB.yml

# The ablation study on VMM in CMB
# The model without VMM in CMB
python basicsr/test.py -opt options/Test/text_ablation_STB_CTB_MCRM.yml
# The model with VMM in CMB
python basicsr/test.py -opt options/Test/test_ablation_STB_CMB_MCRM.yml
```

## Hyperparameter Analysis:
```shell
#The baseline model
python basicsr/test.py -opt options/Test/test_ablation_STB_CMB_MCRM.yml

# Analysis of the Block expansion factor in MCRM
# The Block expansion factor is 1
python basicsr/test.py -opt options/Test/hyper_block_1_MCRM.yml
# The Block expansion factor is 4
python basicsr/test.py -opt options/Test/hyper_block_4_MCRM.yml

# Analysis of the Block expansion factor in CMB
# The Block expansion factor is 1
python basicsr/test.py -opt options/Test/hyper_block_1_CMB.yml
# The Block expansion factor is 2
python basicsr/test.py -opt options/Test/hyper_block_2_CMB.yml

# Analysis of the SSM state expansion factor in MCRM
# The SSM state expansion factor is 16
python basicsr/test.py -opt options/Test/hyper_state_16_MCRM.yml
# The SSM state expansion factor is 32
python basicsr/test.py -opt options/Test/hyper_state_32_MCRM.yml

# Analysis of the SSM state expansion factor in CMB
# The SSM state expansion factor is 16
python basicsr/test.py -opt options/Test/hyper_state_16_CMB.yml
# The SSM state expansion factor is 64
python basicsr/test.py -opt options/Test/hyper_state_64_CMB.yml

# Analysis of the Local convolution width in MCRM
# The Local convolution width is 2
python basicsr/test.py -opt options/Test/hyper_conv_2_MCRM.yml
# The Local convolution width is 3
python basicsr/test.py -opt options/Test/hyper_conv_3_MCRM.yml

# Analysis of the Local convolution width in CMB
# The Local convolution width is 2
python basicsr/test.py -opt options/Test/hyper_conv_2_CMB.yml
# The Local convolution width is 4
python basicsr/test.py -opt options/Test/hyper_conv_4_CMB.yml

# Analysis of the depth of the network
# The number of SAMB is 3
python basicsr/test.py -opt options/Test/hyper_depth_6.yml
# The number of SAMB is 6
python basicsr/test.py -opt options/Test/hyper_depth_12.yml
```

The implementation is based on [DAT](https://github.com/zhengchen1999/DAT/tree/main?tab=readme-ov-file) and [Vision Mamba](https://github.com/hustvl/Vim/tree/main?tab=readme-ov-file)\
The code is based on the [basicsr](https://github.com/XPixelGroup/BasicSR)
