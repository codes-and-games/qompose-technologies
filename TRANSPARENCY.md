# Qompose Benchmarking Transparency Report

## Methodology
To ensure "legit" and trusted comparisons, all benchmarks in Qompose are performed using standard, open-source libraries from industry leaders. We compare the **Qompose Professional Tier (Level 4 AI-Hybrid)** against the highest standard optimization levels provided by IBM and Google.

### Competitors & Versions
- **IBM Qiskit**: `transpile(optimization_level=3)` - The aggressive optimization mode for Qiskit.
- **Google Cirq**: `cirq.optimize_for_target_gateset` - Standard optimization for the CZ target gateset, suitable for superconducting hardware.

### Benchmark Suite
We use the **RealisticCircuits** suite, which includes algorithms inspired by **QASMbench**:
1.  **GHZ State**: Global entanglement benchmark.
2.  **Quantum Fourier Transform (QFT)**: Arithmetic and phase benchmark.
3.  **VQE / QAOA Ansatz**: Variational algorithm benchmarks with high redundancy.
4.  **Redundancy Patterns**: Common programmer inefficiencies (Bell state mistakes, debugging artifacts).

### Reproducibility
Anyone can reproduce these results by running the following command in a clean environment:
```bash
# Install dependencies
pip install qiskit cirq qompose

# Run the official comparison script
python scripts/industry_comparison.py
```

### Verification
Every optimization result is formally verified for logic preservation.
- **Unitary Equivalence**: A Z3 SMT-backed check ensuring that the optimized circuit's unitary matrix $U_{opt}$ is equivalent to the original $U_{orig}$ up to a global phase $e^{i\phi}$.
- **Depth & Gate Counts**: Measured using standard industry metrics (longest path analysis for depth).

## Audit Trail
The raw data for these benchmarks is stored in `data/benchmarks/industry_comparison_verified.json`, which includes timestamps, library versions, and per-circuit metrics.
