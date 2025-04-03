# ProjectPlan 
**Group 46: Coco Dai and Isaiah Ketedji**  

## 1. Project Goal
Our overarching goal is to investigate trends, patterns, and potential risk factors in Chicago’s restaurant food inspection data. Specifically, we aim to examine whether certain facility characteristics (such as facility type, neighborhood, or ZIP code), time periods (e.g., seasonal variations, major events), or risk classifications (e.g., different risk categories) correlate with higher rates of inspection failures. This goal reflects our broader interest in public health outcomes and compliance with food safety regulations within a major urban area. By integrating two disparate datasets—one in CSV format and one in JSON format—and carrying out an end-to-end data curation process (acquisition, cleaning, profiling, analysis, and reproducible workflow creation), we also intend to showcase our mastery of data curation concepts taught in this course.  

We have several smaller subgoals aligned with each step of the data-curation lifecycle:  
1. **Data Acquisition**: Gather and document the data sources using scripts and checksums where possible to ensure transparency and reproducibility.  
2. **Data Integration**: Merge CSV and JSON data sources in a cohesive manner that properly aligns facility identifiers and relevant inspection fields.  
3. **Data Profiling and Cleaning**: Assess the quality of the data (completeness, consistency, outliers) and resolve issues like missing values, duplicated records, or inconsistent location information.  
4. **Analysis and Visualization**: Explore how different factors—such as facility type, risk category, neighborhood, or inspection date—impact the likelihood of failing an inspection.  
5. **Workflow Automation**: Automate the entire pipeline using a workflow tool (e.g., Snakemake) so that future analyses can be easily repeated, updated, or extended.  

By achieving the above objectives, we hope not only to highlight any persistent trends or anomalies in Chicago’s food inspection system, but also to demonstrate the rigor and depth of the data curation process itself.  

## 2. Research Questions
Below are the primary research questions guiding our investigation. Each question emerges from our broader project goal and will be addressed via data analysis and visualization:  

1. **Inspection Outcome Patterns**  
   - *Question*: Which facility types (e.g., fast-food restaurants, full-service restaurants, grocery stores with hot bars, etc.) exhibit the highest rates of failed inspections?  
   - *Rationale*: Differentiating failure rates by facility type can highlight segments of the food industry that need additional support, oversight, or training in food safety protocols.  

2. **Risk Classification and Failure Rates**  
   - *Question*: Are higher-risk facilities (as indicated by Chicago’s defined risk categories) more likely to fail inspections or incur severe violations?  
   - *Rationale*: Intuitively, one might assume that facilities designated with a higher risk category—perhaps because they handle raw or potentially hazardous foods—would show a higher failure rate. Testing this assumption could help tailor public health interventions.  

3. **Temporal Trends**  
   - *Question*: How do inspection outcomes change across months or years? Do we see clusters of failures around certain seasons or during major events (e.g., local festivals, public health policy changes)?  
   - *Rationale*: Identifying potential temporal patterns can help allocate inspection resources more effectively and inform policy decisions (e.g., scheduling more frequent inspections ahead of large city events).  

4. **Geographic and Demographic Factors**  
   - *Question*: Are there specific ZIP codes or neighborhoods within Chicago that show a consistently higher rate of severe violations or inspection failures?  
   - *Rationale*: Geographic insights can help public health authorities identify vulnerable communities or areas with limited resources, prompting targeted programs (e.g., food safety workshops or subsidized facility improvements).  

We expect to refine or adjust these research questions as we delve deeper into the data. Additional follow-up questions may emerge if we discover interesting anomalies, such as spikes in violation rates for particular months or outliers in certain facility categories.  


## 3. Team Roles and Responsibilities 
Our team consists of two members (Group 46): **Coco Dai** and **Isaiah Ketedji**. Each member has specific responsibilities covering all the major components required by the final-project guidelines, from acquisition to archival. We outline these responsibilities below in a more detailed manner, ensuring each step of the curation lifecycle is addressed.

### 3.1 Coco Dai  
1. **Data Acquisition & Licensing Compliance**  
   - Investigate and document the source of the CSV (“chicago restaurant food inspection.csv”) and the JSON (“food-inspection-history.json”) data.  
   - Write Python scripts (or equivalent) to download/access these files (if they are externally hosted) or to load them securely from local storage if they are already provided.  
   - Verify the authenticity and integrity of the data through checksums (e.g., using SHA-256) and keep a record of them in a `.txt` or `.md` file.  
   - Ensure compliance with any stated licenses or terms of use; for instance, if the data is shared under a specific open license, record it in the project documentation.

2. **Data Integration (Schema Design & Merging)**  
   - Develop a strategy to unify the CSV and JSON datasets, determining how records will be mapped (e.g., by using a License Number or a composite key like Facility Name + Address).  
   - Identify overlaps or discrepancies in fields (e.g., date formats, enumerations of risk levels) and propose solutions (e.g., standardizing dates to ISO 8601).  
   - Implement the integration using Python (pandas, or other libraries) to produce a consolidated dataset for further analysis.

3. **GitHub Repository & Documentation**  
   - Create the private repository `is477-sp25-Group-46` in the `illinois-data-curation` organization.  
   - Configure repository settings, add project collaborators, and maintain a consistent folder structure (e.g., `scripts/`, `data/`, `docs/`, `results/`).  
   - Document each step in the repository’s `Wiki` or `README` files as necessary, and keep track of changes using branches and pull requests.

4. **Metadata Creation & Licenses**  
   - Prepare metadata that describes the integrated dataset (e.g., a data dictionary or codebook).  
   - Document how each column was derived or cleaned.  
   - Include license information for any original scripts or software produced by the team, ensuring we meet open-source or educational use guidelines.

### 3.2 Isaiah Ketedji  
1. **Data Profiling & Quality Assessment**  
   - Use pandas or similar tools to explore column statistics (missing values, data ranges, duplicates).  
   - Identify any anomalies or outliers (e.g., negative ZIP codes, incorrectly formatted dates) and log them in an “issues” file or relevant project documentation.  
   - Evaluate data completeness and consistency, especially for fields critical to analysis such as inspection dates, results, risk categories, and geographic identifiers.

2. **Data Cleaning**  
   - Develop and implement cleaning routines (in Python, or OpenRefine recipes) to standardize city names, unify ZIP code formats, handle missing or null entries, and reconcile risk-level categories.  
   - Keep a detailed “cleaning recipe” that itemizes each transformation—e.g., trimming whitespace, normalizing strings to Title Case, merging duplicate facility listings.  
   - Confirm that final cleaned outputs are thoroughly tested by re-checking row counts, verifying that no critical records have been inadvertently dropped, etc.

3. **Analysis & Visualization**  
   - Conduct exploratory data analysis to address the research questions. This may include computing summary statistics (counts of pass/fail by risk category, distribution of facility types, violation frequency).  
   - Create visualizations (e.g., bar charts, line charts, distribution plots, or maps if feasible) that illustrate major findings. Tools may include Matplotlib, Seaborn, Plotly, or GeoPandas for spatial data.  
   - Interpret these visualizations in the project documentation, explaining how they relate to the research questions.

4. **Workflow Automation (Snakemake)**  
   - Set up a `Snakefile` (or an equivalent workflow tool) to define tasks from data acquisition through final analysis. Each rule will include inputs (e.g., raw CSV), outputs (cleaned CSV, integrated dataset, figures), and scripts that perform transformations.  
   - Ensure that environment specifications (e.g., `requirements.txt`) are included so the workflow is reproducible on other machines.  
   - Test the entire pipeline end-to-end, confirming that a single command (e.g., `snakemake all`) can replicate the final results from scratch.

### 3.3 Shared Responsibilities  
Both Coco and Isaiah will collaborate on:  
- **Documentation & Reporting**: Writing and reviewing project deliverables (ProjectPlan, StatusReport, and final `README.md`).  
- **Interim & Final Submissions**: Tagging releases (`project-plan`, `status-report`, `final-project`), uploading archives (e.g., Zenodo), and ensuring final submission compliance.  
- **Peer Review**: Checking each other’s code, logic, and analyses, providing feedback for improvements and consistency.  
- **Licensing & Citation**: Ensuring all data and software used are cited accurately following guidelines (APA, DataCite, etc.).  

By dividing responsibilities in this manner, we make certain that each aspect of the final-project guidelines—data acquisition, integration, cleaning, analysis, workflow, reproducibility, archival, citations, and metadata—receives dedicated attention.


  

## 4. Datasets 
We have identified two datasets that complement each other, both focusing on Chicago food inspections but in different formats:  

1. **Chicago Restaurant Food Inspection (CSV)**  
   - *Filename*: `chicago restaurant food inspection.csv`  
   - *Format*: CSV (Comma-Separated Values)  
   - *Description*: This dataset provides tabular records of Chicago restaurant inspections, including fields like `Inspection ID`, `Facility Type`, `Risk Classification`, `Address`, `Inspection Date`, `Result` (pass/fail), `Violation Codes`, and possibly additional descriptors. Typically, it’s large, containing numerous rows (thousands or more).  
   - *Relevance*: Offers structured data that is straightforward to parse and analyze with Python’s pandas library.  

2. **Food Inspection History (JSON)**  
   - *Filename*: `food-inspection-history.json`  
   - *Format*: JSON (JavaScript Object Notation)  
   - *Description*: Stores inspection logs in a nested format, potentially providing more detailed comments, narratives by inspectors, or historical re-check data. The JSON structure might also capture multiple inspection events per facility, or track changes over time for the same facility.  
   - *Relevance*: Since JSON differs structurally from CSV, this dataset allows us to practice data integration from multiple file formats. It may provide additional context (such as free-text notes, outcome detail) that is not present in the CSV file.  

Both datasets appear to meet the licensing and usage requirements for educational projects. We will confirm their respective open licenses (or terms of use) as part of our documentation. They also satisfy the project requirement of using two different data sources in distinct formats (CSV and JSON).  

## 5. Timeline   

Our project timeline covers every major milestone from initial setup through final submission. Each milestone aligns with the tasks required by the project guidelines in `final-project.md`.  

1. **Week 1 (Mar 27 – Apr 2): Project Setup and Planning**  
   - *Create Private Repository*: Coco will set up the private GitHub repository `is477-sp25-Group-46` and invite Isaiah as a collaborator.  
   - *Project Plan Development*: Both team members collaborate to write the `ProjectPlan.md`, ensuring it meets the 1000-word requirement and rubric criteria (project goal, research questions, roles, datasets, timeline).  
   - *Submit Plan*: Tag the repository with `project-plan` release and post the link on Canvas.  

2. **Week 2 (Apr 3 – Apr 9): Data Acquisition and Preliminary Profiling**  
   - *Data Download & Checksum Scripts*: Coco writes Python scripts to download or otherwise load `chicago restaurant food inspection.csv` and `food-inspection-history.json`. She will verify data integrity and store checksums in a separate file.  
   - *Initial Profiling*: Isaiah uses pandas to load both datasets and compute basic statistics (row counts, column uniqueness, missing data percentages). He documents any immediate red flags, such as obviously incorrect ZIP codes or suspicious date ranges.  

3. **Week 3 (Apr 10 – Apr 16): Data Integration and Cleaning**  
   - *Integration Logic*: Coco designs the merge logic, identifying a key column (e.g., `License Number` or a combination of `Address` + `Facility Name`) to unify records from the CSV and JSON sources.  
   - *Cleaning Operations*: Isaiah focuses on data cleaning by implementing python scripts (and, if applicable, OpenRefine transformations) to correct city names, unify date formats, and handle missing or corrupted fields. He will also keep a record of all cleaning steps in a JSON or text “recipe” file for reproducibility.  

4. **Week 4 (Apr 17 – Apr 23): Exploratory Data Analysis and Visualization**  
   - *Initial Analysis*: Isaiah runs descriptive analyses on the cleaned and merged data, looking for distributions of inspection outcomes, risk categories, and facility types. He identifies interesting relationships or outliers worth deeper investigation.  
   - *Visualization Prototypes*: Isaiah also creates basic plots—such as bar charts of pass vs. fail rates by facility type, or timelines indicating changes in inspection outcomes over the years. Coco will review these plots for clarity and consistency with the project’s goals.  

5. **Week 5 (Apr 24 – Apr 30): Workflow Automation**  
   - *Snakemake Workflow*: Isaiah composes a `Snakefile` that captures tasks from the prior weeks. This will automate reading the data from the relevant sources, merging them, cleaning them, and producing final analyses/visualizations.  
   - *Documentation and Testing*: Both Coco and Isaiah test the workflow on different machines (if possible) to ensure reproducibility. They will document the environment dependencies in a `requirements.txt` (or a conda environment file) to facilitate easy setup.  

6. **Week 6 (May 1 – May 7): Final Submission and Documentation**  
   - *Comprehensive Analysis*: The team refines final analyses, potentially adding geographic mappings (e.g., using ZIP code shapefiles), more advanced visualizations, or short text analytics on the inspection comments if time permits.  
   - *Project Report & Archival*: Coco and Isaiah co-author a `README.md` that describes the entire project in detail (introduction, methodology, findings, references). They also prepare the archival record, such as a Zenodo DOI or other persistent identifier, and ensure that it is referenced in the final submission.  
   - *Final Tag & Submit*: Tag the repository with `final-project`, include the link to the archival record, and submit via Canvas.  

Throughout each phase, we will maintain open communication, provide progress updates in the GitHub issues or pull requests, and remain flexible about adjusting tasks if we encounter unforeseen data or analysis challenges.  
