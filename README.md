Hierarchical Image Graph with Scale Importance
=====

Implementation of our IEEE ISM 2023 paper "Multi-Scale Image Graph Representation: A Novel GNN Approach for Image Classification through Scale Importance Estimation" authored by:
[João Pedro Oliveira Batisteli](https://lattes.cnpq.br/8128547685252443), [Silvio Jamil F. Guimarães](http://lattes.cnpq.br/8522089151904453) and
[Zenilton K. G. Patrocínio Jr](http://lattes.cnpq.br/8895634496108399),

Image representation as graphs can enhance the understanding of image semantics and facilitate multi-scale image representation. However, existing methods often overlook the significance of the relationship between elements at each scale or fail to encode the hierarchical relationship between graph elements. To cope with that, we introduce a novel approach for graph construction from images. This approach utilizes a hierarchical image segmentation technique to generate segmentation at multiple scales and incorporates edges to encode the relationships at each scale. We also propose a new readout function that weighs the importance of each scale when deriving a fixed-size graph representation. Furthermore, we present a new model incorporating those ideas -- called Hierarchical Image Graph with Scale Importance (HIGSI). Experimental results on the CIFAR-10 database indicate that our proposed model outperforms (or closely matches) state-of-the-art and baseline models while utilizing smaller graphs.

## Getting started

### Prerequisites

0. Clone this repository

```
git clone "https://github.com/IMScience-PPGINF-PucMinas/HIGSI.git"
cd "HIGSI"
```

1. Create and activate the environment

```bash
conda env create -f environment.yml
conda activate higsi
```

2. Prepare feature files

The program will download the CIFAR-10 dataset and generate the graphs at first time you execute the training or test script. The graphs will be saved in the `data/processed` for future use. 

If you want to change the target number of superpixels, you need to modify the `nodes` parameter in the training files for each model. The nodes parameter determines how many superpixels the model will generate. For the HIGHSI model, the training file is MG_train.py. You can find the nodes parameter on lines 97, 98 and 99. For the BRM model, the training file is train.py. You can find the nodes parameter on lines 86, 87 and 88.

The dataset will be saved in the `data/processed` folder after you create it. If you want to generate new graphs, you have to delete the existing files in that folder first. Otherwise, the program will use the old files and not create new ones.

### Training and Inference

1. Before you start the model training, you need to launch the mlflow server in a terminal. This will allow you to monitor the model metrics during the training process. To launch the mlflow server, use the following command:

```bash
mlflow ui
```

To start the training scripts, you need to open another terminal and specify the random seed you want to use. The random seed will affect the initialization of the model parameters and the shuffling of the data. You can use any integer value for the random seed.

To run the training script with a given random seed for the BRM model with seed 1, for example, use the following command:

```bash
python train.py 1
```

For the HIGSI model:

```bash
python RG_train.py 1
```

If you want to reproduce the results from the article, you need to run different shell scripts for each model. The shell scripts will run the experiments with the same random seeds that were used in the article. For the HIGHSI model, run the `MG_train_runs.sh` script. For the BRM model, run the `train_runs.sh` script.

2. To perform model testing, it is only necessary to pass the seed that the model was trained on.
For the BRM model with seed 1, for example, run the command:

```bash
python test.py 1
```

For the HIGSI model:

```bash
python RG_test.py 1
```

Don't forget to change directory to the model weights you want to test.

## Citations

If you find this code useful for your research, consider cite our paper:


## Contact

João Pedro Oliveira Batisteli: <joao.batisteli@sga.pucminas.br>
