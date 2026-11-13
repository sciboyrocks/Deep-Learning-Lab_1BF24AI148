# Deep Learning Lab — Continuous Evaluation Programs

**Name:** Samrudh Raikote · **USN:** 1BF24AI148

This repository holds all the self-learning / continuous evaluation lab programs for the Deep Learning Lab.

| # | Program | Folder |
|---|---|---|
| 1 | _(add Program 1 here)_ | `Program_01_...` |
| 2 | Hugging Face Hub, dataset loading & model cards · Convolution and max-pooling in NumPy · Kernel size / stride / padding · Basic CNN for CIFAR-10 | [`Program_02_HF_Hub_Conv_Pool_CNN`](Program_02_HF_Hub_Conv_Pool_CNN) |

## Setup

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
pip install jupyter        # optional, to open the notebooks interactively
```

Run a program notebook end to end:

```bash
jupyter nbconvert --to notebook --execute --inplace Program_02_HF_Hub_Conv_Pool_CNN/Program2_HF_Conv_Pool_CNN.ipynb
```

Datasets are downloaded from the Hugging Face Hub on first run and cached in `~/.cache/huggingface`.
