# Module 2: The Computational Document

## 1. Controversial Studies & Replication Failures

### Ex. 1: Economics — Reinhart & Rogoff
* **Claim:** Debt to GDP (IPB) ratio $> 90\%$ severely harms economic growth
* **Impact:** Heavily cited by politicians to enforce fiscal austerity (consolidation) policies for years
* **The Flaws:**
  * **Methodological/Data error:** Spreadsheet miscalculations, omitted data, and arbitrary weighting
  * **Transparency issue:** Raw data and calculation sheets were not shared publicly until outside researchers demanded them
* Ideas persisted in policy even after the math was discredited because the code/data were withheld for years

---

### Ex. 2: Neuroscience — Functional MRI
* **Dead Salmon:**
  * A dead salmon showed "brain activity" in an fMRI scanner 
  * **Cause:** High statistical noise + poor calibration + lack of correction for false positives (multiple comparisons problem)
* **Statistical Software Bug:**
  * A flaw in standard statistical software algorithms potentially biased up to 40K articles over 15 years
  * Raw MRI data are rarely archived, making re-analysis impossible without re-running entire experiments
* Methodological bugs in shared tools silently corrupt large bodies of literature

---

### Ex. 3: Crystallography — Chang
* **Claim:** Published structures of membrane proteins involved in bacterial drug resistance
* **Problem:** An inherited analysis script flipped two columns of data, inverting the electron-density map
* **Impact:** 5 papers retracted from top journals 
* Contradictory findings from other labs were suppressed or rejected for years because Chang's prestige made the flawed findings seem authoritative

---
- **Key words:** reproducity experiment, low rate replication, lack of rigor and transparency, strong sociological/productivist pressure

---

### 1.1 What prevents debate on the relevance of studies?
1. Authors do not publish raw data, scripts, or calculation sheets, preventing independent verification
2. Massive datasets are often deleted or not stored, making re-analysis impossible. Data used in the study was not released
3. Sharing raw computational workflows has not historically been standard practice (e.g., economics)
4.  High-profile authors are trusted blindly; contradicting findings from other labs are dismissed as suspicious
5. Thorough scrutiny often only happens under media or public controversy/pressure

---

### 1.2 Possible main causes of errors in studies

* Simple calculation errors (preadsheet bugs, omitted rows/cells, improper weighting)
* Software bugs
* Inadequate data processing or statistics → Failing to correct for noise and false positives 
* Data acquisition (e.g Instrument miscalibration)
* High productivity demands push researchers to publish quickly without rigorous verification
* Reviewers evaluate the manuscript, not the underlying computation

---

### 1.3 Consequences of lack of transparency

1. Unverifiable analyses → Impossible to check or reproduce results without redoing the entire physical experiment (which is often impossible or too expensive)
2. Difficult to rely on others' work → Results that contradict prestigious studies are wrongly dismissed as errors or go unpublished
3. Two studies may seem to contradict each other when both are correct, simply because missing details hide different experimental conditions
4. Harmful real-world decisions → Flawed conclusions are used for years to justify misguided public policies (e.g., austerity) or medical choices.
5. Articles contain less information (no details on calculations, experimental protocols, data analysis, etc.) and are therefore easier to read

---
## 2. Why Is Replication So Difficult?

The inability to reproduce published scientific results stems from a combination of missing information, misuse of computational tools, poor organizational habits, and systemic/cultural practices.

### Core Sources of Replication Difficulties

#### 1. Lack of Information
* **Omission of raw data:** When data collection procedures are secret or vague, external verification is impossible
* **Undocumented choices:** 
  * Selection of experimental protocols and their rationale
  * Which data points were kept, discarded, or filtered, and why
  * The statistical tests chosen and whether their underlying assumptions were met
* Current experimental complexity cannot fit into an article alone; technical details, raw data, and processing steps are condensed into summaries and graphs

#### 2. Computers and Software as Sources of Error
* **Interactive graphical software (point-and-click):** Clicking buttons masks the mathematical and algorithmic steps behind an operation. It leaves no audit trail of what was executed
* **Spreadsheets (e.g., Excel):**
  * Calculation logic is hidden inside cells or complex macros, making errors hard to detect
  * Silent automatic formatting errors(e.g., MARCH1 to March 1st)
  * Spreadsheets are designed for basic accounting/office tasks, not statistical or scientific computing
* The source code is hidden, making it impossible to know precisely what the program does or whether a bug exists in the calculation.
* Poorly mastered software stacks → Relying on unverified, inherited, or home-made scripts without validation.
#### 3. Lack of Strictness and Organization
* **Poor backup habits:** Data lost due to disk failure, account deletion during institutional transfers, or accidental overwrites.
* Absence of version control
* Absence of standard software engineering practices

---

### Best Practices to Prevent Data Loss and Errors

1. Use plain text formats (CSV, Markdown, Org-mode, etc). They remain readable decades later across any operating system
2. Use open-source languages (Python or R) → inspectable, traceable code
3. Use lab notebooks
4. Use version control systems (e.g., Git)
5. Secure sensitive data responsibly by using encryption and access control protocols

---

### 2.1 Main Technical Causes Behind Difficulties in Reproducing Work

* **Lack of documentation on choices made:** Failing to explain protocols, criteria for keeping/dropping data, and statistical procedures
* **Interactive graphical software:** Point-and-click interfaces hide computation details, preventing others from knowing the exact parameters used
* **Computation errors:** Errors in formulas, spreadsheet cell ranges, or unverified analysis scripts
* **Data loss:** Lack of backups, file overwrites, or storage in obsolete/proprietary formats that can no longer be opened

**What is NOT a cause:**
* Open-source software: Open-source tools facilitate reproducibility because their source code can be audited. It is proprietary software that acts as a black box
* Information overload: The issue is not having "too much data to search through" (search engines solve that); the issue is a complete absence of data and processing steps

---

### 2.2 Possible Solutions

* Using a laboratory notebook (computational notebook)
* Code review and continuous integration. Applying software engineering standards to scientific code to catch calculation bugs and verify that code executes reliably on fresh systems.
* Version control systems and automated backups

**What to avoid:**
* Spreadsheets: The calculation logic is concealed behind cells, increasing the likelihood of silent, hard-to-detect errors
* Proprietary formats: Formats locked to commercial software restrict data access and frequently break backward compatibility after updates

---

### 2.3 Most Legitimate / Valid Fears Associated with Open Data (releasing research data publicly)

1. **Sensitive and confidential information (e.g Medical records)**, can harm individuals if published openly. This requires institutional ethics committee oversight, controlled access or anonymization
2. **Limited local resources and storage quotas:** Certain fields generate massive data volumes that exceed standard institutional hosting limits. Specialized public data repositories must be used instead

**Unjustified fears (misconceptions):**
* "Fear of looking foolish if errors are discovered": Science is collaborative and incremental. Publicly sharing work allows peers to find errors and help correct them
* "Fear of someone stealing the work / scooping": In science, publishing your code and data openly (communalism) is the strongest proof of intellectual precedence. Reusers must cite the original author, and methodological/data papers are among the most cited in literature

---
## 3. The Computational Document: Principles

A computational document is a single dynamic document that:
1. **Narrative text** (explanations, context, interpretations in Markdown or Org)
2. **Executable source code** (small progressive fragments in Python, R, etc.)
3. **Execution results** (tables, numerical outputs, and generated figures)

It bridges the gap between the final published article and the entire data analysis workflow behind it.

---

### How It Works
* **Progressive calculation:** Code is broken into small chunks rather than a single long script
* **Persistent state:** An active kernel/session keeps variables in memory from one block to the next
* The author explains the logic and findings in text blocks directly between code executions.
* It can be rendered into HTML or PDF documents (permit to hide raw code or intermediate steps)

---

### 3.1 Commonly Found in a Computational Document

* Commentaries
* Code
* An overview of data (Data tables, summaries, and descriptive statistics)
* Computational results (outputs)
* Hypertext links7
* Images

---

### 3.2 What a Computational Document Allows
* **Inspect the computations:** Anyone can examine the exact code, formulas, and data transformations used
* **Easily re-run the computations:** Results can be recalculated with a single command if the original computational environment is available
* Document the code
* Explain choices
* Use multiple languages