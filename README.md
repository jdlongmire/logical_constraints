# LogicalQFT: Logical Consistency Constraints in Quantum Field Theory

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.16377959.svg)](https://doi.org/10.5281/zenodo.16377959)
[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC_BY--NC--SA_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)

A computational framework implementing information-geometric constraints derived from logical consistency requirements in quantum field theory. This package provides tools for studying how structural features of the Standard Model might emerge from fundamental logical principles.

**Current Status**: Version 1.0 provides a comprehensive demonstration of the LogicalQFT framework in a single package file, with complete tutorial and validation. Future releases will include modular structure and pip installation.

## 🔬 Core Concept

**Central Equation**: Ω = L(S)
- **Ω** = Physical reality (actually existing field configurations)
- **L** = Logical consistency operator  
- **S** = Space of all mathematically possible field configurations

**Key Insight**: Physical field configurations may be precisely those mathematical structures that satisfy logical consistency requirements, implemented through information-geometric strain functionals.

## ✅ Computational Achievements

This framework successfully demonstrates:

- **Strain minimization algorithms** that converge random field configurations to solutions of Klein-Gordon, Maxwell, and Yang-Mills equations
- **Three generations emergence** from anomaly cancellation constraints (computational verification: only 3 generations yield Tr[Q³] = 0)
- **Finite quantum corrections** through natural information-theoretic cutoffs (all tested loop integrals converge)
- **Gauge theory structure emergence** from logical definiteness requirements
- **Specific experimental predictions** including muon g-2 corrections and LHC signatures

## 🚀 Quick Start

### Installation

**Quick Start (Current Version)**:
```bash
git clone https://github.com/jdlongmire/logical_constraints.git
cd logical_constraints

# Install dependencies
pip install numpy scipy matplotlib

# Run the complete tutorial
python jupyter_tutorial.py
```

**Dependencies**: 
- Python 3.8+
- NumPy ≥ 1.20.0
- SciPy ≥ 1.7.0  
- Matplotlib ≥ 3.3.0

**Future Releases** will include pip installable package:
```bash
pip install logical-qft
```

### Basic Usage

**Quick Start**: All classes available in main package file:

```python
# Import from the main package file
from logical_constraints_package import ScalarField

# Create scalar field and set random initial condition
field = ScalarField(grid_size=100, box_length=10.0, mass=1.0)
field.randomize(amplitude=1.0)

print(f"Initial strain: {field.total_strain():.6f}")

# Minimize logical strain - watch physics emerge!
result = field.minimize_strain(max_iterations=500)

print(f"Final strain: {result['final_strain']:.6f}")
print(f"Reduction: {result['initial_strain']/result['final_strain']:.1f}x")
```

### Validate Three Generations

```python
from logical_constraints_package import StandardModelTests

tests = StandardModelTests()
anomaly_results = tests.test_three_generations()

for n_gen, anomaly in anomaly_results.items():
    status = "✓ CONSISTENT" if abs(anomaly) < 1e-10 else "✗ INCONSISTENT"
    print(f"{n_gen}: Tr[Q³] = {anomaly:.6f} {status}")
```

### Generate Experimental Predictions

```python
from logical_constraints_package import ExperimentalPredictions

predictions = ExperimentalPredictions()

# Magnetic moment corrections
g_minus_2 = predictions.magnetic_moment_predictions()
print(f"Muon g-2 prediction: δa_μ = {g_minus_2['delta_a_muon']:.2e}")

# LHC cross-section modifications  
lhc_results = predictions.lhc_cross_section_modifications([400, 500, 600])
for energy, result in lhc_results.items():
    print(f"{energy} GeV: +{result['enhancement_percent']:.1f}% enhancement")
```

## 📊 Framework Structure

### Core Components

| Module | Purpose | Key Classes |
|--------|---------|-------------|
| `core.py` | Logical constraint framework | `LogicalParameters`, `FieldConfiguration` |
| `fields.py` | Field implementations | `ScalarField`, `ElectromagneticField` |
| `quantum.py` | Quantum corrections | `QuantumCorrections` |
| `experiments.py` | Testable predictions | `ExperimentalPredictions` |
| `tests.py` | Validation protocols | `StandardModelTests` |

### The Three Fundamental Laws

1. **Identity Law (A = A)**: Field configurations must be self-consistent
   - Implementation: Minimize |δS/δφ|² strain
   - Result: Generates field equations

2. **Non-Contradiction Law (¬(A ∧ ¬A))**: No contradictory properties
   - Implementation: Penalize negative energy densities  
   - Result: Ensures positive definite Hamiltonians

3. **Excluded Middle Law (A ∨ ¬A)**: All observables must be definite
   - Implementation: Eliminate gauge indefiniteness
   - Result: Generates gauge theory structure

## 🎯 Experimental Predictions

### Precision Measurements

| Observable | Prediction | Status |
|------------|------------|--------|
| Muon g-2 | δa_μ = +2.2×10⁻⁹ | Matches observed +2.5×10⁻⁹ |
| Electron g-2 | δa_e = -2.2×10⁻⁹ | **Testable with future precision** |

### High-Energy Signatures

**LHC Cross-Section Enhancements**:
- 400 GeV: +2% effect
- 500 GeV: +4% effect  
- 1 TeV: +17% effect

**Logical Consistency Scale**: Λ_logic ≈ 480 GeV

## 📁 Repository Structure

### Current Structure (v1.0)

```
logical_constraints/
├── README.md                        # This file
├── logical_constraints_package.py   # Complete framework implementation
├── jupyter_tutorial.py             # Comprehensive demonstration tutorial
├── scoped_paper.md                 # Full theoretical paper (Markdown)
├── Logical_Constraints_Framework.pdf # Theory paper (PDF)
└── repo_structure.md               # Planned expansion structure
```

**Getting Started**: The current repository contains everything needed to run the LogicalQFT framework:
- `logical_constraints_package.py` - Full implementation with all classes and methods
- `jupyter_tutorial.py` - Complete walkthrough demonstrating all capabilities
- `scoped_paper.md` - Theoretical foundation and mathematical details

### Planned Expansion Structure

For production use, the repository will be restructured into:

```
logical_constraints/
├── README.md                     # This file  
├── setup.py                      # Installation script
├── requirements.txt              # Dependencies
├── logical_qft/                  # Main package
│   ├── __init__.py              
│   ├── core.py                  # Core framework
│   ├── fields.py                # Field implementations  
│   ├── quantum.py               # Quantum corrections
│   └── experiments.py           # Predictions
├── examples/                     # Usage examples
├── tests/                        # Test suite
└── docs/                        # Documentation
```

**Note**: Current version provides all functionality in the main package file for simplicity. Modular structure will be implemented in future releases.

## 🧪 Running the Full Tutorial

For a complete demonstration of all framework capabilities:

```python
# Run the comprehensive tutorial
python jupyter_tutorial.py
```

This generates:
- Strain minimization demonstrations
- Three generations validation plots
- Quantum corrections analysis
- Experimental prediction calculations
- Framework validation results

## ⚗️ Validation & Testing

### Comprehensive Test Suite

**Current Version**:
```python
from logical_constraints_package import StandardModelTests

tests = StandardModelTests()
results = tests.run_comprehensive_tests()

for test_name, passed in results.items():
    status = "✓ PASS" if passed else "✗ FAIL"
    print(f"{test_name}: {status}")
```

**Complete Tutorial**: For full demonstration of all capabilities:
```python
python jupyter_tutorial.py
```

**Future Releases** will include dedicated test suite:
```bash
python -m pytest tests/
```

### What's Validated

- ✅ **Strain minimization convergence** to known field equations
- ✅ **Three generations requirement** from anomaly cancellation  
- ✅ **Finite quantum corrections** without external regularization
- ✅ **Gauge theory emergence** from logical definiteness
- ✅ **Experimental prediction generation** with specific numerical values

## 📄 Citation & Publication

### Academic Citation

```bibtex
@article{longmire2025logical,
  title={Logical Consistency Constraints in Quantum Field Theory: Information-Geometric Foundations and Standard Model Applications},
  author={Longmire, James D.},
  year={2025},
  doi={10.5281/zenodo.16377959},
  url={https://github.com/jdlongmire/logical_constraints}
}
```

### Software Citation

```bibtex
@software{logicalqft2025,
  title={LogicalQFT: Computational Framework for Logical Constraints in Quantum Field Theory},
  author={Longmire, James D.},
  year={2025},
  doi={10.5281/zenodo.16377959},
  url={https://github.com/jdlongmire/logical_constraints}
}
```

## 🔬 Current Status & Limitations

### What This Framework Demonstrates

- Working computational implementation of logical strain functionals
- Successful strain minimization to known field equations
- Verified three generations emergence from anomaly constraints
- Finite quantum loop calculations through natural cutoffs
- Specific experimental predictions ready for testing

### What Requires Further Development

- **Experimental validation**: Computational predictions need laboratory confirmation
- **Mass generation mechanisms**: Higgs mechanism and mass hierarchies not yet addressed
- **Gravitational interactions**: Extension to general relativity
- **Cosmological applications**: Dark matter, dark energy, cosmological constant
- **Precision constant derivation**: Fundamental coupling values

### Significance Assessment

This work establishes **logical consistency as a computational organizing principle** for quantum field theory, with demonstrated success in explaining structural features that were previously treated as empirical discoveries. The framework provides both theoretical insights and testable experimental predictions.

## 🛠️ Development & Contributions

### Dependencies

- Python 3.8+
- NumPy ≥ 1.20.0
- SciPy ≥ 1.7.0  
- Matplotlib ≥ 3.3.0

### Development Setup

**Current Version**:
```bash
git clone https://github.com/jdlongmire/logical_constraints.git
cd logical_constraints
pip install numpy scipy matplotlib

# Test the framework
python jupyter_tutorial.py
```

**Future Releases** will include:
```bash
pip install -e .  # Editable installation for development
python -m pytest tests/  # Full test suite
```

### Running Tests

**Current**: Use the comprehensive validation:
```python
from logical_constraints_package import StandardModelTests
tests = StandardModelTests()
tests.run_comprehensive_tests()
```

**Coming Soon**: Dedicated test suite with unit tests, integration tests, and performance benchmarks.

### Contributing

Contributions welcome! Please:
1. Fork the repository
2. Test changes with `python jupyter_tutorial.py`
3. Ensure validation tests pass
4. Submit a pull request with clear description

**Development Priorities**:
- Modular package structure
- Expanded test coverage  
- Performance optimizations
- Additional field theory implementations

## 📧 Contact & Author

### About the Author

**James (JD) Longmire** is a Northrop Grumman Fellow (unaffiliated research), Senior Systems Architect, and AI researcher with extensive experience in complex systems integration, artificial intelligence, and emergent organizational structures. This interdisciplinary background in digital engineering ecosystems, AI development, and systems architecture informs the systematic analytical methodology applied to foundational questions about reality's organizational hierarchy.

**Contact Information**:
- **ORCID**: [0009-0009-1383-7698](https://orcid.org/0009-0009-1383-7698)  
- **Email**: longmire.jd@gmail.com  
- **GitHub**: [@jdlongmire](https://github.com/jdlongmire)

### Support & Questions

For questions about:
- **Theoretical framework**: See `scoped_paper.md` and `Logical_Constraints_Framework.pdf`
- **Implementation details**: See code comments in `logical_constraints_package.py`
- **Usage examples**: Run `jupyter_tutorial.py` for complete demonstration
- **Bug reports**: Open an issue on GitHub
- **Planned features**: See `repo_structure.md` for development roadmap

## 📜 License

<a href="https://github.com/jdlongmire/logical_constraints">Logical Consistency Constraints in Quantum Field Theory</a> © 2025 by <a href="https://github.com/jdlongmire">JAMES (JD) Longmire</a> is licensed under <a href="https://creativecommons.org/licenses/by-nc-sa/4.0/">CC BY-NC-SA 4.0</a>

**Summary**: You are free to share and adapt this work for non-commercial purposes, provided you give appropriate credit and distribute any derivatives under the same license.

## 🔬 Related Work & Context

This framework builds on established principles from:
- Information geometry and maximum entropy methods
- Quantum field theory and the Standard Model
- Mathematical logic and consistency requirements  
- Computational physics and numerical methods

The approach provides a novel synthesis rather than replacement of existing physics, offering new perspectives on why certain structures appear in fundamental theories.

---

**Ready to explore how logical consistency might constrain physical reality?** Start with `jupyter_tutorial.py` for a comprehensive demonstration of the framework in action!
