This is the official source code of our paper: **"Enhancing Semantic Correlation between Instances and Relations for Zero-Shot Relation Extraction"**, Journal of Natural Language Processing.

To reproduce our reported experimental results, please follow steps below:

## 1. **Hardware Environment Information**

All our experiments were performed on 1 NVIDIA RTX A6000 GPU 48GB (CUDA version 11.6). 

## 2. **Prepare Conda Environment**

Create a new conda environment via commands:

conda create --name env_zsre python=3.6

Then, please install all required packages for this conda environment in the file: "Code-ZSRE/requirements.txt". Next, we active the conda environment env_zsre:

conda activate env_zsre

## 3. **How to Run Experiments**

### + Datasets:
Both FewRel and Wiki-ZSL datasets are in the folder: "Code-ZSRE/official_data". Also, the relation labels and descriptions are available.
As introduced in the paper, we split the entire datasets into training and test sets, where the number of unseen relations in the test set is 15 (m=15).
We repeat this division 5 times for 5 different random selections of m.
Finally, the division result is saved in the file: "Code-ZSRE/official_data/split_train_test_sets/official_data_divisions.json"

### + Train and evaluate on Wiki-ZSL set:
We run 5 times with 5 different random selections according to id_round in [1,2,3,4,5].
Inside the folder: "Code-ZSRE/Wiki-ZSL"

cd Code-ZSRE/Wiki-ZSL

CUDA_VISIBLE_DEVICES=0 python train.py --alpha 1 --n_unseen 15 --K 5 --id_round 1

CUDA_VISIBLE_DEVICES=0 python train.py --alpha 1 --n_unseen 15 --K 5 --id_round 2

CUDA_VISIBLE_DEVICES=0 python train.py --alpha 1 --n_unseen 15 --K 5 --id_round 3

CUDA_VISIBLE_DEVICES=0 python train.py --alpha 1 --n_unseen 15 --K 5 --id_round 4

CUDA_VISIBLE_DEVICES=0 python train.py --alpha 1 --n_unseen 15 --K 5 --id_round 5

The final reported performance on Wiki-ZSL is avaraged of 5 the results by running 5 times above.


### + Train and evaluate on FewRel set:
Similarly, we also perform the experiment 5 times.
Inside the folder: "Code-ZSRE/FewRel"

cd Code-ZSRE/FewRel

CUDA_VISIBLE_DEVICES=0 python train.py --alpha 1 --n_unseen 15 --K 5 --id_round 1

CUDA_VISIBLE_DEVICES=0 python train.py --alpha 1 --n_unseen 15 --K 5 --id_round 2

CUDA_VISIBLE_DEVICES=0 python train.py --alpha 1 --n_unseen 15 --K 5 --id_round 3

CUDA_VISIBLE_DEVICES=0 python train.py --alpha 1 --n_unseen 15 --K 5 --id_round 4

CUDA_VISIBLE_DEVICES=0 python train.py --alpha 1 --n_unseen 15 --K 5 --id_round 5

The final reported performance on FewRel is avaraged of 5 the results by running 5 times above.

