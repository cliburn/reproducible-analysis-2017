# Informatics tools for reproducible analysis of large-scale data

- Overview of reproducible research
- Pieces of the problem
  - Experimental design
    - Is there a statistical analysis plan?
      - What is the outcome measure?
      - What are the variables?
      - What is the experimental unit?
      - Is there sufficient power?
      - Is the sample likely to be representative?
    - Is there a data management plan?
      - How will data be captured?
      - Is there any validation?
      - How are data entry errors guarded against?
      - How will samples be labeled and tracked?
      - If there is data transfer, what is the reconciliation process?
  - Data generation
    - Are there clear SOPs for sample processing?
    - Is the staff trained?
    - QC/QA of assays
    - Care to minimize batch effects
    - SOP for data annotation
    - SOP for data upload and storage
  - Data analysis
  - Data stewardship
3. Focus on data analysis
4. Practices
5. Checklists
6. Software tools
7. Training


----


- Overview
  - Reproducible research includes
    - Experimental design
      - Pre-specified plan
    - Data generation
      - Quality of assay data
    - Data analysis
      - From raw data to report
    - Data stewardship
      - FAIR principles for data stewardship
        - Findable
        - Accessible
        - Interoperable
        - Reusable
  - Here the focus is only on the analysis
- Modern data analysis can be complicated
  - Multiple large data sets
    - Genomics, transcriptomics, proteomics, singe cell assays
    - Multiple time points
    - Missing data
  - Complex bioinformatics pipelines
  - Complex statistical models

- Questions
  - Is the analysis reproducible?
  - Is the analysis reasonable?
  - Is the analysis correct?
  - Is the analysis robust?
- Assume
  - Raw data is OK
- Principles
  - Analysis by GUI is hard to replicate
  - Scripting is necessary
- Stages
  - Raw data
  - Bioinformatics processing
  - Intermediate data
  - Statistical analysis
  - Results
  - Report
- Artifacts
  - Data
  - Code
  - Report
- Software tools
  - data
  - code
  - report

  - Begin from the end
    - Start with a report showing statistics, tables and figures
      - [ ] Objective is to replicate the statistics, tables and figures from raw data
    - Can we get the raw data?
      - [ ] Data source is mysterious
      - [ ] Data is missing
      - [ ] Data is incomplete
      - [ ] Data is proprietary
    - Is this the correct raw data?
      - [ ] Duplicate filenames
      - [ ] Multiple versions of "same" file
      - [ ] Data is corrupted
    - Can we find the preprocessing/analysis code?
      - [ ] No code - if analysis done in Excel, Prism, SPSS etc
      - [ ] Multiple versions of code
    - Can we run the preprocessing/analysis code?
      - [ ] Version of programming language
      - [ ] Version of library packages
      - [ ] Other dependencies
      - [ ] OS version
    - Can we understand the preprocessing/analysis code?
      - [ ] Inconsistent data annotation
      - [ ] Inappropriate choice of parameters for processing pipeline
      - [ ] Inappropriate model assumptions
      - [ ] Bugs in code
    - Are the results of analysis robust?
      - [ ] Use "equivalent" data (e.g. bootstrap samples)
      - [ ] Use "equivalent" bioinformatics pipeline
      - [ ] Use "equivalent" statistical model
