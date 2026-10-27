# Module 3: Replicable Analysis

## 1. What is a replicable analysis?

### 1.1 Traditional vs. Replicable Analysis

* **Traditional**
  * Focus primarily on the final results and conclusions
  * Only provides a brief methodological summary of the calculations and procedures used
  * **Limitation:** The underlying computations, decision points, and raw scripts remain hidden

* **Replicable**
  * An analysis where the brief methodological summary is replaced by the complete code used for all calculations, embedded in a computational document.
  * It must include a detailed explanation docs about the decisions, assumptions, and filters made at each step of the pipeline.

---

### 1.2 Goals

1. Easier to redo (Maintainability): If the input data updates, expands, or changes in the future, the entire analysis can be re-run automatically to generate updated results without starting from scratch

2. Easier to modify (Adaptability): If new research questions arise or alternative hypotheses need testing, the existing workflow and code parameters can be tweaked and reused immediately

3. Easier to inspect and verify: Reviewers, readers, and the authors themselves can audit every calculation step and methodological choice, making the final conclusions verifiable and far more credible
