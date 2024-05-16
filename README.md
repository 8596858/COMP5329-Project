# COMP5329-Project

## Dependencies

- Python 3.10
- PyTorch 2.1.2
- NVIDIA GPU + [CUDA](https://developer.nvidia.com/cuda-downloads)

## install:
```bash
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

## ablation study:
```shell
# The ablation study on CMB and MCRM
python basicsr/test.py -opt options/Test/test_ablation_STB_CMB_MCRM.yml
python basicsr/test.py -opt options/Test/test_ablation_STB_CMB.yml
python basicsr/test.py -opt options/Test/test_ablation_STB_STB_MCRM.yml
python basicsr/test.py -opt options/Test/test_ablation_STB_STB.yml

# The ablation study on VMM in CMB
python basicsr/test.py -opt options/Test/text_ablation_STB_CTB_MCRM.yml
```

## Hyperparameter Analysis:
```shell
# Analysis on the Block expansion factor in MCRM
python basicsr/test.py -opt options/Test/hyper_block_1_MCRM.yml
python basicsr/test.py -opt options/Test/hyper_block_4_MCRM.yml

# Analysis on the Block expansion factor in CMB
python basicsr/test.py -opt options/Test/hyper_block_1_CMB.yml
python basicsr/test.py -opt options/Test/hyper_block_2_CMB.yml

# Analysis on the SSM state expansion factor in MCRM
python basicsr/test.py -opt options/Test/hyper_state_16_MCRM.yml
python basicsr/test.py -opt options/Test/hyper_state_32_MCRM.yml

# Analysis on the SSM state expansion factor in CMB
python basicsr/test.py -opt options/Test/hyper_state_16_CMB.yml
python basicsr/test.py -opt options/Test/hyper_state_64_CMB.yml

# Analysis on the Local convolution width in MCRM
python basicsr/test.py -opt options/Test/hyper_conv_2_MCRM.yml
python basicsr/test.py -opt options/Test/hyper_conv_3_MCRM.yml

# Analysis on the Local convolution width in CMB
python basicsr/test.py -opt options/Test/hyper_conv_2_CMB.yml
python basicsr/test.py -opt options/Test/hyper_conv_4_CMB.yml

# Analysis on the depth of the network
python basicsr/test.py -opt options/Test/hyper_depth_6.yml
python basicsr/test.py -opt options/Test/hyper_depth_12.yml
```

The implementation is based on DAT: https://github.com/zhengchen1999/DAT/tree/main?tab=readme-ov-file