# ActivityNet Entities dataset
This repo hosts the dataset used in our paper [Grounded Video Description](https://arxiv.org/abs/1812.06587).

ActivityNet-Entities, is based on the video description dataset [ActivityNet Captions](https://cs.stanford.edu/people/ranjaykrishna/densevid/) and augments it with 158k bounding box annotations, each grounding a noun phrase (NP). Here we release the complete set of NP-based annotations as well as the pre-processed object-based annotations.

<img src='demo/dataset_teaser.png' alt="dataset teaser" width="80%"/>

### Data
We have the following dataset files under the `data` directory:

- `anet_entities_trainval.json`: The raw dataset file with noun phrase and bounding box annotations. We only release the training and the validation splits for now.

- `anet_entities_cleaned_class_thresh50_trainval.json`: Pre-processed dataset file with object class and bounding box annotations. For training and validation splits only.

- `anet_entities_skeleton.txt`: Specify the expected structure of the JSON annotation files.

- `split_ids_anet_entities.json`: Video IDs included in the training/validation/testing splits.

- `anet_entities_cleaned_class_thresh50_test_skeleton.json`: Object class annotation for the testing split. This file is for evaluation server purpose and the bounding box annotation is not given. See below for more details.

Note: Both the raw dataset file and the pre-processed dataset file contains all the 12469 videos in the original training and validation splits (as in ActivityNet Captions, which is based on [ActivityNet 1.3](http://activity-net.org/download.html)). This includes 626 videos without box annotations.

### Evaluation
Under the `scripts` directory, we include:
- `attr_prep_tag_NP.py`: The preprocessing scripts to obtain the NP/object annotation files.
- `anet_entities_np_stats.py`, `anet_entities_object_stats.py`: The scripts that print the dataset stats.
- `eval_grd_anet_entities.py`: The evaluation script for object grounding on GT captions. [PyTorch](https://pytorch.org/get-started/locally/) is required. To evaluate your results, simply run:
```
python scripts/eval_grd_anet_entities.py -s YOUR_SUBMISSION_FILE.JSON
```
Please follow the example in `data/anet_entities_skeleton.txt` to format your submission file.


### Others
Please contact <luozhou@umich.edu> if you have any trouble running the code. Please cite the following paper if you use the dataset.
```
@article{zhou2018grounded,
  title={Grounded Video Description},
  author={Zhou, Luowei and Kalantidis, Yannis and Chen, Xinlei and Corso, Jason J and Rohrbach, Marcus},
  journal={arXiv preprint arXiv:1812.06587},
  year={2018}
}
```
### License
This project is licensed under the license found in the LICENSE file in the root directory of this source tree.

The noun phrases in these annotations are based on [ActivityNet Captions](https://cs.stanford.edu/people/ranjaykrishna/densevid/), which are linked to videos in [ActivityNet 1.3](http://activity-net.org/download.html) 
