# System Identification on Industrial Manipulators

This repository contains code and experiments for **data-driven system identification** on industrial robot manipulators, focusing on:

- A heavy-duty **KUKA KR300 R2500 ultra SE** industrial arm.
- A 7-DoF **Baxter** robot arm.

The main goal is to benchmark classical and learning-based identification methods on high-quality open datasets and to provide a reproducible baseline for future research on model-based and learning-based control.

---

## Datasets

### 1. KUKA KR300 R2500 ultra SE – Industrial Robot Identification Benchmark

We use the public benchmark dataset released by Weigand *et al.* for a 6-DoF KUKA KR300 R2500 ultra SE industrial robot. The dataset contains joint positions, velocities and torques over rich excitation trajectories and is specifically designed for nonlinear system identification. 

- **Dataset homepage** (Nonlinear Benchmark):  
  https://www.nonlinearbenchmark.org/benchmarks/industrial-robot   

- **Benchmark description paper (PDF)**:  
  https://kluedo.ub.rptu.de/frontdoor/deliver/index/docId/6731/file/Robot_Identification_Benchmark_Description.pdf   

- **DOI / data landing page**:  
  https://doi.org/10.26204/DATA/5   

This dataset exhibits strong nonlinearities (backlash, pose-dependent inertia, nonlinear friction, etc.), which makes it a challenging and realistic benchmark for identification and model-based control.

---

### 2. Baxter 7-DoF Arm – Inverse Dynamics Dataset

For the Baxter robot, we use a publicly available dataset of joint angles, velocities, and torques collected along diverse trajectories, originally used to train recurrent neural networks for inverse dynamics learning.   

- **Dataset on Zenodo** (recommended canonical link):  
  https://zenodo.org/records/17035193   

- **Companion GitHub repository**:  
  https://github.com/EduardoRosLab/Baxter_Dynamic_Model   

The Baxter dataset is particularly suited to compare classical rigid-body models vs. data-driven models (RNNs, BRNNs, etc.) for inverse dynamics.

---

## Repository structure

Planned layout:

- `sysid_kuka_baxter_research.ipynb`  
  Jupyter notebook that:
  - Downloads / loads the KUKA and Baxter datasets.
  - Performs basic preprocessing (normalization, train/validation splits).
  - Fits baseline models (e.g., linear regression, NARX-style models, simple RNNs).
  - Compares prediction errors and discusses identification quality.

- (Optional, future)
  - `kuka/` – helper scripts and configs specific to the KUKA benchmark.
  - `baxter/` – helper scripts and configs for the Baxter dataset.
  - `figures/` – plots of trajectories, residuals, and identification metrics.

---

## Getting started

### Requirements

- Python ≥ 3.9  
- Jupyter / JupyterLab  
- Common scientific packages:
  - `numpy`, `scipy`, `pandas`, `matplotlib`, `seaborn`
  - (optional) `pytorch` / `tensorflow` for neural network models

Install a minimal environment (example using `pip`):

```bash
python -m venv .venv
source .venv/bin/activate
pip install numpy scipy pandas matplotlib seaborn jupyter
# plus any extra libraries you need inside the notebook (e.g. torch)
````

### Running the notebook

```bash
cd /path/to/System-Identification-on-Industrial-Manipulators
source .venv/bin/activate    # if you created a venv
jupyter lab                   # or: jupyter notebook
```

Then open:

* `sysid_kuka_baxter_research.ipynb`

and run the cells to reproduce the experiments.

---

## References

* J. Weigand, J. Götz, J. Ulmen, M. Ruskowski,
  **“Dataset and Baseline for an Industrial Robot Identification Benchmark”**,
  Data-Centric Engineering, 2023.

* Baxter inverse dynamics dataset and codebase:
  **Baxter Dynamic Model**, EduardoRosLab, GitHub + Zenodo.

This repository is intended as a research starting point for system identification on real industrial manipulators. Contributions and pull requests with additional models or datasets are welcome.

````

> Don’t rerun `git init` or `git remote add` – you already did that.

Save and exit (`Ctrl+X`, then `Y`, then `Enter` in `nano`).

---

## 2. Add the notebook to this repo

Your notebook is currently in `~/Downloads`. Move it into the new repo:

```bash
cd ~/System-Identification-on-Industrial-Manipulators   # or whatever path you used

mv ~/Downloads/sysid_kuka_baxter_research.ipynb .
# or, if you prefer a subfolder:
# mkdir -p notebooks
# mv ~/Downloads/sysid_kuka_baxter_research.ipynb notebooks/
````
