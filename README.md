# Deutsch-Jozsa Algorithm: Experimental Proof of Quantum Parallelism
## Executive Summary
This project provides a rigorous implementation of the Deutsch-Jozsa Algorithm, the first quantum protocol to demonstrate a deterministic exponential speedup over classical computation. While the problem itself is of limited practical use, its theoretical significance is profound: it serves as the primary evidence that Quantum Interference and Superposition can solve specific black-box problems with a complexity gap that is fundamentally inaccessible to classical Turing machines.
## Mathematical Foundation
Consider a boolean function $f: \{0,1\}^n \rightarrow \{0,1\}$. We are guaranteed that $f$ is either constant (outputs the same value for all inputs) or balanced (outputs $0$ for exactly half of the input space and $1$ for the other half).
### The Complexity Gap
**Classical Complexity:** To guarantee a correct answer, a deterministic classical algorithm must query the oracle at least $2^{n-1} + 1$ times in the worst-case scenario. This represents exponential growth $O(2^n)$.
**Quantum Complexity:** Utilizing the Deutsch-Jozsa protocol, we determine the function's nature with a single query $O(1)$, leveraging phase kickback and constructive/destructive interference.
## Circuit Architecture
The implementation follows the standard quantum circuit model:
1. Initialization: Preparing $n$ input qubits in state $|0\rangle^{\otimes n}$ and one ancilla qubit in $|1\rangle$.
2. Superposition: Applying Hadamard gates $H^{\otimes n+1}$ to create a global superposition.
3. Oracle Application ($U_f$): Mapping $|x\rangle|y\rangle$ to $|x\rangle|y \oplus f(x)\rangle$.
4. Interference: Re-applying Hadamard gates to the input register to revert the phase information into measurable state information.
5. Measurement: Collapsing the wave function to observe the result.
## Tech Stack & Reproducibility
This research is implemented using the following tools:
* Language: Python 3.11+
* Framework: IBM Qiskit
* Simulator: Qiskit Aer (High-performance statevector simulator)
* Visualization: Matplotlib
### Installation
To replicate the experiment, ensure your environment meets the requirements:
```bash
pip install qiskit
```
## Experimental Results
The results included in the Jupyter Notebook demonstrate:
* Case A (Constant): Measurement yields the $|0\rangle^{\otimes n}$ state with 100% probability.
* Case B (Balanced): Measurement yields any state other than $|0\rangle^{\otimes n}$ with 100% probability.
These empirical results validate the theoretical predictions of quantum computational advantage.
## Author
Developed as part of a deep-dive into Quantum Information Theory and algorithmic complexity.
