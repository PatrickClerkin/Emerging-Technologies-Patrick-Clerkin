# Emerging Technologies 
This repository contains my submission for the **Emerging Technologies**
module assessment. The notebook
[`problems.ipynb`](problems.ipynb) works through five problems exploring
the contrast between **classical and quantum algorithms**, building up to
a Qiskit implementation of the Deutsch–Jozsa algorithm for four-input
Boolean functions.

## Quick start

```bash
# Clone the repository
git clone https://github.com/PatrickClerkin/Emerging-Technologies-Patrick-Clerkin.git
cd Emerging-Technologies-Patrick-Clerkin

# Install dependencies (Python 3.10+ required)
pip install -r requirements.txt

# Launch the notebook
jupyter notebook problems.ipynb
```

Then in the notebook menu choose **Kernel → Restart & Run All** to
reproduce every cell in order.

## Requirements

- **Python 3.10 or later** (the notebook uses PEP 604 union types like
  `int | None` and `int.bit_count()`).
- The packages listed in [`requirements.txt`](requirements.txt). The key
  ones for this notebook are `qiskit`, `qiskit-aer`, `qiskit[visualization]`,
  `numpy`, and `matplotlib`; the rest of the file lists supporting
  packages permitted by the assessment brief.

## What's in the notebook

The notebook follows a single narrative arc from the *space of inputs*
to the *exponential quantum advantage*. Each problem builds directly on
the previous one.

| # | Problem | Topic |
|---|---------|-------|
| 1 | Generating Random Boolean Functions | Sampling uniformly from the four-input constant-or-balanced promise set (12,872 functions in total). |
| 2 | Classical Testing for Function Type | Adversary proof of the $2^{n-1}+1 = 9$ classical worst-case query bound, with an early-terminating implementation. |
| 3 | Quantum Oracles | XOR-oracle construction in Qiskit for the four single-input Boolean functions. |
| 4 | Deutsch's Algorithm with Qiskit | The original 1985 single-input algorithm, with state-by-state derivation and verification on all four oracles. |
| 5 | Scaling to the Deutsch–Jozsa Algorithm | The $n$-input generalisation, demonstrated on both constant functions and two balanced functions, exhibiting the exponential separation between deterministic classical and exact quantum query complexity. |

Each problem includes mathematical analysis, an implementation, sanity
tests, a demonstration, and a brief summary connecting to the next
problem.

## Repository structure

```
.
├── problems.ipynb        # The main submission — all five problems
├── README.md             # This file
├── requirements.txt      # Python dependencies (per assessment brief)
├── .gitignore            # Excludes Jupyter checkpoints, __pycache__, etc.
└── img/                  # Circuit drawings and result histograms
                          # produced by the notebook
```

There is no `data/` folder for this assessment — the problems are
self-contained and require no external datasets. Image files in `img/`
are produced automatically when the notebook is run; they are committed
to the repository so the work is browsable without re-running.

## Reproducibility

The notebook is fully reproducible:

- Every `random.Random` instance is explicitly seeded.
- Quantum circuits are run on `qiskit_aer.AerSimulator`, which is
  noiseless by default — measurements are exactly deterministic, not
  probabilistic.
- All assertions in the notebook (sanity checks, distributional
  agreement with theoretical bounds, etc.) are written to pass on a
  clean run.

A clean run on Python 3.12 with the package versions in `requirements.txt`
takes well under a minute on a standard laptop.

## References

Full per-problem reference lists are included inside the notebook. The
primary sources informing the work are:

- Deutsch, D. (1985). Quantum theory, the Church–Turing principle and
  the universal quantum computer. *Proceedings of the Royal Society A*,
  400(1818), 97–117.
- Deutsch, D., & Jozsa, R. (1992). Rapid solution of problems by
  quantum computation. *Proceedings of the Royal Society A*, 439(1907),
  553–558.
- Cleve, R., Ekert, A., Macchiavello, C., & Mosca, M. (1998). Quantum
  algorithms revisited. *Proceedings of the Royal Society A*, 454(1969),
  339–354.
- Nielsen, M. A., & Chuang, I. L. (2010). *Quantum Computation and
  Quantum Information* (10th anniversary ed.). Cambridge University
  Press.
- IBM Quantum Learning. *Deutsch–Jozsa algorithm* and *Deutsch's
  algorithm.* https://quantum.cloud.ibm.com/learning

## Author

Patrick Clerkin