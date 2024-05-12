# COMP5329-Project

train:\
python basicsr/train.py -opt options/Train/train_x2.yml\
python basicsr/train.py -opt options/Train/train_x3.yml\
python basicsr/train.py -opt options/Train/train_x4.yml

test:\
python basicsr/test.py -opt options/Test/test_x2.yml\
python basicsr/test.py -opt options/Test/test_x3.yml\
python basicsr/test.py -opt options/Test/test_x4.yml

ablation study:\
python basicsr/test.py -opt options/Test/test_ablation_STB_CMB_MCRM.yml\
python basicsr/test.py -opt options/Test/test_ablation_STB_CMB.yml\
python basicsr/test.py -opt options/Test/test_ablation_STB_STB_MCRM.yml
python basicsr/test.py -opt options/Test/test_ablation_STB_STB.yml\
python basicsr/test.py -opt options/Test/text_ablation_STB_CTB_MCRM.yml