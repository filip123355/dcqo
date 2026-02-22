# PennyLane study (DCQO)

Small experiments with PennyLane: adiabatic/QAOA-like circuits, optional counter-diabatic (CD) term, training + running “shots”, and plotting results.

## Setup
```bash
# (recommended) create env
conda create -n pennylane-study python=3.13 -y
conda activate pennylane-study

pip install pennylane pennylane-qiskit qiskit torch matplotlib tqdm python-dotenv
```

## Run
Open the notebook:
```bash
code notebooks/dcqo.ipynb
```

Typical flow inside the notebook:
1. `optimize(...)` (saves `losses/` + `parameters/`)
2. `run_circuit(...)` (saves `experiments/experiments.pkl`)
3. `plot_results(...)` (boxplot comparison CD vs no-CD)

## IBM hardware (optional)
Set token:
```bash
export IBMQ_TOKEN="your_token_here"
```

With newer Qiskit, prefer the modern remote device (not legacy `qiskit.ibmq`):
- `qml.device("qiskit.remote", backend="...", provider=...)`

## Output folders
Each run directory typically contains:
- `losses/losses.pkl`
- `parameters/{gamma,beta,alpha}.pth`
- `experiments/experiments.pkl`
- `plots/*.png`