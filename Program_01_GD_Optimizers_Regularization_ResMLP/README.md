# Lab Program 1 — Gradient Descent Variants, Optimizers, Regularization and Residual MLPs

**Problem statement:** Demonstrate batch, stochastic, and mini-batch gradient descent on a small dataset. Using an MLP on a
subset of Fashion-MNIST, compare selected momentum-based and adaptive optimizers with constant and scheduled learning rates.
Investigate overfitting, evaluate dropout, L2 regularization, and data augmentation, apply early stopping, and compare plain
and residual MLPs under controlled training conditions.

## Files

| File | Contents |
|---|---|
| [`Program1_GD_Optimizers_Regularization_ResMLP.ipynb`](Program1_GD_Optimizers_Regularization_ResMLP.ipynb) | The full program, executed, with all outputs and plots |

## What the notebook covers

**Part A — Batch vs. stochastic vs. mini-batch GD** (NumPy, from scratch)
- Linear regression on a 200-point noisy dataset; one `gradient_descent(batch_size, lr, epochs)` function covers all three variants
- Loss vs. epochs, loss vs. number of updates, trajectories on the loss-surface contour plot
- Gradient noise vs. batch size (≈ 1/√m)

**Fashion-MNIST subset** — loaded from the Hugging Face Hub (`zalando-datasets/fashion_mnist`):
class-balanced 6 000 train / 2 000 validation images, full 10 000-image test set

**Part B — Optimizers × learning-rate schedules**
- SGD (baseline), SGD + Momentum, Nesterov (momentum-based) and RMSprop, Adam (adaptive)
- Each with constant, step-decay and cosine-annealing learning rates — 15 runs from identical initial weights
- Training-loss / validation-accuracy curves, summary table, test-accuracy heat-map

**Part C — Overfitting and regularization**
- Over-parameterised MLP (784-512-512-10) trained 60 epochs to show overfitting (train → 100 %, validation loss rising)
- Dropout (0.2, 0.5), L2 (1e-4, 1e-3), data augmentation (random rotation / shift / flip), and all combined
- Early stopping (patience 5, best weights restored); comparison table and test-accuracy chart

**Part D — Plain vs. residual MLPs**
- Identical architectures, parameters and initial weights; the only difference is the skip connection
- Depths 2, 6, 12, 24 hidden layers × 3 seeds; gradient norms at initialization, training curves, accuracy vs. depth

## Run

```bash
pip install -r ../requirements.txt
jupyter nbconvert --to notebook --execute --inplace Program1_GD_Optimizers_Regularization_ResMLP.ipynb
```

Runs on CPU in a few minutes.
