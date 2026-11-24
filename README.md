# GenAI Task Affordances and Labor Outcomes

Code and data for **“Beyond Aggregate GenAI Exposure: Associations Between Task-Affordance Configurations and Employment and Wage Growth”**.

The study asks whether the tasks GenAI could automate or support, and how important those tasks are within an occupation, help explain differences in U.S. occupational employment and wage growth beyond aggregate GenAI exposure.

## Reproduce the analysis

Start with the two notebooks in [09_RQ1_Analysis/Code](09_RQ1_Analysis/Code/). Both run independently using the prepared datasets in folders 05, 07, and 08. No API key or new task classification is needed for this analysis.

1. Clone or download this repository and keep its folder structure intact.
2. Install the analysis packages and start JupyterLab.

   ```bash
   python -m pip install jupyterlab pandas numpy statsmodels matplotlib jinja2
   jupyter lab
   ```

3. In the first code cell of each notebook, set `BASE_DIR` to the repository folder on your computer or mounted Google Drive. Run the cells from top to bottom.

| Notebook | What it produces |
| --- | --- |
| [09_Model_Analysis.ipynb](09_RQ1_Analysis/Code/09_Model_Analysis.ipynb) | Occupational task summaries, employment and wage models, and comparisons across occupational groups and sectors. It also saves the [task-share and importance-position figure](09_RQ1_Analysis/Figures/task_share_imp_positions.png). |
| [09_Robustness_Tests.ipynb](09_RQ1_Analysis/Code/09_Robustness_Tests.ipynb) | Robustness checks covering occupational-group fixed effects, the alternative exposure benchmark, influential occupations, core-weighted task shares, and median wage. |

## Data preparation

| Folder | Purpose |
| --- | --- |
| [01_BLS_Raw_Data_Construct](01_BLS_Raw_Data_Construct/) | Match BLS occupations to O*NET and build the initial occupation and task files. |
| [02_Task_Data_and_Classification](02_Task_Data_and_Classification/) | Prepare the task universe, classify tasks in two passes, and compare model labels with human annotations. |
| [03_Layer1_Task_Affordance_Count](03_Layer1_Task_Affordance_Count/) | Count tasks and calculate the share classified as automation, augmentation, or limited applicability within each occupation. |
| [04_Layer2_Task_Affordance_Weighted](04_Layer2_Task_Affordance_Weighted/) | Calculate task shares with greater weight on core tasks. |
| [05_Layer3_Task_Configuration](05_Layer3_Task_Configuration/) | Combine task shares with the positions of each category’s tasks in the occupation’s importance ranking. |
| [06_Eloundou_Task_Alignment](06_Eloundou_Task_Alignment/) | Align published exposure annotations to O*NET tasks, then construct occupational exposure benchmarks. |
| [07_GenAI_Exposure](07_GenAI_Exposure/) | Merge the task configurations with the exposure benchmarks. |
| [08_Labor_Outcomes](08_Labor_Outcomes/) | Harmonize BLS occupational codes and construct growth measures using employment and wage estimates from 2017–2019 and 2023–2025. |

When rebuilding a stage, update the path in its notebook. The Stage 01 notebook and the Stage 02 classification notebook use `ROOT` for their respective **stage folders**. The other preparation notebooks point to the **repository folder**. Reading the Excel source files requires `openpyxl`.

### Task classification and validation

The [Stage 02 notebooks](02_Task_Data_and_Classification/Code/) run in numerical order. The [classification notebook](02_Task_Data_and_Classification/Code/01_Task_Classification_Procedure.ipynb) runs two passes over the same tasks. Pass 1 provides the labels used in the analysis. Pass 2 measures repeatability. Each pass resumes from its own saved checkpoint in [Output](02_Task_Data_and_Classification/Output/).

To run the classification notebook as written, use Google Colab with `OPENAI_API_KEY` in Colab Secrets and the `openai`, `tqdm`, and `scikit-learn` packages installed. The [human-validation notebook](02_Task_Data_and_Classification/Code/02_Task_Classification_Human_Validation.ipynb) uses the saved provisional labels and the two coder workbooks.

## Data sources

- [O*NET Database, release 30.0](https://www.onetcenter.org/database.html) — occupations, task statements, and task ratings.
- [U.S. Bureau of Labor Statistics, Occupational Employment and Wage Statistics](https://www.bls.gov/oes/tables.htm) — employment and wage estimates.
- [Eloundou et al., GPTs are GPTs](https://github.com/openai/GPTs-are-GPTs) — published task-level GenAI exposure annotations.

## Contact

Udayakumar Routhu · Capitol Technology University · urouthu@captechu.edu
