# BenchQC

quantumBENCH is a Python package for benchmarking quantum computers and their performance of the Variational Quantum Eigensolver (VQE) on chemical systems. This package aims to contribute to materials discovery and design by providing tools for quantum chemistry simulations.

## Features

- Generate qubit operators from molecular data
- Compute energies using VQE and classical solvers
- Supports various quantum devices and optimizers

## Installation

You can install the package using `pip`. First, clone the repository:

```bash
git clone https://github.com/niapollard/quantumBENCH.git
cd quantumBENCH
```

Then install the package:

```bash
pip install .
```
## Examples
| Notebooks | Google&nbsp;Colab | Descriptions |
| --- | --- | --- |
| [Figure 2_Cube File Generation](https://colab.research.google.com/github/niapollard/Benchmarking-Quantum-Algorithms-for-Materials-Discovery-and-Design/blob/main/Cube_File_Generation.ipynb) | [![Open in Google Colab]](https://colab.research.google.com/github/niapollard/Benchmarking-Quantum-Algorithms-for-Materials-Discovery-and-Design/blob/main/Cube_File_Generation.ipynb)] | Description of Notebook 1. |



## Usage

Here's an example of how to use the package:

```python
from quantum_vqe import get_qubit_op, get_energy
from qiskit.algorithms.optimizers import SLSQP
from qiskit.providers.aer import AerSimulator
from qiskit_nature.drivers import Molecule
from qiskit_nature.mappers.second_quantization import JordanWignerMapper

# Define a molecule
molecule = Molecule(geometry=[['H', [0., 0., 0.]], ['H', [0., 0., 0.735]]], multiplicity=1, charge=0)

# Get the qubit operator
res1 = get_qubit_op(molecule)

# Define an optimizer and quantum device
optimizer = SLSQP(maxiter=1000)
device = Aer.get_backend('statevector_simulator')

# Compute the energy
res = get_energy(optimizer, device, res1['qubit_op'])

print("Computed Energy:", res['eigenvalue'])
```

## API Reference

### `get_qubit_op`

```python
get_qubit_op(molecule, basis='sto3g', functional='lda', method=MethodType.RKS, driver_type=ElectronicStructureDriverType.PYSCF, mapper=JordanWignerMapper())
```

- `molecule`: The molecule to be simulated.
- `basis`: The basis set to be used (default: 'sto3g').
- `functional`: The functional to be used (default: 'lda').
- `method`: The method to be used (default: `MethodType.RKS`).
- `driver_type`: The electronic structure driver type (default: `ElectronicStructureDriverType.PYSCF`).
- `mapper`: The mapper to convert to qubit operator (default: `JordanWignerMapper`).

Returns a dictionary with the keys:
- `qubit_op`: The qubit operator.
- `converter`: The qubit converter.
- `problem_reduced`: The reduced electronic structure problem.
- `numpy_solver`: The numpy solver.

### `get_energy`

```python
get_energy(optimizer, device, qubit_op, seed=42, reps=1)
```

- `optimizer`: The optimizer to be used.
- `device`: The quantum device to be used.
- `qubit_op`: The qubit operator.
- `seed`: The seed for the random number generator (default: 42).
- `reps`: The number of repetitions (default: 1).

Returns a dictionary with the keys:
- `eigenvalue`: The computed eigenvalue.
- `vqe`: The VQE instance.
- `qi`: The quantum instance.

## Contributing

Contributions are welcome! Please submit a pull request or open an issue to discuss changes.

## License

This project is licensed under the NIST License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- This package uses [Qiskit](https://qiskit.org/), an open-source SDK for working with quantum computers.

## Contact

For more information, please contact [Nia Pollard](mailto:nia.rodney-pollard@nist.gov).
```

Replace `https://github.com/yourusername/quantum_vqe.git` and `your.email@example.com` with your actual GitHub repository URL and email address. This `README.md` provides a comprehensive guide to installing, using, and contributing to your package.
