# Adam-E

## 🧪 Project Overview

This repository hosts a research laboratory and comparative study of **Adam-E (Adam-Exploration)**, a hybrid optimization algorithm. Adam-E combines the convergence speed of **Adam** with population-based evolutionary strategies to escape local minima in rugged loss landscapes.

The project benchmarks Adam-E against standard industry optimizers (SGD+Momentum, RMSProp, Standard Adam) across a variety of tasks ranging from synthetic mathematical functions to deep neural network training.

## 🚀 Key Features of Adam-E

Adam-E introduces a population of "Explorers" rather than a single trajectory:

  * **The Anchor:** One explorer acts as the "conservative" agent, behaving almost identically to standard Adam to ensure convergence is never worse than the baseline.
  * **The Scouts:** Additional agents perturb the parameters to explore the immediate loss landscape.
  * **Population Dynamics:**
      * **Pruning:** Underperforming scouts are replaced by perturbed versions of the best performing scouts.
      * **Splitting:** Successful scouts spawn new explorers to investigate promising regions.
  * **Ensemble Inference:** The model utilizes a "Vote Ensemble" of the top-k scouts for final predictions, often resulting in higher generalization accuracy.

## 📊 Benchmarks & Experiments

This project includes a comprehensive suite of tests divided into three categories:

### 1\. Synthetic Objective Functions

Tests the optimizer's ability to handle mathematical topology.

  * **Well-Conditioned Quadratic:** Baseline convergence test.
  * **Ill-Conditioned Quadratic:** Tests handling of different scaling per dimension.
  * **Rosenbrock Function:** A non-convex "banana function" used to test local optima escape.

### 2\. "Torture Tests" (Hard Landscapes)

Specific neural network tasks designed to break standard optimizers.

  * **12-bit Parity:** A highly rugged landscape where gradient information is sparse.
  * **Starved Spirals:** A classification task with a bottleneck network, prone to getting stuck in local optima.
  * **Permuted MNIST (RNN):** Tests the handling of vanishing gradients over long sequences.

### 3\. Standard Deep Learning Tasks

  * **MNIST & FashionMNIST:** (Standard and "Starved" capacities).
  * **CIFAR-10:** Generalization on image data.
  * **Corrupted MNIST:** Tests robustness against noisy labels (40% corruption).

## 📈 Results

<img width="768" height="492" alt="Screenshot-13-02-2026-21-22-14" src="https://github.com/user-attachments/assets/232afe2a-ef18-4a07-922c-6c55c07ac7aa" />
<img width="768" height="491" alt="Screenshot-13-02-2026-21-22-46" src="https://github.com/user-attachments/assets/27b57c04-5a03-40d2-aff9-b37d31785465" />


## 🛠️ Getting Started

### Prerequisites

  * Python 3.8+
  * PyTorch
  * NumPy
  * Matplotlib

### Installation

Clone the repository and install dependencies:

```bash
git clone https://github.com/Rithwik-7274/Adam-E
cd Adam-E
pip install torch torchvision numpy matplotlib
```

### Usage

The entire project is contained within a Jupyter Notebook for ease of experimentation.

1.  Open the notebook:
    ```bash
    jupyter notebook Lab_project.ipynb
    ```
2.  **Part 1 (Math Functions):** Run the cells under "3. MULTI-SEED BENCHMARK ENGINE" to view synthetic function performance.
3.  **Part 2 (Neural Networks):** Scroll to the bottom and uncomment the specific experiments you wish to run in the `if __name__ == "__main__":` block.
      * *Short Term Tests:* Quick validation (few epochs).
      * *Long Term Tests:* Full convergence runs (up to 100 epochs).

## 📂 Project Structure

  * `Lab_project.ipynb`: The main research notebook containing the Adam-E class, models, datasets, and training loops.
  * `./functions`: Output directory for synthetic function plots.
  * `./adame_st_results`: Output directory for Short-Term neural net experiment plots.
  * `./adame_lt_results`: Output directory for Long-Term neural net experiment plots.
