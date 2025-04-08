# HarDNet-CWS: An Enhanced Harmonic Densely Connected Hybrid Transformer Network Architecture for Chronic Wound Segmentation Utilising Multi-Colour Space Tensor Merging

Source code for the HarDNet-CWS architecture. This is a modified HarDNet segmentation model which shows improvements in performance when trained on light skin patients and tested on patients with darker skin tones. The main ehancements come from three core adjustments: (1) a tensor merging process that combines RGB tensors with an exaggerated luminance channel, (2) implementation of a modified stem with non-destructive contrast elimination, and (3) a rebalanced HarDNet block design.

If you use any of the concepts or code from this repository, please consider citing our paper:

```BibTex
@article{cassidy2024cws,
 title   = {An Enhanced Harmonic Densely Connected Hybrid Transformer Network Architecture for Chronic Wound Segmentation Utilising Multi-Colour Space Tensor Merging},
 author  = {Bill Cassidy and Christian McBride and Connah Kendrick and Neil D. Reeves and Joseph M. Pappachan and Cornelius J. Fernandez and Elias Chacko and Raphael Brüngel and Christoph M. Friedrich and Metib Alotaibi and Abdullah Abdulaziz AlWabel and Mohammad Alderwish and Kuan-Ying Lai and Moi Hoon Yap},
 year    = {2024},
 journal = {arXiv preprint arXiv:2410.03359}
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

After the model has been trained, the trained weights will be saved to the weights/exp directory.

Test the model using:

    python test.py --rect --tta vh

Test metrics can then be generated using:

    python get_metrics.py

Test metrics are saved to the metrics directory.
