# HarDNet-CWS: An Enhanced Harmonic Densely Connected Hybrid Transformer Network Architecture for Chronic Wound Segmentation Utilising Multi-Colour Space Tensor Merging

Source code for the HarDNet-CWS architecture. This is a modified HarDNet-DFUS segmentation model which shows improvements in performance when trained on light skin patients and tested on patients with darker skin tones. The main ehancements come from three core adjustments: (1) a tensor merging process that combines RGB tensors with an exaggerated luminance channel (see ``utils/dataloader.py``), (2) implementation of a modified stem with non-destructive contrast elimination (see ``lib/HarDMSEG.py``, ``lib/kingnet.py``, and ``lib/layers.py``), and (3) a rebalanced HarDNet block design (see ``lib/kingnet.py``).

If you use any of the concepts or code from this repository, please consider citing our paper:

```BibTex
@article{cassidy2025cws,
 title   = {An Enhanced Harmonic Densely Connected Hybrid Transformer Network Architecture for Chronic Wound Segmentation Utilising Multi-Colour Space Tensor Merging},
 author  = {Bill Cassidy and Christian McBride and Connah Kendrick and Neil D. Reeves and Joseph M. Pappachan and Cornelius J. Fernandez and Elias Chacko and Raphael Brüngel and Christoph M. Friedrich and Metib Alotaibi and Abdullah Abdulaziz AlWabel and Mohammad Alderwish and Kuan-Ying Lai and Moi Hoon Yap},
 year    = {2025},
 journal = {Computers in Biology and Medicine},
 volume  = {192},
 pages   = {110172},
 issn    = {0010-4825},
 doi     = {https://doi.org/10.1016/j.compbiomed.2025.110172}
} 
```

Before training the model, create the conda environment as follows:

    conda env create -f environment.yml

The dataset should be organised using the following directory structure:

    dataset
    ├─ train
    |   └─ images
    |   └─ masks
    └─ test
        └─ images
        └─ masks

You can then train the model using:

    python train.py --rect --augmentation

After the model has been trained, the trained weights will be saved to the ``weights/exp`` directory.

Test the model using:

    python test.py --rect --tta vh

Prediction masks are saved to the ``pred_mask`` directory.

Convert the prediction masks to 8-bit:

    python convert_masks.py

Test metrics can then be generated using:

    python get_metrics.py

Test metrics are saved to the ``metrics`` directory.

For more information on the base architecture (HarDNet-DFUS), please refer to the original [repository](https://github.com/YuWenLo/HarDNet-DFUS).
