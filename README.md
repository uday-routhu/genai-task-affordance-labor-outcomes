# GenAI Task Affordances and Labor Outcomes

This repository contains code and data accompanying the manuscript **“Beyond Aggregate GenAI Exposure: Associations Between Task-Affordance Configurations and Employment and Wage Growth”** by Udayakumar Routhu.

The study combines O*NET task information, published GenAI exposure annotations, and U.S. Bureau of Labor Statistics data to examine whether task-affordance configurations are associated with occupational employment and wage growth beyond aggregate GenAI exposure.

## Code organization

The workflow is organized into numbered folders. Each contains `Code`, `Input`, and/or `Output` subfolders as applicable.

| Folder | Contents |
|---|---|
| [01_BLS_Raw_Data_Construct](01_BLS_Raw_Data_Construct/) | Occupational selection and initial task records. |
| [02_Task_Data_and_Classification](02_Task_Data_and_Classification/) | Task preparation, classifications, human validation, and audit records. |
| [03_Layer1_Task_Affordance_Count](03_Layer1_Task_Affordance_Count/) | Task counts and unweighted shares. |
| [04_Layer2_Task_Affordance_Weighted](04_Layer2_Task_Affordance_Weighted/) | Core/Supplemental-weighted task shares. |
| [05_Layer3_Task_Configuration](05_Layer3_Task_Configuration/) | Task-affordance configurations and importance positions. |
| [06_Eloundou_Task_Alignment](06_Eloundou_Task_Alignment/) | Alignment and construction of exposure benchmarks. |
| [07_GenAI_Exposure](07_GenAI_Exposure/) | Integration of configurations and exposure benchmarks. |
| [08_Labor_Outcomes](08_Labor_Outcomes/) | Employment and wage outcome construction. |
| [09_RQ1_Analysis](09_RQ1_Analysis/) | Main analyses, robustness checks, and figure output. |

## Software requirements

The code uses Python notebooks. Install JupyterLab and the required packages:

```bash
python -m pip install jupyterlab pandas numpy scipy statsmodels matplotlib openpyxl scikit-learn
```

## Running the analysis

1. Clone this repository or download and extract it using **Code → Download ZIP**.
2. Open the notebooks in JupyterLab or your preferred Python notebook environment.
3. In each notebook you run, replace the root-directory path with the location of your project folder. Keep the repository's folder structure unchanged.

For the two analysis notebooks, set `BASE_DIR`, for example:

```python
from pathlib import Path
BASE_DIR = Path(r"C:\Users\YourName\Projects\genai-task-affordance-labor-outcomes")
```

The supplied paths refer to the original Google Drive workspace. Use your own local or mounted Drive path instead.

Run the cells from top to bottom in:

- [Model_Analysis.ipynb](09_RQ1_Analysis/Code/Model_Analysis.ipynb): descriptive summaries, employment and wage models, and sector heterogeneity analyses.
- [Robustness_Tests.ipynb](09_RQ1_Analysis/Code/Robustness_Tests.ipynb): supporting robustness checks.

Both notebooks independently load the prepared datasets supplied in folders 05, 07, and 08. **Task classification and data preparation do not need to be rerun to use these inputs.**

### Data preparation and audit notebooks

Folders 01–08 contain the upstream preparation workflow. Root variables are named `ROOT`, `BASE_DIR`, or `DATA_DIR`; the stage 01 notebook's root points directly to its stage folder.

The notebooks in `02_Task_Data_and_Classification/Code/Audit/` document classification and validation preparation. They are optional for running the analysis and require additional path/input configuration; generating fresh classifications also requires API credentials. Use a separate working copy when rebuilding data or validation templates, because these notebooks can replace existing outputs.

## Data sources

- [O*NET Database](https://www.onetcenter.org/database.html), version 30.0: occupation information, task statements, and task ratings.
- [BLS Occupational Employment and Wage Statistics](https://www.bls.gov/oes/tables.htm): occupational employment and wage data, including the 2017–2019 and 2023–2025 study periods.
- [Eloundou et al., GPTs-are-GPTs](https://github.com/openai/GPTs-are-GPTs): published task-level GenAI exposure annotations.

Source files and prepared datasets are included in the corresponding workflow folders. Use the supplied versions when reproducing the analysis.

## Contact

Udayakumar Routhu, Capitol Technology University  
Email: urouthu@captechu.edu
