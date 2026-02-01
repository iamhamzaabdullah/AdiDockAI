# BindFM 🧬  
### A Foundation Model for Molecular Binding

BindFM is an AI-native foundation model for molecular recognition that unifies protein–aptamer, protein–small-molecule, and general docking under a single learned geometric framework.

Unlike classical docking tools that rely on heuristic search, rigid assumptions, and hand-crafted scoring functions, BindFM reframes docking as **probabilistic geometric learning**, predicting distributions over binding poses with calibrated uncertainty.

BindFM is designed as an **AlphaFold-class project**, emphasizing representation learning, scale, and principled inductive bias over incremental improvements to existing docking pipelines.

---

## 🔬 Why BindFM?

Despite decades of development, molecular docking remains fundamentally limited:

| Limitation | Classical Tools |
|-----------|----------------|
| Ligand size bias | Small molecules only |
| Electrostatics | Poorly modeled |
| Flexibility | Heuristic |
| Manual inputs | Required |
| Generalization | Weak |
| Uncertainty | Absent |

BindFM addresses these limitations by **learning the laws of molecular recognition directly from data**, inspired by the paradigm shift introduced by AlphaFold in protein structure prediction.

---

## 🧠 Core Philosophy

BindFM is built on the following principles:

- **Representation over heuristics**
- **Distributional pose prediction**, not single poses
- **Unified ligand handling** (aptamers + small molecules)
- **Physics as regularization**, not scoring
- **Explicit uncertainty modeling**
- **End-to-end learning**

BindFM does **not** attempt to predict absolute binding free energies (ΔG).  
All outputs are **relative, probabilistic, and confidence-aware**.

---

## 🧪 Supported Interaction Types

| Interaction Type | Support Status |
|------------------|---------------|
| Protein–Aptamer (RNA/DNA) | ✅ Phase 1 (primary focus) |
| Protein–Small Molecule | 🚧 Phase 2 |
| Protein–Protein | 🔮 Planned |

Aptamers are intentionally prioritized as the first proof-of-capability due to their size, electrostatics, and flexibility—properties that expose the weaknesses of existing docking tools.

---

## 🏗️ High-Level Architecture
Key architectural features:
- No docking boxes
- No grids
- No genetic algorithms
- No manual active residues

Full details are provided in `docs/architecture.md`.

---

## 🧬 What BindFM Outputs

For a given protein–ligand pair, BindFM produces:

- An **ensemble of binding poses**
- A **binding likelihood score (0–1)**
- **Cluster consistency metrics**
- **Uncertainty estimates**
- Interpretable **interaction maps**

BindFM explicitly avoids reporting misleading single-value binding energies.

---

## 🚀 Project Roadmap

### Phase 1 — Aptamer-First Proof
**Goal:** Outperform HADDOCK in protein–aptamer docking robustness and interface accuracy.

- Protein + aptamer encoders
- Cross-interaction transformer
- Pose distribution learning
- Blind benchmarking against HADDOCK

📄 Outcome: Q1 methods paper (Bioinformatics / Nature Methods tier)

---

### Phase 2 — Unified Docking
**Goal:** Extend BindFM to small molecules and mixed ligand classes.

- Graph-based ligand encoder
- Unified representation layer
- Joint training across ligand types

📄 Outcome: Flagship unified docking paper

---

### Phase 3 — Foundation-Scale Training
**Goal:** Learn molecular recognition at scale.

- Millions of interaction examples
- Contrastive learning (binders vs non-binders)
- Robust uncertainty calibration

📄 Outcome: Nature / Science–level submission

---

## 📁 Repository Structure
BindFM/
├── README.md
├── docs/
│   ├── architecture.md
│   ├── data.md
│   ├── training.md
│   ├── evaluation.md
│   └── roadmap.md
├── models/
│   ├── encoders/
│   ├── interaction_trunk/
│   ├── pose_head/
│   └── refinement/
├── training/
├── inference/
├── evaluation/
├── llm/
└── scripts/

---

## 📊 Data Strategy

BindFM is trained using:
- Protein–RNA/DNA complexes (PDB)
- SELEX-derived aptamer datasets
- Protein–ligand complexes (PDBbind)
- Hard negatives and decoys
- MD-perturbed structures

Negative examples are **explicitly required** to prevent overconfident hallucinations.

---

## 🧠 LLM Integration

Large Language Models are used for:
- Aptamer sequence reasoning
- SELEX enrichment pattern learning
- Mutation suggestions
- Result interpretation

LLMs are **not** used for:
- Coordinate prediction
- Pose generation
- Physics simulation

Geometry remains the domain of deep learning + equivariant models.

---

## ⚙️ Compute & Infrastructure

BindFM is designed for:
- Multi-GPU distributed training
- PyTorch + DDP
- A100 / H100 class accelerators
- Continuous dataset versioning

This project assumes **serious compute availability**.

---

## 📄 Publications & Citations

BindFM is intended to support multiple peer-reviewed publications.

Planned venues include:
- *Bioinformatics*
- *Nature Methods*
- *Nature*
- *Science*

Citation instructions will be added upon first release.

---

## ⚠️ Disclaimer

BindFM is a research system under active development.

- It does **not** replace molecular dynamics
- It does **not** predict absolute binding free energies
- It does **not** guarantee experimental binding

BindFM provides **probabilistic structural hypotheses**, not experimental truth.

---

## 🤝 Contributing

This repository is developed as a startup-scale research effort.

Contributions are welcome via:
- Issues
- Discussions
- Pull requests

Please see `CONTRIBUTING.md` for guidelines.

---

## 📬 Contact

For collaboration, academic partnerships, or early access:
- Open a GitHub issue
- Or contact the maintainers via repository discussions

---

**BindFM aims to do for docking what AlphaFold did for structure prediction —  
replace assumptions with learned representations, at scale.**
