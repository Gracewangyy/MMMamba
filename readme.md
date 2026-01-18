# MMMamba

This folder contains the implementation of **MMMamba**, as described in the paper [MMMamba: A Versatile Cross-Modal In Context Fusion Framework for Pan-Sharpening and Zero-Shot Image Enhancement](https://arxiv.org/abs/2512.15261).

**MMMamba** is a novel framework built upon the Mamba architecture that introduces a **Cross-Modal In-Context Fusion** approach. Unlike traditional concatenation or cross-attention methods, MMMamba employs in-context conditioning and a **Multimodal Interleaved (MI) scanning mechanism** to facilitate efficient and direct information exchange between PAN and MS modalities with linear computational complexity. It also supports image super-resolution in a zero-shot manner.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

In order to run this implementation, you need to have the following software and libraries installed:

- Python 3.7 or later
- PyTorch 1.6 or later
- CUDA (if using GPU)
- NumPy
- Matplotlib
- OpenCV
- PyYAML

### Installing

**Important:** Please follow the instructions in  the official Mamba installation guide to install the Mamba block environment first, as this project depends on `causal-conv1d` and `mamba-ssm`.

You can install the other necessary packages using pip:

Bash

```
pip install torch numpy matplotlib opencv-python pyyaml
```

### Configuration

Before training or testing the model, you need to configure the options in the `option.yaml` file:

- `log_dir`: The directory to store the training log files.
- `checkpoint`: The directory to store the trained model parameters.
- `data_dir_train`: The directory of the training data.
- `data_dir_eval`: The directory of the evaluation data.

### Training the Model

To train the MMMamba model, run the following command:

Bash

```
python main.py
```

### Testing the Model

To test the trained model, you can run:

Bash

```
python test.py
# Or for deep learning based demonstration methods:
python py-tra/demo_deep_methods.py
```

### Configuration Details (`option.yaml`)

The configuration options are stored in the `option.yaml` file. Below is an explanation of key options:

#### Algorithm & Model

- `algorithm`: The model name for training (e.g., `MMMamba`).
- `model`: The specific model architecture location to use.

#### Logging & Weights

- `log_dir`: Location for log files.
- `checkpoint`: Location to store/load model weights.

#### Data Paths

- `data_dir_train`: Path to training dataset.
- `data_dir_eval`: Path to evaluation/test dataset.
- `source_ms`: Keyword/folder for multi-spectral data.
- `source_pan`: Keyword/folder for panchromatic data.

#### Pretraining

- `pretrained`: Set to `true` to use a pretrained model.
- `pre_sr`: Path to the specific pretrained `.pth` file.

#### Data Processing Hyperparameters

- `upscale`: Upscale factor (usually 4 for Pan-sharpening).
- `batch_size`: Batch size for training.
- `patch_size`: Image patch size (crop size).
- `data_augmentation`: Enable/disable data augmentation (Flip, Rotation).
- `n_colors`: Number of spectral bands/channels.
- `rgb_range`: Value range of the input images (e.g., 255 or 1).
- `normalize`: Whether to normalize input data.

#### Optimization

- `schedule.lr`: Learning rate.
- `schedule.decay`: Learning rate decay type (e.g., `step`).
- `schedule.optimizer`: Optimizer (ADAM, SGD, RMSprop).

## Citation

If you find this code or work helpful, please cite our paper:

```
@article{wang2025mmmamba,
  title={MMMamba: A Versatile Cross-Modal In Context Fusion Framework for Pan-Sharpening and Zero-Shot Image Enhancement},
  author={Wang, Yingying and He, Xuanhua and Wu, Chen and Huang, Jialing and Zhang, Suiyun and Liu, Rui and Ding, Xinghao and Che, Haoxuan},
  journal={arXiv preprint arXiv:2512.15261},
  year={2025}
}
```
