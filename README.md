# HALO: A Tiered Evidence Program for a Holographic Quantum Artificial-Life Architecture

**Author:** Balagopal P (balagopal.p44@gmail.com)
**Affiliation:** Independent Researcher
**Date:** February 2026

## License

- **Paper** (`paper.pdf`, `plain_language_summary.pdf`, `plain_language_summary.html`, `latex_source/`): [CC-BY-4.0](https://creativecommons.org/licenses/by/4.0/)
- **Code** (`code/`): [MIT License](https://opensource.org/licenses/MIT)
- **Data** (`data/`): [CC0 1.0 Public Domain](https://creativecommons.org/publicdomain/zero/1.0/)

See `LICENSE` for full terms.

## Citation

Please cite this record via the Zenodo DOI:
**https://doi.org/10.5281/zenodo.18769321**
A machine-readable `CITATION.cff` is included for reference managers.

---

## Contents

### `paper.pdf`
The full 27-page manuscript. Start here.

### `plain_language_summary.pdf` / `plain_language_summary.html`
A plain-language explainer of the paper — no physics degree required.
Open `plain_language_summary.pdf` for the best reading experience (works everywhere).
The `.html` source is also included for browser viewing.

### `latex_source/`
Complete LaTeX source for reproducible compilation.

| File | Purpose |
|---|---|
| `main.tex` | Main manuscript source |
| `quantumarticle.cls` | Compatibility shim for the Quantum journal document class |
| `halo_circuit.pdf` | Architecture figure (Fig. 1) |
| `fig_qubit_count.png` | Scaling figure — qubit count (Fig. 2a) |
| `fig_two_qubit_depth.png` | Scaling figure — two-qubit depth (Fig. 2b) |
| `fig_gate_count.png` | Scaling figure — gate count (Fig. 2c) |
| `fig_logical_fidelity.png` | Scaling figure — logical fidelity (Fig. 2d) |
| `fig_compression_multiexcitation.png` | k-excitation compression ratio figure (C2) |
| `fig_security_trend.png` | Security trend with confidence intervals (C3) |
| `fig_cross_sector_compression.png` | Multi-sector direct-sum isometry compression ratios (C4, §5.4) |
| `fig_sector_leakage.png` | Sector leakage vs perturbation strength (C4, App. D) |
| `fig_quantum_evolution.png` | Fully quantum evolution: fit probability and entropy (C5, §5.5) |

To recompile: run `pdflatex main.tex` twice from the `latex_source/` directory.
Requires TeX Live 2020+ with standard packages (amsmath, amssymb, amsthm,
hyperref, booktabs, subcaption, cleveref, enumitem, doi, microtype, xcolor).

### `code/`
Companion simulation code.

| File | Purpose |
|---|---|
| `halo_simulation.py` | Five-qubit HALO toy circuit — C0 validation (clock, DFS, reversibility) |
| `scaling_benchmark.py` | C1 — Lattice-Trotter proxy: one-hot (2n qubits) vs binary (⌈log₂n⌉+1 qubits) qubit-count scaling |
| `run_extended_experiments.py` | C2 + C3 extended experiments (k-excitation compression + security trend) |
| `cross_sector_compression.py` | C4 — Multi-sector direct-sum isometry and sector leakage experiment (Qiskit circuit + numpy fallback) |
| `quantum_evolution.py` | C5 — Fully quantum multi-generation evolution via Grover amplitude amplification (Qiskit circuit + numpy fallback) |
| `requirements.txt` | Python dependencies (`qiskit`, `qiskit-aer`, `numpy`, `matplotlib`) |
| `experiments/__init__.py` | Package init for the experiments module |
| `experiments/backends.py` | Backend selection helper (Aer → BasicSimulator fallback) |

**Reproduce all results:**

```bash
# Step 1: Enter the code directory and install dependencies
cd code
python3 -m pip install -r requirements.txt

# Step 2: C0 toy validation
python3 halo_simulation.py
# Expected: three tests, all PASS

# Step 3: C1 — qubit-count scaling benchmark
python3 scaling_benchmark.py
# Outputs: data/scaling_results.jsonl, fig_qubit_count.png, fig_two_qubit_depth.png

# Step 4: C2 + C3 extended experiments
python3 run_extended_experiments.py
# Outputs: data/compression_results.jsonl, data/security_results.jsonl, two figures

# Step 5: C4 — cross-sector compression and leakage
# (Qiskit circuit; falls back to numpy if Qiskit is not installed)
python3 cross_sector_compression.py
# Outputs: data/cross_sector_results.jsonl, fig_cross_sector_compression.png, fig_sector_leakage.png

# Step 6: C5 — fully quantum multi-generation evolution via Grover amplification
# (Qiskit circuit; falls back to numpy if Qiskit is not installed)
python3 quantum_evolution.py
# Outputs: data/evolution_results.jsonl, fig_quantum_evolution.png
```

> **Note:** `halo_simulation.py` imports from the `experiments/` sub-package.
> All steps should be run from within the `code/` directory.
> Steps 5 and 6 support numpy-only fallback mode (no Qiskit needed for numerical results;
> circuit depth metrics require Qiskit).

### `data/`
Raw simulation results from which all figures and tables in the paper derive.
Each file is newline-delimited JSON (JSONL), one record per simulation run.

| File | Claim | Description |
|---|---|---|
| `scaling_results.jsonl` | C1 | Lattice-Trotter proxy scalability benchmark |
| `compression_results.jsonl` | C2 | k-excitation isometry metrics (k=1,2,3; N=4,8,16,32) |
| `cross_sector_results.jsonl` | C4 | Multi-sector isometry (sectors {1,2},{0,1,2},{1,2,3}; N=4,6) and sector leakage experiment (N=4, k=2 center) |
| `evolution_results.jsonl` | C5 | Fully quantum Grover-based evolution (P=8 agents, G=5 generations) |
| `security_results.jsonl` | C3 | Heuristic attacker success rates (n=6–18, 100 trials) |

---

## Abstract

HALO (Holographic Artificial-Life with Observational confinement) is a
quantum-computing architecture integrating the Page–Wootters mechanism,
decoherence-free subspace encoding, subspace-isometric holographic compression,
and complexity-theoretic fitness encryption. Using a six-rung claim-ladder
methodology, evidence is reported at six levels: toy-scale composability (C0),
sub-linear qubit-count scaling in a matched-fidelity proxy benchmark (C1),
explicit isometric compression across k-excitation subspaces (k=1,2,3) (C2),
a statistically significant security hardening trend under a bounded heuristic
attacker (Mann–Kendall p=0.0027) (C3), direct-sum cross-sector isometries with
leakage characterisation (C4), and a fully quantum multi-generation evolution
loop demonstrating Grover amplitude amplification with no intermediate
measurement (C5). Hardware-scale validation and universal compression are
explicitly deferred to C6.

---

## How to cite

If you use this work, please cite the Zenodo record directly (DOI assigned
via https://doi.org/10.5281/zenodo.18769321. A `CITATION.cff` file is included
for automated citation extraction by GitHub, Zotero, and similar tools.

---

## Changelog

- **v1.0.0 (2026-03-01):** Initial public release. Six-rung evidence ladder (C0–C5) with full simulation code, raw data, and reproduction scripts. Archived on Zenodo: https://doi.org/10.5281/zenodo.18769321
