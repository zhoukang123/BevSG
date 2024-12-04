# BevSG
Code and datasets for paper “Learning Bird’s Eye View Scene Graph and Knowledge-Inspired Policy for Embodied Visual Navigation”

## Learning Bird’s Eye View Scene Graph and Knowledge-Inspired Policy for Embodied Visual Navigation
We propose BevNav framework to solve these issues by three parts: (i) we introduce a novel Bird’s Eye View  
(BEV) scene graph (BevSG) that utilizes multi-view 2D information transformed into 3D under the  
supervision of 3D detection to encode scene layouts and geometric clues. It can distinguish multi-view  
semantically similar objects and make plans in this graph. (ii) we propose BEV-BLIP contrastive  
learning that aligns the BEV and language grounding inputs transferring constrain commonsense  
knowledge in pre-trained models without other training in the environments. (iii) we design BEV-  
based view search navigation policy, which encourages representations that encode the semantics,  
relationships, and positional information of objects. This policy leverages the topological relations of  
locally collected BEV representations to infer invisible objects.    

## Setup
- *Dependeces*: We use earlier (0.2.2) versions of [habitat-sim](https://github.com/facebookresearch/habitat-sim/tree/v0.2.2) and [habitat-lab](https://github.com/facebookresearch/habitat-sim/tree/v0.2.2). Other related depencese can be found in requirements.txt.  
- *Data(MatterPort3D*: Please download the scene dataset and the episode dataset from [habitat-lab/DATASETS.md](https://github.com/facebookresearch/habitat-sim/blob/main/DATASETS.md#matterport3d-mp3d-dataset)

## Installation

**Step 1**
Download Matterport3D scene dataset from [here](https://niessner.github.io/Matterport/).
Download object-goal navigation episodes dataset from [here](https://github.com/facebookresearch/habitat-lab/blob/main/DATASETS.md).
According to your dataset path, set the scene dataset path (SCENES_DIR) and episode dataset path (DATA_PATH) in config file `configs/challenge_objectnav2021.local.rgbd.yaml`.

**Step 2**
Install habitat-sim according to [here](https://github.com/facebookresearch/habitat-sim).
Install habitat-lab according to [here](https://github.com/facebookresearch/habitat-lab) or install habitat-lab with ``pip install -e habitat-lab``.

**Step 3**
Install the conda environment we provided.
```
conda env create -f BevSG_Nav.yml
```

**Step 4**
Install GLIP model.
```
cd GLIP
python setup.py build develop --user
```
Download GLIP checkpoint.
```
cd MODEL
wget https://huggingface.co/GLIPModel/GLIP/resolve/main/glip_large_model.pth
```

**Step 5**
Install ConceptGraph according to [here](https://github.com/concept-graphs/concept-graphs).

Then organize the files as follows:
```
3dAwareNav/
  data/
    scene_datasets/
        mp3d/
    episode_datasets/
        objectnav_mp3d_v1/
```
The weight of our 2D backbone RedNet can be found in [Stubborn](https://github.com/Improbable-AI/Stubborn).


## Training and Evaluating:

We provide scripts for quick training and evaluation. The parameters can be found in [sh_train_mp3d.sh](sh_train_mp3d.sh) and [sh_eval.sh](sh_eval.sh), You can modify these parameters to customize them according to your specific requirements.
```
sh sh_train_mp3d.sh # training 
sh sh_eval.sh # evaluating
```
