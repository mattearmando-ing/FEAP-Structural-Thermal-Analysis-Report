# Comprehensive Structural and Thermal Finite Element Analysis with FEAP

![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![FEA](https://img.shields.io/badge/Tool-FEAP-blue)
![Structural](https://img.shields.io/badge/Analysis-Structural%20%26%20Thermal-orange)
![Elastoplastic](https://img.shields.io/badge/Material-Elastoplastic-red)
![Convergence](https://img.shields.io/badge/Study-Convergence%20Analysis-purple)

## 📖 Overview

This report documents a comprehensive finite element analysis study conducted using the **FEAP** (Finite Element Analysis Program) software. The work covers a wide range of structural and thermal problems, from linear elastic beam analysis to nonlinear elastoplastic plate behavior, demonstrating the versatility and power of the finite element method in engineering applications.

The analyses follow a systematic approach:

1. **Cantilever Beam Analysis** – Euler-Bernoulli vs. Timoshenko beam elements, convergence study, and shear locking phenomenon.
2. **Plate with Circular Hole** – Stress concentration analysis using Kirsch's analytical solution, comparison between 3-node triangular and 4-node rectangular elements.
3. **Pressure Vessel Analysis** – Thick vs. thin cylinder theory (Lamé equations vs. membrane theory), axisymmetric modeling.
4. **1D Thermal Bar** – Heat conduction with internal heat generation, element performance comparison (Q4 vs. T3).
5. **2D Thermal Rod** – Poisson equation with mixed boundary conditions, inverse problem for heat generation.
6. **CICC Thermal Analysis** – Cable-In-Conduit Conductor for fusion applications, heat transfer with convective cooling.
7. **Elastoplastic Plate** – Nonlinear material behavior, stress redistribution, plastic zone evolution.

> **🔬 Key Contribution:** This work provides a complete reference for FEAP-based structural and thermal analysis, with detailed convergence studies, validation against analytical solutions, and comparative assessment of different element formulations (3-node triangular vs. 4-node quadrilateral).

## 🔬 Key Features

- **Multiple Problem Types:** Structural (beams, plates, pressure vessels) and thermal (1D/2D conduction with generation).
- **Element Comparison:** Systematic evaluation of linear triangular (T3) and quadrilateral (Q4) elements.
- **Convergence Studies:** Mesh refinement sequences from coarse to fine discretizations (doubling strategy).
- **Analytical Validation:** Results compared against closed-form solutions (Euler-Bernoulli, Kirsch, Lamé, Poisson).
- **Nonlinear Analysis:** Elastoplastic material behavior with Von Mises yield criterion and perfect plasticity.
- **Symmetry Exploitation:** Quarter and eighth models to reduce computational cost.
- **Inverse Problem Solving:** Determination of critical heat generation for target temperatures.

## 📊 Key Results

| Problem | Element Type | Key Finding | Error |
| :--- | :--- | :--- | :--- |
| **Cantilever Beam** | Euler-Bernoulli | Exact solution with 1 element | 0.00% |
| **Cantilever Beam** | Timoshenko | Requires 10-12 elements for <1% error | <1% |
| **Cantilever Beam** | 4-node Q4 (linear) | 128 elements for <1% error | <1% |
| **Cantilever Beam** | 3-node T3 | 128×128 mesh required | <1% |
| **Plate with Hole** | 4-node Q4 | σ_FEAP = 7.96×10⁸ N/m² | +6.1% (finite plate) |
| **Plate with Hole** | 3-node T3 | σ_FEAP = 7.91×10⁸ N/m² | +5.5% (finite plate) |
| **Thick Cylinder** | 4-node Q4 | Excellent convergence with 64×2 mesh | <1% |
| **Thin Cylinder** | 3-node T3 | Accurate with coarse mesh | ~1% |
| **Thermal Bar (Q=1)** | 4-node Q4 | Captures parabolic profile perfectly | ~0% |
| **Thermal Bar (Q=1)** | 3-node T3 | Underestimates peak temperature | ~1.5% |
| **Thermal Rod** | 4-node Q4 | T_M = 127.25°C (analytical: 145°C) | Physical (2D effect) |
| **CICC Conductor** | 4-node Q4 | T_hot = 7.65 K (theoretical: 7.63 K) | <0.3% |
| **Elastoplastic Plate** | 4-node Q4 | First yield at 40% load | Perfect match |

> **⚠️ Key Insight:** The 4-node quadrilateral element consistently outperforms the 3-node triangular element in both structural and thermal analyses. However, for simple geometries with constant gradients, both element types converge rapidly. The study demonstrates the importance of element selection based on problem physics: Euler-Bernoulli beams are exact for bending, while Timoshenko and 2D elements require mesh refinement to overcome shear locking.

## 🛠️ Technologies & Tools

- **FEA Software:** FEAP (Finite Element Analysis Program) – University of California, Berkeley.
- **Element Formulations:**
  - 3-node Linear Triangular (T3) – Constant strain/flux.
  - 4-node Bilinear Quadrilateral (Q4) – Linear strain/flux.
  - Euler-Bernoulli Beam – Exact for slender beams.
  - Timoshenko Beam – Includes shear deformation.
- **Material Models:** Linear elastic, elastoplastic (Von Mises, perfect plasticity).
- **Solution Strategies:** Incremental loading, Newton-Raphson iterations, convergence tolerance control.
- **Symmetry Exploitation:** Quarter and eighth models with symmetry boundary conditions.
- **Mesh Generation:** BLEND command for circular-to-square transitions, structured meshing.
- **Post-Processing:** Stress and heat flux recovery, nodal projection, contour plotting.

## 📄 Full Report

For a complete description of the mathematical formulations, convergence studies, and detailed results for each problem, please refer to the  
[Full Project Report](https://cdn.jsdelivr.net/gh/mattearmando-ing/[nome-repository]@main/FEAP_Structural_Thermal_Analysis_Report.pdf)

---

## 📚 Problems Covered

### 1. Cantilever Beam (Structural)
- Euler-Bernoulli (shear off) vs. Timoshenko (shear on)
- Convergence study for 2D elements: 4-node Q4 and 3-node T3
- Shear locking phenomenon analysis

### 2. Plate with Circular Hole (Structural)
- Kirsch's analytical solution for infinite plate
- Finite plate correction factor (b/2r = 7)
- Stress concentration factor (K_t ≈ 3)

### 3. Pressure Vessels (Structural)
- Thick cylinder: Lamé equations (nonlinear stress distribution)
- Thin cylinder: Membrane theory (constant stress)
- Axisymmetric modeling with 3-node and 4-node elements

### 4. 1D Thermal Bar (Thermal)
- Heat generation in first half only
- Analytical solution: quadratic temperature profile
- Element performance: Q4 vs. T3

### 5. 2D Thermal Rod (Thermal)
- Mixed Dirichlet boundary conditions
- Inverse problem: find Q for T_M = 300°C
- Superposition principle application

### 6. CICC Conductor (Thermal)
- Superconducting cable for fusion applications
- Convective cooling with supercritical Helium
- Material contrast: k_SC = 10 vs. k_SS = 0.2 W/(m·K)

### 7. Elastoplastic Plate (Nonlinear)
- Von Mises yield criterion
- Perfect plasticity (no hardening)
- Plastic zone evolution ("butterfly" shape)
- Stress redistribution beyond first yield

---

*Project developed for the "Finite Element Analysis Program" course – Politecnico di Torino (Academic Year 2025/2026).*
