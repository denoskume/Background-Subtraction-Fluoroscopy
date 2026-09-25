# Background Subtraction

Neurointerventional image-processing project for detecting moving guidewires and microcatheters in fluoroscopic sequences using a fixed background reference, histogram transformation, spatial and spectral filtering, morphology, segmentation, and quantitative validation.

The project follows the same four-notebook structure used across the repository:

- [Problem Statement](notebooks/background_subtraction_problem_statement.ipynb) — context, inputs, objectives, constraints, and numbered workflow stages.
- [Requirements Gathering & Approach](notebooks/background_subtraction_requirements_gathering_and_approach.ipynb) — implementation requirements, acceptance criteria, and task-to-code traceability.
- [Theory](notebooks/background_subtraction_theory.ipynb) — mathematical foundations, assumptions, metrics, and limitations.
- [Implementation](notebooks/Background_Subtraction.ipynb) — executable code and outputs only.

The number of numbered stages is project-dependent. For the current implementation, the supporting notebooks are synchronized with the **15 executable cells** in the implementation notebook.

## Current Workflow

1. configure the processing environment;
2. define reusable processing and evaluation functions;
3. validate frames and annotations;
4. build the static background reference;
5. inspect the intermediate processing pipeline;
6. generate fixed-threshold, Otsu, and EM/GMM masks;
7. compare segmentation strategies qualitatively;
8. evaluate every strategy across the sequence;
9. aggregate metrics and retain the selected strategy;
10. plot temporal validation curves;
11. summarize strategy-level performance;
12. assemble the final retained pipeline;
13. generate the final guidance gallery;
14. perform final qualitative validation;
15. export results and verify deliverables.

## Outputs

Generated numerical results:

```text
outputs/background_subtraction_metrics.csv
outputs/background_subtraction_summary.csv
```

Generated figures:

```text
outputs/figures/
├── 01_background_reference.png
├── 02_intermediate_pipeline.png
├── 03_strategy_comparison_representative.png
├── 04_temporal_metric_curves.png
├── 05_strategy_summary.png
├── 06_final_guidance_gallery.png
└── 07_final_validation.png
```

## Run

From the project directory:

```bash
cd ~/Master_SIP_EC-Nantes/Projects/Background_Subtraction

python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
code .
```

Open [Background_Subtraction.ipynb](notebooks/Background_Subtraction.ipynb), select the project environment as the Jupyter kernel, and execute the implementation notebook from top to bottom when fresh outputs are required.

## Project Structure

```text
Background_Subtraction/
├── data/
│   └── catheter/
├── notebooks/
│   ├── background_subtraction_problem_statement.ipynb
│   ├── background_subtraction_requirements_gathering_and_approach.ipynb
│   ├── background_subtraction_theory.ipynb
│   └── Background_Subtraction.ipynb
├── outputs/
│   ├── figures/
│   ├── background_subtraction_metrics.csv
│   └── background_subtraction_summary.csv
├── requirements.txt
└── README.md
```

## Implemented Scope

- fixed static background reference from frame 201;
- Gaussian spatial smoothing;
- percentile-based intensity normalization;
- signed background subtraction;
- Gaussian high-pass filtering in the Fourier domain;
- morphological refinement;
- fixed-threshold, Otsu, and two-component EM/GMM segmentation;
- sequence-level SAD, MSE, PSNR, Dice, and IoU evaluation;
- quantitative strategy comparison and retained-strategy selection;
- temporal metric analysis;
- guidance overlays and qualitative validation;
- CSV export and explicit deliverable checks.

## Out of Scope

- non-rigid registration;
- optical flow;
- learned segmentation networks;
- adaptive online background models;
- clinical validation or deployment.

## Participant

**Denos Kume**  
MSc. CORO DASSIP — École Centrale de Nantes
