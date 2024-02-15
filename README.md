# XXZ_SpinChain

This repo simulates the XXZ Heisenberg spin chain using the QuTiP and Qiskit Python packages. 

## Files
- qutip.ipynb: the Von Neumann entropy and quantum Fisher information of an XXZ spin chain are calculated over time. The relationship between these two properties are investigated.
- qiskit.ipynb: the Von Neumann entropy of an XX spin chain is calculated and compared to the results calculated by QuTiP

## Packages Used
- qutip
- qiskit
- numpy
- matplotlib
- tqdm

## Theoretical Background

Heisenberg spin chains are 1D spin lattices with coupling interaction, $J$. They are the simplest formulation of the quantum Heisenberg model. The quantum Heisenberg model is similar to the classical Ising model, however, the Heisenberg model exploits Pauli spin-1/2 operators acting on acomposite space (ℂ2)⊗𝑁. The XXZ spin chain is defined with the following Hamiltonian:

```math
H = -J\sum_{j=1}^{N-1} \left( \sigma_j^x \sigma_{j+1}^x + \sigma_j^y \sigma_{j+1}^y \right) + U\sum_{j=1}^{N-1} \sigma_j^z \sigma_{j+1}^z
```

where $\sigma_{j}^{\alpha}$ are the Pauli operators acting on the jth qubit as follows:
```math
I^{\otimes j} \otimes \sigma^{\alpha} \otimes I^{\otimes (N-j)}
```

In this repo, we will calculate the Von Neumann entropy, $S_{VN}$. The Von Neumann entropy is a bipartite entanglement of a state. For a system composed of sub-systems, $A$ and $B$, the Von Neumann entropy of a subsystem, $A$ as:
```math
S_{A} = -tr(\rho_{A} \ln(\rho_{A}))
```
Let $B$ represent the rest of the total system. For a pure state, $S_{A} = S_{B}$ and $\rho_{A} = -tr_{B}(|\Psi \rangle \langle \Psi |)$. We will also introduce the Quantum Fisher Information which describes the susceptibility of a system to some small perturbation. It is a meaasurement of the amount of information that can be obtained from a quantum state. The higher the QFI, the more accurate the measurement of a specific variable can be taken. It also represents a measure of multipartite entanglement. For a pure state, the QFI is a measure of the variance of an operator. For the spin chain, the quantum Fisher information can be written as follows:

```math
F_Q(t) = \sum_{j,k} \ s_js_k \langle \psi(t) | \sigma_j^z \sigma_{j+1}^z | \psi(t) \rangle - (\sum_{j} s_j \langle \psi(t) | \sigma_j^z  | \psi(t) \rangle)^2
```

where $s_j$ depends on the two subsystems being analysed. $s_j\ = +1$ for subsystem A and $-1$ for subsystem B. The relationship between the $S_{VN}$ and $F_{Q}$ is established as [1]:
```math
S_{VN}(t) \approx \frac{5}{32} F_{Q}(t)
```

## References

[1] A. Smith, M. S. Kim, F. Pollmann, and J. Knolle, “Simulating quantum many-body dynamics on a current digital quantum computer,” npj Quantum Information, vol. 5, no. 1, Nov. 2019, doi: https://doi.org/10.1038/s41534-019-0217-0.





