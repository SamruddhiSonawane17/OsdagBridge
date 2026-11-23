OsdagBridge — Automated LaTeX Structural Design Report
FOSSEE Internship Screening Task | OsdagBridge
Project Overview
OsdagBridge is a modular Python application for steel bridge analysis and design within the Osdag ecosystem. This internship project focuses on generating a structured, calculation-based LaTeX/PDF engineering design report from bridge inputs and analysis results, with particular attention to loading, design checks, and report presentation.

The application provides a PySide6 desktop interface and uses a shared Python core for engineering calculations and report preparation.
Project Objectives
- Generate an organized structural design report from bridge model inputs and computed results.
- Present relevant design parameters, equations, units, and intermediate calculations.
- Document IRC-based loading and load combinations.
- Include girder, deck slab, and cross-bracing results where available.
- Produce a readable PDF report with consistent chapter headings and tables.
- Support traceable design verification by reporting both passing and failing checks.
Main Features
Bridge analysis and design
- Plate-girder bridge modelling and structural analysis workflow.
- Bridge geometry, girder spacing, deck configuration, and load input handling.
- Girder-by-girder design-check reporting, including four physical girders (G1–G4) in the tested model.
- Deck slab and cross-bracing calculation summaries.
Automated report generation
- LaTeX-based generation of a multi-chapter PDF report.
- Engineering input summaries, numerical results, equations, and units.
- Chapter 3 loading details, including vehicle live loads, footpath loading, impact factors, braking, wind, seismic, temperature, and load combinations where inputs/results are available.
- Repeated headings across multi-page report tables for readability.
Engineering references
The project includes calculations and checks based on applicable Indian Roads Congress (IRC) provisions. The exact code clauses, input assumptions, and generated values should be verified before using the output for engineering decisions.
Technology Stack
Area	Technology
Programming	Python 3.11–3.12
Desktop interface	PySide6 / Qt
Environment	Conda
Analysis	OsdagBridge core, OpenSeesPy / OspGrillage components
Report generation	LaTeX, MiKTeX / pdfLaTeX
PDF inspection	PyMuPDF (optional)
Version control	Git and GitHub


Repository Layout
OsdagBridge/
├── environment.yml
├── pyproject.toml
├── README.md
├── src/
│   ├── osdagbridge/                 # Desktop application and shared core (layout may vary)
│   └── ospgrillage/                 # Included analysis and report modules
├── tests/
├── docs/
└── examples/
Relevant report files in the submitted project include:
src/ospgrillage/osdagbridge/core/reports/chap3.py
src/ospgrillage/osdagbridge/core/reports/report_generator.py
Some development copies may have these modules under src/osdagbridge/ instead. Use the paths present in your checked-out repository.
Setup and Installation (Windows)
Prerequisites: Miniconda or Anaconda, Git, and a working LaTeX distribution such as MiKTeX.
# Clone your own submitted repository (replace the URL)
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd OsdagBridge

# Create the project environment
conda env create -f environment.yml
conda activate osdagbridge-env

# Install the project if required by your environment
pip install -e .
Run the desktop application
From the project root:
$env:PYTHONPATH = "$PWD\src;$PWD\src\ospgrillage"
python -m osdagbridge.desktop
The additional PYTHONPATH entry is relevant to the submitted development layout; it may not be necessary for other installations.
Demonstration Workflow
1. Launch the OsdagBridge desktop application.
2. Enter or load the bridge geometry, material, and loading parameters.
3. Run the structural analysis and design calculations.
4. Review the girder, deck, and bracing design outputs.
5. Generate the LaTeX-based PDF design report.
6. Inspect the report's loading chapters, calculation tables, and design-check summaries.
Example Model and Verification Status
A development test used a 30 m span, 8.4 m deck width, and four girders at 2.1 m spacing. The girder mapping was checked to ensure separate G1–G4 results were produced.

Important: Successful execution and PDF generation do not mean all engineering checks passed. In the observed test output, girder fatigue stress and intermediate stiffener checks reported failures; end-diaphragm checks were not fully evaluated. Some thermal load results and summary labels also required further validation. These issues must be resolved and the results independently reviewed before engineering use.
Testing
Where the test dependencies are installed:
python -m pytest -q
Also perform a manual desktop test and inspect the generated PDF. The command above is a test invocation, not a claim that the entire suite currently passes.
Deliverables
- OsdagBridge source code and environment configuration.
- LaTeX/PDF report-generation modules.
- Generated structural design report (PDF).
- Project documentation and demonstration video.
Scope and Disclaimer
This is an internship screening/development submission. Its outputs are for development, testing, and educational review. Structural design calculations must be checked by a qualified engineer before any practical application.
Acknowledgement
Developed as part of the FOSSEE internship screening task using the OsdagBridge project ecosystem. Credit for the underlying OsdagBridge framework and its dependencies belongs to their respective maintainers and contributors.
