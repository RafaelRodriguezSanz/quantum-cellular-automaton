# Quantum 2D Cellular Automaton (QCA)
![Python](https://img.shields.io/badge/python-3.10+-blue?logo=python&logoColor=white)
![Qiskit](https://img.shields.io/badge/qiskit-0.50+-purple?logo=qiskit&logoColor=white)
![License](https://img.shields.io/badge/license-MIT-green)

## 🔬 Description

I explore the **fusion of two technologies**: cellular automata and quantum computing.  
In this project, I implemented a **2D Quantum Cellular Automaton (QCA)**, simulating the evolution of a qubit grid with local unitary rules.  
I visualize the evolution through 2D animations that show the **propagation of probabilities** in each qubit over time.

This is a **research-oriented project**: I wanted to experiment with how classical cellular automata patterns behave when translated into the quantum domain.

![simulation](https://github.com/user-attachments/assets/1b766a03-0b4b-4ab3-bcb1-fd610a202cc7)

---

## ⚙️ Features

- Configurable 2D grid (`L x L` qubits)  
- Local unitary rules applied between each cell and its neighbors  
- Configurable initial state  
- Temporal evolution with interactive animation in Jupyter Notebook  
- Visualization of P(|1⟩) probabilities per qubit  

---

## 🏛 Theoretical Background

### Wavefunction Evolution

Consider a 2D grid of $$(L \times L)$$ qubits. Let the **total Hilbert space** be $$(\mathcal{H} = (\mathbb{C}^2)^{\otimes N})$$ with $$(N = L^2)$$ qubits.

The **state of the system at time (t)** is described by the wavefunction:

$$|\psi(t)\rangle = \sum_{b \in {0,1}^N} \alpha_b(t) , |b\rangle$$

where $$(|b\rangle = |b_0 b_1 \dots b_{N-1}\rangle)$$ are computational basis states, and $$(\alpha_b(t) \in \mathbb{C})$$ satisfy

$$\sum_{b} |\alpha_b(t)|^2 = 1$$

---

### Local Unitary Evolution

Each qubit interacts with its neighbors via a **local unitary gate (U)**. Let the unitary layer at time step \(t\) be:

$$
U_{\text{layer}}(t) = \prod_{i,j} U_{(i,j),(i',j')}
$$

where \((i', j') \in \text{neighbors}(i,j)\).

The **discrete-time evolution** is then:

$$
|\psi(t+1)\rangle = U_{\text{layer}}(t) |\psi(t)\rangle
$$

Starting from an initial state \( |\psi(0)\rangle \), typically localized excitations or superpositions:

$$
|\psi(0)\rangle = \bigotimes_{i,j} |q_{i,j}\rangle
$$

the state evolves under repeated application of the local unitary layers.

---

### Observables: Probability of |1⟩

The probability of finding qubit \(q_k\) in state \(|1\rangle\) is obtained from the wavefunction:

$$
P(q_k = 1; t) = \sum_{\substack{b \in \{0,1\}^N \\ b_k = 1}} |\alpha_b(t)|^2
$$

In the 2D QCA visualization, each frame corresponds to the matrix of probabilities:

$$
\mathbf{P}(t) =
\begin{bmatrix}
P(q_{0,0}=1;t) & \cdots & P(q_{0,L-1}=1;t) \\
\vdots & \ddots & \vdots \\
P(q_{L-1,0}=1;t) & \cdots & P(q_{L-1,L-1}=1;t)
\end{bmatrix}
$$

This matrix evolves as you apply the local unitary layers over time.

---

## 📚 References

- **Watrous, J. (1995).** *On one-dimensional quantum cellular automata.* In *Proceedings of the 36th Annual Symposium on Foundations of Computer Science (SFCS)*, pp. 528–537. [Link](https://emoutot.perso.math.cnrs.fr/static/etudes/M2/quantum_slides.pdf)

- **Schumacher, B. & Werner, R. F. (2004).** *Reversible quantum cellular automata.* arXiv:quant-ph/0405174. [Link](https://arxiv.org/abs/quant-ph/0405174)

- **Arrighi, P. (2019).** *An overview of Quantum Cellular Automata.* arXiv:1904.12956v2. [Link](https://arxiv.org/abs/1904.12956)
