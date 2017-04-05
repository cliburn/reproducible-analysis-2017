# Tools for Reproducible Analysis with Large-scale Data

### Can we replicate the results we published last year?

Cliburn Chan and Jeremy Gresham

---


## Overview: Replicating a study is hard but tools are improving

- Research is becoming more complex
- Pieces of reproducible *research*
- Focus on reproducible *analysis*
- Tools for reproducible analysis

---


## Research is becoming more complex

|  |  |
| ------:| -----|
| Single discipline   |  → Multiple disciplines |
| Single assay type |  → Multiple assay types |
| Single center    | → Multiple centers|
| GUI-driven analysis | → Script-driven analysis |

---


### Single discipline → multiple discipline

- Cancer immunotherapy study
  - Surgeon
  - Oncologist
  - Cancer biologist
  - Immunologist
  - Platform experts
  - Bioinformatician
  - Biostatistician

---


### Single assay type → Multiple assay types

- Cancer immunotherapy study
  - Whole exome or targeted sequencing for mutation load and neoantigens
  - RNA-seq for expression and pathway analysis
  - TCR sequencing for clonal diversity
  - Flow or mass cytometry for immunophenotyping and functional characterization
  - Multiplexed ELISA for cytokines, angiogenic factors, tumor growth factors
  - IHC for tumor architecture

---


### Single center → Multiple centers

- Often necessary due to get adequate power
  - Sample processing
  - Sample shipping
  - Need for reconciliation
  - Data capture, standards and annotation

---


### GUI-driven analysis → Script-driven analysis

- Manual analysis is either already impossible or moving there rapidly
  - Whole exome sequencing - 180,000 exons or 3,000,000 base pairs
  - RNA-seq millions of reads, 20,000 genes
  - TCR sequencing - estimated theoretical number of different TCRs > 10<sup>15</sup>
  - Cytometry - CyTOF and BD Symphony theoretically capable of 50 parameters per cell (currently probably ~ 30 parameters)
  - Multiplexed ELISA - 10s - 100s of soluble factors
  - IHC - Up to 10 distinct antibodies
- Need for script-driven computational processing and analysis

---


## Pieces of Reproducible Research

- Experimental design
- Data generation
- Data stewardship
- <font color=red>Data analysis</font>

---


### Experimental design

- Is there a statistical analysis plan?
- Is there a sample management plan?
- Is there a data management plan?

---


#### Is there a statistical analysis plan?

- What is the study objective?
- What is the outcome?
- What are the variables?
- What is the study design?
- Is there sufficient power?
- Will the samples be representative of the target population?

----


#### Is there a sample management plan?

- Shipping SOP
- Transfer and reconciliation SOP
- Sample labeling
- Sample tracking
- Use of LIMS

---


#### Is there a data management plan?

- Where will raw data be uploaded/stored?
- What variables will be recorded?
- What data standards will be used for annotation?
- Where will it be recorded?
  - Often REDCap for clinical data
  - Often the Wild West for laboratory data summaries
- How are data entry errors handled?
  - Automated validation checks
  - Double-entry book-keeping
  - Review by supervisor
- Are data modifications tracked/logged?

---


### Data generation

- Assay QA/QC/reproducibility
  - Consideration of batch effects
  - Consideration of lot effects
  - These can sometimes be adjusted for by statistical modeling, but the batch/lot data must be available to do so
- Operator training
- Use of written SOPs for sample processing, performance of assay, and recording of data

---


### Data stewardship

- FAIR principles
  - Findable
  - Accessible
  - Inter-operable
  - Reusable
- See [FAIR guidelines](https://www.force11.org/group/fairgroup/fairprinciples)

---


### Data analysis

- Some scenarios for re-analysis
  - Someone else wants to replicate your results
  - You need to update the data and re-run the analysis
  - You suspect there is a bug in your script and want to re-run the analysis after fixing it

- Can you do it?
  - Can we find and reuse the data?
  - Can we recreate the analysis environment?
  - Can we find and use the analysis scripts?
  - Can we replicate the report/poster/paper?

  ---


#### Can we find and reuse the data?

- Does the data even exist anymore?
- If exists, can you identify the exact data used?
- Can you link the laboratory and clinical data?

---


####Practices and tools for data

- Keep raw data
- Hash the data (e.g. MD5 or SHA-1) to check for corruption
- Annotate data using standard vocabularies
- Make a copy of all data - ideally in a public repository
  - NCI: Genomic Data Commons
  - NIAID: ImmPort

- Example: [ReFlow](https://test.reflowproject.org)

----


#### Can we recreate the analysis environment?

- You used Windows XP but you whole lab is now a Mac-only shop
- You used proprietary software A from Vendor X to preprocess the ELISA data (Vendor X went bankrupt 2 years ago)
- You ran the analysis with R 3.0.4 with packages X (version 1.23), Y (version 2.34) and Z (version 3.45)

#### Practices and tools for analytic environment

- Prefer open-source tools
- Use reproducible **virtual machines** or **containers** environments to run your analysis

- Example: Using Docker (Jeremy's talk)

---


#### Can we find and use the analysis scripts?

- If you did the analysis using a GUI (e.g. Excel, Prism), your analysis is almost certainly unless you (or your analyst) has a perfect memory
  - Perfect memory does not exist
- Can you find the script(s) used for analysis?
- Are you sure that is the exact version of the script used?
- Can you still run your script (see previous slide)

---


#### Practices and tools for analytic scripts

- Don't do the final analysis using a GUI
- Use version control for scripts (e.g. `hg`, `git`)
- Use a version control service (e.g. `GitHub`, `Bitbucket`')
- Commit early and often
- Use informative log messages when commuting

- Example: Using [GitHub](https://github.com/cliburn/reproducible-analysis-2017

----


#### Can we replicate the report/poster/paper?

- Can you replicate the report/poster/paper when
  - you need to modify some data
  - you suspect that is a bug in your script
  - you want to switch one pipeline stage for another
- If your report/poster/paper was done by copy/paste from Excel or Prism etc, you are most likely in for a world of pain

---


#### Practices and tools for document generation

- Have a script to generate all results, tables and statistical plots
- If feasible, generate the entire document programmatically
using `literate programming`
  - Literate programming combines documentation with code-generated artifacts (e.g. p-values, tables, figures)

- Example: Literate programming with `beaker`
