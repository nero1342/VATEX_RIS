The official implementation of the paper:

<div align="center">
<h1>
<b>
Vision-Aware Text Features in Referring Image Segmentation: <br> From Object Understanding to Context Understanding
</b>
</h1>
</div>
<p align="center">
  <img src="assets/teaser.png" width="600">
</p>

## Abstract
Referring image segmentation is a challenging task that involves generating pixel-wise segmentation masks based on natural language descriptions. The complexity of this task increases with the intricacy of the sentences provided. 
Existing methods have relied mostly on visual features to generate the segmentation masks while treating text features as supporting components. 
However, this under-utilization of text understanding limits the model's capability to fully comprehend the given expressions. 
In this work, we propose a novel framework that specifically emphasizes object and context comprehension inspired by human cognitive processes through Vision-Aware Text Features.
Firstly, we introduce a CLIP Prior module to localize the main object of interest and embed the object heatmap into the query initialization process.
Secondly, we propose a combination of two components: Contextual Multimodal Decoder and Meaning Consistency Constraint, to further enhance the coherent and consistent interpretation of language cues with the contextual understanding obtained from the image. 
Our method achieves significant performance improvements on three benchmark datasets RefCOCO, RefCOCO+ and G-Ref.

<!-- ## Update
``` update here ``` -->
## Requirements
We test our work in the following environments, other versions may also be compatible:
- CUDA 11.1
- Python 3.8
- Pytorch 1.9.0

## Installation
Please refer to [installation.md](docs/installation.md) for installation

## Data preparation
Please refer to [data.md](docs/data.md) for data preparation.

## Getting Started with VATEX 
Download the pretrained model from ImageNet of Swin-B, Swin-L and Video-Swin-B and put in weights folder 

## Training 
To train VATEX with "train_net_video.py", first setup the corresponding datasets following [data.md](docs/data.md), then run:
```
python train_net_video.py --config configs/refcoco/swin/swin_base.yaml --num-gpus 2 OUTPUT_DIR ${OUTPUT_DIR} $
```
where OUTPUT_DIR is the output direction to save weight and log.

To resume the training process 
```
python train_net_video.py --config configs/refcoco/swin/swin_base.yaml --num-gpus 2 --resume OUTPUT_DIR ${OUTPUT_DIR} $
```
## Evaluation
```
python train_net_video.py --config configs/refcoco/swin/swin_base.yaml --num-gpus 2 --eval-only OUTPUT_DIR ${OUTPUT_DIR} $ MODEL.WEIGHTS link_to_weights
```
## Main Results

Main results on RefCOCO

| Backbone | val | test A | test B |
| ---- |:-------------:| :-----:|:-----:|
| ResNet101 | 75.66 | 77.88 | 72.36 |
| Swin-B | 78.16  |   79.64  | 75.64 |

Main results on RefCOCO+

| Backbone | val | test A | test B |
| ---- |:-------------:| :-----:|:-----:|
| Swin-B | 70.02 | 74.41 | 62.52 |

Main results on G-Ref

| Backbone | val | test |
| ---- |:-------------:| :-----:|
| Swin-B | 69.73 | 70.58|





## Demo
<p align="center">
  <img src="assets/demo1.png" width="600">
</p>
