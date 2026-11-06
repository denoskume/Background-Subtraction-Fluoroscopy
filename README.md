<p>
  <img align="left" src="https://www.ec-nantes.fr/medias/photo/logocn-rvb_1648479844750-png?ID_FICHE=178994&amp;INLINE=FALSE" alt="Centrale Nantes" height="64">
</p>
<p align="right"><strong>MSc. CORO DASSIP</strong></p>
<br clear="both">

<h1 align="center">Background Subtraction</h1>

Neurointerventional image-processing project for detecting moving guidewires and microcatheters in fluoroscopic sequences using a fixed background reference, histogram transformation, spatial and spectral filtering, morphology, segmentation, and quantitative validation.

The project is organized into four complementary notebooks:

- [Problem Statement](notebooks/problem_statement.ipynb) — context, inputs, objectives, constraints, and numbered workflow stages.
- [Requirements](notebooks/requirements.ipynb) — implementation requirements, acceptance criteria, and task-to-code traceability.
- [Theory](notebooks/theory.ipynb) — mathematical foundations, assumptions, metrics, and limitations.
- [Implementation](notebooks/main.ipynb) — executable code and outputs only.

> **Reconstruction note (6 November 2026):** The initial `notebooks/main.ipynb` committed on 27 September 2026 was an empty (0-byte) file. The 15-cell implementation has since been reconstructed from the three supporting notebooks, the provided images/annotations, and archived figures/metrics. It has been executed successfully in GitHub Actions. The original numerical hyperparameters could not be recovered; results from re-running the reconstructed notebook may differ from the historical CSVs. The notebook writes new CSVs with the `_reconstructed` suffix so the historical numerical evidence is not overwritten. Figure files are regenerated locally on execution; the historical committed figures remain unchanged until a user explicitly commits replacements.


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
git clone https://github.com/denoskume/Background-Subtraction-Fluoroscopy.git
cd Background-Subtraction-Fluoroscopy

python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
code .
```

Open [main.ipynb](notebooks/main.ipynb), select the project environment as the Jupyter kernel, and execute the implementation notebook from top to bottom when fresh outputs are required.

## Project Structure

```text
Background_Subtraction/
├── data/
│   └── catheter/
├── notebooks/
│   ├── problem_statement.ipynb
│   ├── requirements.ipynb
│   ├── theory.ipynb
│   └── main.ipynb
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

## Participants

Denos Kume  
Oluwole Shokunbi
