# 🧬💊 ProteoHunter 
-----------------------------------------------------------------

**ProteoHunter** is a fully automated, rule‑based protein-ligand docking pipeline designed for accurate binding mode prediction and confidence scoring. It integrates:

- **Geometric pocket detection** via K‑means clustering of surface residues
- **Density-based ligand volume estimation** (18–25 Å³/heavy atom, adjusted for flexibility)
- **Dual‑engine docking** (AutoDock Vina + GNINA) with consensus scoring
- **Multi‑pocket fallback** (tests up to 3 pockets sequentially)
- **Volume‑ratio validation** (aborts on undersized pockets to avoid false positives)
- **Calibrated confidence score** (0–1) derived from binding strength, pocket quality, ligand efficiency, docking consistency, and compatibility
- **External validation** via PoseBusters (22 geometric/chemical checks)

**Key finding:** On a 30‑example benchmark spanning proteases, kinases, GPCRs, nuclear receptors, and metabolic enzymes, ProteoHunter achieved **93% accuracy**, significantly outperforming the state‑of‑the‑art deep‑learning model Boltz‑2 (77%, p = 0.0078).

# 📦 Installation
-----------------------------------------------------------------
1. Create and activate the conda environment
pip install -r requirements.txt

2. Install external docking tools
a) AutoDock Vina (required):
conda install -c conda-forge vina

b) GNINA (optional but recommended):
wget https://github.com/gnina/gnina/releases/latest/download/gnina
chmod +x gnina
mv gnina /usr/local/bin/

c) MGLTools (optional, for PDBQT conversion):
Download from https://ccsb.scripps.edu/mgltools/downloads/

# 🚀 Quick Start
-----------------------------------------------------------------
Run step‑by‑step in Jupyter Lab (Recommended)

Step 1 – Fetch protein structure:

Step 2 – Detect binding pockets:

Step 3 – Run docking:

posebuster_validation.py

# 🔧 Configuration
-----------------------------------------------------------------
Before running, edit the all paths:

VINA_PATH = "/path/to/your/vina"
GNINA_PATH = "/path/to/your/gnina"
MGL_DIR = "/path/to/your/mgltools"
and others

# 📊 Output
-----------------------------------------------------------------
Each run generates:

- PDB file: the protein structure

- Summary file (*_summary.txt): protein statistics and amino acid composition

- Pocket report (*_pocket_report.txt): detected pockets with scores and druggability

- Docking report (*_docking_report.txt): full docking results, confidence score, and warnings

- 3D interactive viewer 

- Vina/GNINA result files (vina_results.pdbqt, gnina_results.pdbqt)

# 🧪 Validation with PoseBusters
-----------------------------------------------------------------
ProteoHunter integrates PoseBusters as an external validation tool. 

PoseBusters performs 22 geometric and chemical checks:

Chemical validity (RDKit sanitization, bond lengths, bond angles)

Intramolecular plausibility (internal steric clashes, ring planarity)

Intermolecular reasonableness (protein-ligand distance, volume overlap)

# 📚 Citation
-----------------------------------------------------------------
If you use ProteoHunter in your research, please cite:

[Your name et al., "ProteoHunter: A PoseBusters-Validated Docking Pipeline Outperforms Boltz2 Across 30 Diverse Drug Targets," Journal Name, Year. DOI:X]


# 📝 License
-----------------------------------------------------------------
This project is licensed under the MIT License.

# 📧 Contact
-----------------------------------------------------------------
For questions, bug reports, or feature requests, please contact: [armannakib35@gmail.com]