# IEAP-Series03-RStudio

Team solution to **IEAP Series 03 — Data wrangling and ANOVA** (M1 IEAP, Université de Montpellier, course *Python, R and Git for data analysis*).

We reproduce the main result of Mottet et al. (2017, Fig. 3): movement time as a function of the index of difficulty in patients after a stroke, age-matched controls and young controls. Our report includes data cleaning, a mixed ANOVA, linear regressions by group, a graph and a discussion comparing our results with the scientific article.

The final report is [IEAP-Series03-Rstudio.pdf](IEAP-Series03-Rstudio.pdf).

## Team

| Member | Part of the report |
|:--|:--|
| Martin PIGEAU | 1.1–1.3 Scientific question, library, data reorganization and ANOVA |
| Shunan YIN | 1.4–1.5 Linear regression by group and graph |
| Elouan DELFIN | 1.6–1.7 PDF export and discussion |

The Git workflow, the challenges encountered and the checklist concern the whole team.

## Structure of the repository

```text
IEAP-Series03-Rstudio.qmd     Master document including all sections
IEAP-Series03-Rstudio.pdf     Final report generated with Quarto
README.md                     Project description and instructions
LICENSE                       License information

data/
  Results.txt                 Experimental data

sub-documents/
  1.1-think-before-coding.qmd       Scientific question and hypotheses
  1.2-library.qmd                   ANOVA library
  1.3-data-reorganization.qmd       Data cleaning and ANOVA
  1.4-regression.qmd                Linear regressions by group
  1.5-graph.qmd                     Graph and regression equations
  1.6-export.qmd                    PDF export of the graph
  1.7-discussion.qmd                Comparison with the article

```

We decided to work with a separate Quarto file for each question. All the sub-documents are included in the main file using `{{< include ... >}}`.

This organization made it easier to work on different parts of the assignment. However, the sections must be executed in order because some parts reuse objects created in previous sections. For example, the regression uses the cleaned dataset from section 1.3, and the PDF export uses the graph created in section 1.5.

## How to render the report

Requirements:

- R and RStudio
- Quarto
- R packages: `tidyverse`, `dplyr`, `ggplot2`, `ez`
- Typst support for PDF generation

Steps:

1. Clone the repository.

   ```bash
   git clone https://github.com/ElouanDef/IEAP-Series03-RStudio.git
   ```

2. Open the project folder in RStudio.

3. Install the required packages in the R console if necessary:

   ```r
   install.packages(c("tidyverse", "ez"))
   ```

4. Check that `Results.txt` is located in the `data/` folder.

5. Open `IEAP-Series03-Rstudio.qmd` and click **Render**, or use the terminal:

   ```bash
   quarto render IEAP-Series03-Rstudio.qmd
   ```

The render generates `IEAP-Series03-Rstudio.pdf` and exports the regression graph as a separate PDF in the `figures/` folder.

## Data

`data/Results.txt` was provided on the course Moodle page for Series 03:

https://moodle.umontpellier.fr/mod/folder/view.php?id=1025707

Each row represents one reaching movement. The dataset contains the following columns:

- `GROUP`: experimental group
- `SUBJ`: participant
- `TRIAL`: trial number
- `ORI`: movement orientation
- `DIR`: movement direction
- `ID`: index of difficulty
- `REP`: repetition
- `NbVelPeaks`: number of velocity peaks
- `MovementTime`: movement duration

The incomplete conditions `ID3` and `R3` were removed before the analysis, as explained in section 1.3.

The cleaned data were used to perform a mixed ANOVA and linear regressions for each group.

## Git workflow

`main` is the branch used for the final submission. We divided the assignment between the three team members, and each person worked on separate branches. Once a section was completed, we committed the changes and created Pull Requests to merge them into `main`.

For Shunan and Elouan, it was the first time working on a GitHub project with several sub-documents. We found this method useful because the files were shorter, easier to read and better organized.

The main challenge was coordinating our work because we all had different schedules. We also encountered some problems with file paths and dependencies between R scripts when combining the different sections.

The assignment helped us better understand how to use GitHub for teamwork and how to organize a project with several R and Quarto files.

## Reference

Mottet, D., van Dokkum, L. E. H., Froger, J., Gouaïch, A., & Laffont, I. (2017). Trajectory formation principles are the same after mild or moderate stroke. *PLOS ONE*, 12(3), e0173674.

https://doi.org/10.1371/journal.pone.0173674

## License

See [`LICENSE`](LICENSE).
