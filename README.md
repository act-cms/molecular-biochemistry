Molecular Biochemistry: Computational Structural Biology of Enzymes and Designed Proteins
=========================================================================================

A nine-part module that teaches molecular biochemistry as a computational
discipline. Students begin by locating a catalytic triad by hand in a raw PDB
coordinate file and finish by hallucinating a peptide binder against a protein
target — working throughout on one real enzyme, the polyethylene terephthalate
hydrolase (PETase) of *Ideonella sakaiensis*.

The module is written for junior and senior undergraduates in biochemistry,
biophysics, computational biology, bioengineering and data science. It assumes
general and introductory biochemistry, and Python at the level of variables,
conditionals and loops; the command line, NumPy, and every physical and
statistical idea the notebooks use are built up from near zero where they are
first needed. All nine notebooks run in Google Colab with no local
installation. Total student working time is about **12.5 hours**, which fits
nine class sessions of 75–90 minutes.

Each part can be taught on its own, but they are designed to accumulate. The
catalytic triad students first find in a text file in Part 1 becomes the pocket
they centre a docking box on in Part 7, the residues whose thermal fluctuations
they measure in Part 6, and the site whose predicted coordinates they validate
against the crystal structure in Part 8. A parallel nucleic-acid thread follows
a bacterial purine riboswitch aptamer through the early parts, so students meet
the same questions in a polyanionic system where the electrostatics are
different.

## Lesson/Module Contents

The nine lessons are listed in teaching order below. Note that GitHub displays
the directories alphabetically, which is **not** the intended sequence.

1. **Foundations: UNIX, Python Data Structures, and PDB Record Parsing**
    * Directory: `Foundations-unix-python-pdb`
    * Description: Shell pipelines over a crystallographic coordinate file;
      Python data structures for a multi-chain assembly; net charge and
      isoelectric point computed from the atomic records by
      Henderson-Hasselbalch. Introduces the legacy PDB format alongside
      PDBx/mmCIF.
    * Time: 75 min · CPU runtime

2. **Biomolecular Databases, Sequence Literacy, and Enzyme Kinetics**
    * Directory: `Databases-sequence-kinetics`
    * Description: Programmatic queries to UniProt, RCSB and NCBI Entrez, and
      reconciling a numbering offset between a precursor entry and a deposited
      structure. Sliding-window hydrophobicity and GC-content profiles. Then
      Michaelis-Menten fitting by non-linear least squares, and competitive
      versus non-competitive inhibition diagnosed by a global fit across
      multiple inhibitor concentrations.
    * Time: 75 min · CPU runtime

3. **Sequence Alignment, Scoring Matrices, and Phylogenetics**
    * Directory: `Sequence-alignment`
    * Description: Homology as an inferred hypothesis rather than a
      measurement; pairwise alignment under BLOSUM62 and PAM250 with affine
      gap penalties, and a sensitivity analysis of both; multiple sequence
      alignment with MAFFT and a colourblind-safe conservation heatmap;
      Neighbor-Joining compared against Maximum Parsimony, with outgroup
      rooting and a zero-length polytomy to diagnose.
    * Time: 90 min · CPU runtime

4. **Force Fields and Energy Minimization**
    * Directory: `Force-Fields-Energy-Minimization`
    * Description: A classical Class I potential energy function taken apart
      term by term and evaluated numerically. Students write a
      steepest-descent minimizer in pure Python to relieve a Lennard-Jones
      clash, contrast it with conjugate gradient and L-BFGS, then parameterize
      a real enzyme with Amber14 in OpenMM and measure per-residue
      displacement.
    * Time: 90 min · **GPU runtime recommended** (see Runtimes below)

5. **Solvation, Counter-Ions, and MD System Preparation**
    * Directory: `Solvation-ions-md-preparation`
    * Description: Implicit versus explicit solvent and what each model can
      represent; 3-site against 4-site water geometry; the ion arithmetic for
      a neutral system at 150 mM NaCl; periodic cell construction with OpenMM
      `Modeller`, minimum solute-to-wall clearance, and why an unneutralized
      system is an artifact under Particle Mesh Ewald.
    * Time: 90 min · CPU runtime

6. **Molecular Dynamics, Ensembles, and Trajectory Analysis**
    * Directory: `Molecular-Dynamics-trajectories`
    * Description: The velocity-Verlet update and why rigid bond constraints
      are what permit a 2 fs timestep; the NVE, NVT and NPT ensembles and the
      case for Langevin middle integrators and Monte Carlo barostats; an
      equilibration pipeline in OpenMM; RMSD, RMSF and radius of gyration as
      convergence and flexibility diagnostics.
    * Time: 90 min · CPU runtime

7. **Molecular Docking, Scoring Functions, and Virtual Screening**
    * Directory: `Molecular-Docking`
    * Description: An empirical scoring function broken into its steric,
      hydrophobic, hydrogen-bonding and torsional-entropy components, and what
      a physics-based force field leaves out. Ligand preparation in RDKit
      (SMILES, ETKDG conformers, rotatable bonds, logP), search-box
      definition on the catalytic triad, and screening performance measured by
      ROC-AUC and early enrichment factors.
    * Time: 90 min · CPU runtime

8. **Structure Prediction: Evoformer, Invariant Point Attention, and Confidence**
    * Directory: `Structure-Prediction`
    * Description: The core tensor operations of AlphaFold2 implemented in
      NumPy — the outer-product mean and the triangular multiplicative update
      that enforces the triangle inequality — then residues as rigid-body
      frames in SE(3), with Invariant Point Attention shown numerically to be
      invariant to global rotation and translation. Closes on pLDDT and
      predicted aligned error, and validation against experimental
      coordinates.
    * Time: 75 min · CPU runtime

9. **Peptide Binder Design with AfDesign**
    * Directory: `Peptide-Binder-Design`
    * Description: Hallucinating a short peptide binder against a chosen
      target chain by optimizing interface contacts and binder pLDDT through
      AlphaFold, using ColabDesign's AfDesign. Students compare optimizers,
      inspect the designed sequence profile, and confront the central
      objection: a structure-prediction confidence score is a poor proxy for
      binding affinity, and the search can return adversarial sequences.
    * Time: 75 min · **GPU runtime required**

## Prerequisites

**Scientific.** General chemistry, including acids, bases, pH and buffers.
Introductory biochemistry: amino acids, the peptide bond, protein secondary
and tertiary structure, nucleic acid structure. Enzymes as catalysts — no
prior exposure to kinetic modelling is assumed. Introductory physics or
physical chemistry helps, but energy, force and the Boltzmann distribution are
each reintroduced where they are used.

**Programming.** Basic Python syntax: variables, conditionals, loops and
function calls. No prior command-line experience is required; the shell is
taught from the beginning of Part 1. No prior experience with NumPy, linear
algebra in code, or machine-learning frameworks is required.

## Running the notebooks

**Google Colab** is the developed and tested platform, and the recommended one.
Every notebook installs its own dependencies in a first setup cell and
downloads the structures it needs over HTTPS, so there is nothing for students
to install and nothing to distribute alongside the notebook.

A **local installation** works given Python 3, OpenMM, PDBFixer, RDKit,
MDAnalysis, Biopython, gemmi, py3Dmol, NumPy, SciPy, scikit-learn, pandas,
matplotlib and jupyterquiz, plus MAFFT for Part 3. Part 9 additionally needs a CUDA GPU and
the JAX stack that ColabDesign depends on.

### Runtimes

Eight of the nine notebooks run on a CPU runtime. Two deserve attention before
class:

* **Part 4 (Force Fields)** runs on CPU, but its implicit-solvent minimization
  is O(N²) with no cutoff: on a free CPU runtime that single cell takes about
  fourteen minutes. The code already prefers CUDA when it is available, so
  selecting a T4 GPU runtime reduces it to a minute or two. If you must stay on
  CPU, start the cell and lecture over it.
* **Part 9 (Peptide Binder Design)** requires a GPU runtime and will not run
  without one. It downloads roughly 5.6 GB of AlphaFold parameters on every
  fresh session, so have students start the setup cell before any introduction.

### A note on dependency pinning

Four notebooks write a pip requirement as `openmm>=8.2.0` or `rdkit>=2024.3`
without quotation marks. IPython hands that to the shell, which reads `>=` as
an output redirection: the version floor is silently not enforced and a stray
file appears in the working directory. Quoting those specifiers is a one-line
fix worth making before the first class.

## Assessment

Each notebook carries embedded `jupyterquiz` self-checks — thirty-eight
questions across the module — placed after the section they assess, with
automated per-option feedback. These are formative and ungraded: students get
the explanation whether they answer correctly or not.

Eight of the nine notebooks also close with a set of open-ended challenge
questions intended for a graded laboratory report. These ask students to
extend or stress-test what the notebook did rather than to repeat it, and they
are where the real assessment weight belongs.

## Instructor materials

A companion instructor guide accompanies every notebook: a four- or five-page
PDF covering an at-a-glance table of runtime, wall-clock time, network
dependencies and files produced; a before-class checklist; a
section-by-section walkthrough with the actual expected output; the complete
quiz answer key; notes on the open-ended report questions; and the known
issues for that notebook.

Because these guides contain full answer keys, they are intended for
instructors rather than students. If you are viewing a copy of this repository
that includes the `*-Instructor-Guide.pdf` files, treat them accordingly and do
not distribute them to a class. Instructors adopting this module can request
access through the ACT-CMS portal.

### Known issues, and why they are documented rather than hidden

Several notebooks print conclusions that their code does not establish. These
are catalogued in the instructor guides, with a suggested way to teach each
one, because they make unusually good discussion material — a student who
notices that a summary line contradicts the numbers printed above it has
learned something that a notebook which always agrees with itself cannot
teach. Three examples, so that adopting instructors know what they are taking
on:

* Part 5 hard-codes a net charge that Part 1 computes differently, and its
  hand-calculated ion counts disagree with what the solvation routine actually
  builds. The discrepancy is the protein's real charge.
* Part 8 does not run AlphaFold. It perturbs experimental coordinates and
  analyses the result, and its summary claims an accuracy better than the
  values printed directly above it. The Evoformer and IPA sections, which are
  the substance of the notebook, are correct.
* Part 7 performs no conformational search; its reported binding score is a
  constant plus a torsional term. It works well as an exercise in
  scoring-function anatomy and screening statistics, which is how the guide
  frames it.

Read the guide for a notebook before teaching it.

## Running systems and data sources

All structures are fetched at runtime from the RCSB Protein Data Bank; no
coordinate files are redistributed here.

* **Protein thread:** *Ideonella sakaiensis* PETase, PDB
  [`6ANE`](https://www.rcsb.org/structure/6ANE), UniProt `A0A0K8P6T7` — a
  bacterial hydrolase that degrades post-consumer PET plastic, and the subject
  of an active protein-engineering literature.
* **Nucleic acid thread:** a bacterial purine riboswitch aptamer, PDB
  [`1Y26`](https://www.rcsb.org/structure/1Y26), Rfam `RF00167`.
* **Part 3** uses forkhead DNA-binding domains drawn from UniProt.
* **Part 9** defaults to PDB [`4N5T`](https://www.rcsb.org/structure/4N5T) and
  accepts any PDB or UniProt accession, or an uploaded structure.

## Author

**Keith Fraser, PhD**  
Senior Lecturer, Department of Biological Sciences  
Rensselaer Polytechnic Institute

## Citation

If you adopt or adapt this module, please cite it as:

> Fraser, K. *Molecular Biochemistry: Computational Structural Biology of
> Enzymes and Designed Proteins.* ACT-CMS, 2026.

## Acknowledgments

These notebooks build on open-source scientific software, and the module would
not exist without it: OpenMM, PDBFixer, RDKit, MDAnalysis, Biopython, gemmi,
NumPy, SciPy, pandas, matplotlib, py3Dmol, MAFFT, jupyterquiz, and
ColabDesign/AfDesign. Primary citations with DOIs for every method, force
field, database and structure appear in the References section of each
notebook.
