# Section-by-Section Writing Prompts

## Literature Review: Early ICU Mortality Prediction Using Time-Series Data

---

> **How to use these prompts:**
> Each prompt is self-contained. Before submitting a prompt, paste in the referenced materials
> from `paper_evaluation_template.md` or `synthesis_notes.md` where indicated by `[PASTE: ...]`.
> Submit one section at a time. Review and revise before moving to the next section.

---

## Section 1 — Methods

**Submit order: First**

```
You are helping me write the Methods section of a literature review paper formatted for
AMIA Annual Symposium submission. The paper topic is:

  "Early ICU Mortality Prediction Using Time-Series Data:
   Multi-Window Modeling and Cross-Dataset Generalization Evaluation"

Your task is to write the Methods section only. This section should describe:
1. The databases searched (PubMed via MeSH, PubMed free text, Google Scholar)
2. The search strings used for each database
3. The inclusion and exclusion criteria
4. The number of papers ultimately included (8 papers)

I will give you the search strategy information：

## Search Strategy Log

| Database           | Search String                                                                                                                                                                                                                                                         | Results Count | Notes |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------- | ----- |
| PubMed (MeSH)      | ("Intensive Care Units"[MeSH]) AND<br /> ("Hospital Mortality"[MeSH] OR "Mortality"[MeSH]) AND <br />("Machine Learning"[MeSH] OR "Deep Learning"[MeSH]) AND<br /> ("time series"[tiab] OR temporal[tiab] OR longitudinal[tiab] OR sequential[tiab] OR dynamic[tiab]) | 53            |       |
| PubMed (Free text) | ("ICU" OR "intensive care") AND<br />  ("mortality prediction") AND<br />  ("time series" OR "temporal" OR "observation window") AND<br />  ("deep learning" OR "LSTM" OR "transformer" OR "machine learning")                                                        | 47            |       |
| Google Scholar     | ICU mortality prediction time series deep learning                                                                                                                                                                                                                    | about 42,200  |       |

### Inclusion Criteria

- [X] Related to ICU mortality prediction
- [X] Uses time-series / temporal clinical data
- [X] Employs machine learning or deep learning methods
- [X] English language
- [X] Peer-reviewed journal, conference paper, or preprint

### Exclusion Criteria

- [X] Not focused on ICU setting
- [X] Uses only static/snapshot data (no temporal modeling)
- [X] Review articles (unless foundational)
- [X] Non-English

Instructions:
- Write in third person, past tense, formal academic prose.
- Use a PRISMA-style narrative: describe the search, then the screening, then the final inclusion.
- Do NOT invent numbers (e.g., how many papers were excluded at each step) that are not in my notes.
  If a number is missing, write "papers were screened according to the following criteria" without
  fabricating counts.
- Length: approximately 150–220 words.
- Do not add section subheadings.
- Do not include any information beyond what I have provided above.
```

---

## Section 2 — Related Work / Results

**Submit order: Second**

```
You are helping me write the Related Work (Results) section of a course literature review paper
formatted for AMIA Annual Symposium submission. The topic is:

  "Early ICU Mortality Prediction Using Time-Series Data:
   Multi-Window Modeling and Cross-Dataset Generalization Evaluation"

I have reviewed 8 papers. I will provide (A) my synthesis notes and (B) the key metrics for each
paper. Your task is to write a thematic narrative of the reviewed literature — do NOT summarize
papers one by one.

(A) Synthesis notes — Theme Grouping, Common Trends, and Key Similarities and Differences:

## 1. Theme Grouping

### Dynamic or real-time risk prediction

- **[Paper 2], [Paper 6], [Paper 7], and [Paper 8]** can be grouped together because they frame mortality prediction as an updating process during ICU stay rather than a single admission-time estimate. [Paper 2] and [Paper 7] explicitly predict short-term death in the next 24 hours in real time, [Paper 6] evaluates arbitrary real-time windows during ICU stay, and [Paper 8] reports dynamic performance as cumulative data accrue over the first 48 hours.

### Explicit multi-window comparison studies

- **[Paper 1], [Paper 4], [Paper 6], and [Paper 8]** belong together because they explicitly compare alternative temporal windows or repeated timepoints rather than using one fixed early window. However, their window definitions differ: day-wise simple vs cumulative windows in [Paper 1], peri-admission clinical checkpoints in [Paper 4], 4/8/24-hour or random-time windows in [Paper 6], and cumulative 12/24/48-hour performance in [Paper 8]. This group is central for discussing whether prognostic value changes with additional ICU time.

### Fixed early-window models

- **[Paper 3] and [Paper 5]** are the clearest fixed-window studies because both use the first 48 hours after ICU admission as the observation period and do not compare alternative window lengths. They are useful for contrasting with the dynamic and multi-window papers, since they prioritize early standardized prediction over time-varying reassessment.

### External validation and cross-dataset generalization emphasis

- **[Paper 2], [Paper 5], and [Paper 7]** form the strongest external-generalization group because they train on one source and test on separate external datasets. **[Paper 3]** partially fits this theme because it evaluates on both MIMIC-III and MIMIC-IV, but the notes explicitly distinguish this from strict train-on-one/test-on-another transport validation. By contrast, **[Paper 1], [Paper 4], [Paper 6], and [Paper 8]** remain single-dataset studies.

### Explainability or clinical transparency emphasis

- **[Paper 4] and [Paper 5]** belong together because interpretability is not just incidental but part of the paper's stated contribution. [Paper 4] proposes a model-agnostic explainability framework with probability-based variable interpretation, while [Paper 5] uses timestep-level and variable-level attention to support clinical interpretability. Other papers discuss calibration or model design, but the notes do not present explainability as equally central.

### Broad heterogeneous input streams vs curated routine-variable models

- **[Paper 8]** stands apart because it models nearly 5,000 event types without manual variable selection or curation. In contrast, **[Paper 1], [Paper 2], [Paper 5], and [Paper 7]** use more compact, curated, or routinely available variable sets, while **[Paper 3]** sits between these poles by fusing multiple structured types (labs, vitals, prescriptions) in a more organized architecture. This grouping highlights a feature-scope tension across the literature.

## 2. Common Trends

- **Structured ICU EHR data dominate across all eight papers.** The reviewed studies rely on combinations of vitals, labs, demographics, medications/prescriptions, interventions, or other structured charted variables; none of the notes describe the use of clinical notes or other unstructured modalities.
- **Temporal framing is treated as a core design issue, but implemented in different ways.** Some studies use fixed early windows ([Paper 3], [Paper 5]), some compare multiple windows or timepoints ([Paper 1], [Paper 4], [Paper 6], [Paper 8]), and others move to continuous real-time updating ([Paper 2], [Paper 7]). This suggests broad agreement that mortality risk should be modeled as time-dependent rather than purely static.
- **Performance typically improves over time or with richer temporal context when time comparisons are made.** [Paper 1] reports best discrimination on day 2 cumulative modeling and decline afterward; [Paper 4] reports stronger later-window F1; [Paper 8] shows AUROC increasing from 12 to 48 hours with diminishing returns. This pattern supports the idea that additional observation time can improve prediction, while also raising questions about how much clinical lead time remains.
- **AUROC is the dominant evaluation metric.** Several papers either do not report AUPRC at all or note that AUROC is the headline metric even when AUPRC is available. Calibration reporting is much less common, with clearer attention in [Paper 2] and [Paper 7] than in most of the rest of the set.
- **Machine learning models usually outperform traditional clinical scores or simpler baselines when such comparisons are included.** This is explicit against APACHE-II or logistic regression in [Paper 1], against NEWS in [Paper 2], against multiple temporal baselines in [Paper 3], against logistic regression and simpler RNNs in [Paper 5], against SAPS II and other severity scores in [Paper 6], against comparator models plus NEWS/MEWS in [Paper 7], and against SAPS II and OASIS in [Paper 8]. [Paper 4] is the main exception because its main comparison is between machine learning models rather than against conventional severity scores.
- **Validation practice is uneven.** Stronger transport-oriented evaluation appears in [Paper 2], [Paper 5], and [Paper 7], partial cross-dataset robustness appears in [Paper 3], and the remaining studies rely on internal validation within one dataset. External validation is therefore present, but not yet standard across the reviewed literature.
- **Missing-data handling is ubiquitous but methodologically inconsistent.** The papers use multiple imputation ([Paper 1]), median plus forward filling ([Paper 2]), zero filling for baseline comparisons ([Paper 3]), carry-forward or predefined normal values ([Paper 5]), learned end-to-end imputation ([Paper 7]), or explicit missingness/event tokenization ([Paper 8]). This suggests broad recognition that temporal ICU data are incomplete, but no common strategy across studies.

## 3. Key Similarities and Differences

### Prediction task definition

- Most papers predict **ICU or in-hospital mortality**, but they do not define the task identically. [Paper 2] and [Paper 7] focus on **short-term next-24-hour death risk** during ICU stay, [Paper 4] focuses on **72-hour ICU mortality**, [Paper 3] and [Paper 5] use the **first 48 hours** to predict later mortality, [Paper 6] predicts mortality in real time throughout stay, [Paper 8] performs dynamic survival prediction over the first 48 hours, and [Paper 1] predicts ICU discharge vital status using data from the first 1-5 ICU days. These are related but not interchangeable task formulations.

### Observation window and prediction horizon design

- The literature splits sharply between **fixed-window early prediction** and **dynamic updating**. [Paper 3] and [Paper 5] standardize on the first 48 hours; [Paper 2] and [Paper 7] instead update continuously in real time; [Paper 1], [Paper 4], [Paper 6], and [Paper 8] explicitly examine how performance changes across windows or timepoints. This means the papers are not only comparing models; they are also comparing different underlying notions of when a mortality prediction should be made.

### Input feature design

- There is substantial agreement on using **structured vitals and laboratory data**, but the breadth of features varies. [Paper 2] and [Paper 7] emphasize compact sets of routinely available variables plus temporal recency features; [Paper 5] uses a curated 67-variable set including interventions and derived clinical scores; [Paper 3] fuses vitals, labs, and prescriptions; [Paper 4] includes demographics, comorbidities, treatments, biochemical variables, and hospital characteristics; [Paper 1] relies on daily summaries of a smaller structured feature set; [Paper 8] is the main outlier, using broad tokenized chart, lab, and output streams without manual variable selection.

### Model families

- The model landscape is heterogeneous. Classical tree-based or boosting approaches are prominent in [Paper 1], [Paper 4], and [Paper 6], and remain competitive or preferred in structured-windowed settings. Deep sequential or attention-based models dominate [Paper 3], [Paper 5], and [Paper 8]. [Paper 2] and [Paper 7] move toward hybrid systems by combining deep temporal modeling with ensemble learning or learned imputation. Overall, there is no single dominant family across all task designs.

### External validation and transportability

- External validation is one of the clearest points of differentiation. [Paper 2] and [Paper 7] provide the broadest geographic or dataset coverage, [Paper 5] shows one-way transfer from eICU to MIMIC-III, and [Paper 3] provides dual-dataset evidence but not strict transport validation. In contrast, the explicitly multi-window papers in this set ([Paper 1], [Paper 4], [Paper 6], [Paper 8]) do not provide cross-dataset validation, so the window-comparison literature and the transportability literature only partially overlap.

### Clinical usability and interpretability

- Clinical usability is discussed unevenly. [Paper 4] explicitly aligns windows with admission and reassessment decision points and adds model-agnostic explanation, while [Paper 5] makes interpretability a core design goal through variable- and timestep-level attention. [Paper 2] and [Paper 7] contribute more on calibration, decision curves, or alert efficiency than on transparent feature attribution. [Paper 1], [Paper 6], and [Paper 8] read more as performance-oriented benchmark studies in the notes.

(B) Key metrics per paper (for embedding specific numbers in the text):
## Paper 1: Optimal intensive care outcome prediction over time using machine learning

- **AUROC:** Best day 1 model `DeepNN` = 0.883 (±0.008); logistic regression with same predictors = 0.846 (±0.010); APACHE-II baseline = 0.836 (±0.007); best overall performance on day 2 cumulative model = 0.895 (±0.008)
- **AUPRC:** Not reported
- **Other:** Predictive ability declined after day 2; machine learning consistently outperformed logistic regression across days 1–5

---

## Paper 2: Real-time machine learning model to predict short-term mortality in critically ill patients

- **AUROC:** Internal validation = 0.964 (95% CI 0.963–0.965); external validation = 0.890 (MIMIC-III), 0.886 (eICU-CRD), 0.870 (AmsterdamUMCdb)
- **AUPRC:** Reported in the paper, but headline emphasis is on AUROC
- **Other:** Outperformed NEWS in all cohorts; NEWS AUROC was 0.866 internally and 0.746, 0.798, 0.819 on MIMIC-III, eICU-CRD, and AmsterdamUMCdb respectively. Calibration was also better than NEWS based on expected calibration error

---

## Paper 3: TERTIAN — Clinical Endpoint Prediction in ICU via Time-Aware Transformer-Based Hierarchical Attention Network

- **AUROC:** MIMIC-III `TERTIAN` = 0.9506 (±0.0039); MIMIC-IV `TERTIAN` = 0.8361 (±0.0093)
- **AUPRC:** Not reported
- **Other:** MIMIC-III precision 0.9689, F1 0.9457, recall 0.9236; MIMIC-IV precision 0.8680, F1 0.8666, recall 0.8688. Outperformed ConCare, GRASP, GRUD, TimeLine, IseeU, and AttDMM

---

## Paper 4: Toward transparent clinical decision support in the ICU — multi-window, model-agnostic explainability for 72-h mortality prediction

- **AUROC:** Not emphasized/reported as a main headline metric in the main results tables
- **AUPRC:** Not reported
- **Other:** Random Forest F1-scores ≈ 0.83, 0.92, 0.93 across windows A, B, C (Table 3); recalls 0.86, 0.93, 0.94. Global test-set F1-scores of 0.92, 0.95, 0.96 for windows A, B, C respectively (Table 5)

---

## Paper 5: A Clinically Practical and Interpretable Deep Model for ICU Mortality Prediction with External Validation

- **AUROC:** Training / validation / test = 0.912 / 0.899 / 0.855; external validation on MIMIC-III = 0.855
- **AUPRC:** Not reported
- **Other:** Outperformed logistic regression and simpler RNN baselines; includes qualitative attention-based interpretability analysis

---

## Paper 6: Real-time mortality prediction in the Intensive Care Unit

- **AUROC:** Gradient Boosting = 0.927 (first-24-hour prediction), 0.920 (real-time random-time windows); logistic regression = 0.892 (real-time setting)
- **AUPRC:** Reported for the real-time experiment, though AUROC is the headline metric
- **Other:** Gradient Boosting substantially outperformed SAPS II on the same first-24-hour data (0.927 vs. 0.809)

---

## Paper 7: Unlocking the potential of real-time ICU mortality prediction — redefining risk assessment with continuous data recovery

- **AUROC:** 0.957 (internal held-out eICU centers), 0.968 (MIMIC-IV), 0.932 (SICdb)
- **AUPRC:** Not highlighted as the main headline metric
- **Other:** RealMIP improved NEWS and MEWS when used as an imputation engine; strong calibration, decision-curve performance, and temporal alert efficiency reported

---

## Paper 8: Dynamic survival prediction in intensive care units from heterogeneous time series without variable selection or curation

- **AUROC:** 0.77 after 12 hours; 0.8463 (95% CI 0.8411–0.8513) after 48 hours
- **AUPRC:** Not emphasized; paper reports AUROC-centric dynamic comparisons
- **Other:** Outperformed SAPS II (≈0.72) and OASIS (≈0.76) at 24 hours; predictive performance increased over first 48 hours with diminishing returns

Instructions:
- Organize the section around 3–4 thematic paragraphs, such as:
    (1) temporal window design strategies,
    (2) model families and architectures,
    (3) external validation and generalizability,
    (4) interpretability and clinical usability.
- Within each paragraph, compare papers against each other rather than describing them in isolation.
- Cite papers as [1] through [8] in the order they appear in my evaluation template.
- Embed specific AUROC values or other numbers where they strengthen a comparison.
- Do NOT use bullet lists — write in connected prose paragraphs.
- Do NOT fabricate any claim not supported by my notes.
- If a detail is marked [VERIFY] in my notes, omit it or flag it with "(reported in some studies)".
- Length: approximately 600–800 words.
```

---

## Section 3 — Discussion

**Submit order: Third**

```
You are helping me write the Discussion section of a course literature review paper formatted for
AMIA Annual Symposium submission. The topic is:

  "Early ICU Mortality Prediction Using Time-Series Data:
   Multi-Window Modeling and Cross-Dataset Generalization Evaluation"

I will provide my pre-written synthesis notes covering disagreements, literature gaps, future
directions, and key takeaways. Your task is to convert these structured notes into a
well-argued Discussion section in academic prose.

Here are my synthesis notes:
## 4. Key Disagreements or Tensions

- **Fixed-window early prediction vs continuous dynamic prediction.** [Paper 3] and [Paper 5] assume a standardized early observation period is appropriate, whereas [Paper 2], [Paper 6], [Paper 7], and [Paper 8] assume that mortality risk should be updated as new data arrive. This is not just a technical difference; it reflects competing views of when prediction is most clinically useful.
- **Accuracy gains from later windows vs clinical actionability of earlier warning.** [Paper 1], [Paper 4], and [Paper 8] all suggest improved performance with more accumulated temporal information, but [Paper 4] explicitly notes that later windows are closer to the outcome and therefore less useful for early intervention. The literature therefore contains a real tension between maximizing discrimination and preserving usable lead time.
- **Curated routine-variable models vs minimally curated heterogeneous streams.** [Paper 2], [Paper 5], and [Paper 7] are closer to clinically practical compact-variable designs, while [Paper 8] intentionally avoids variable selection and manual curation. [Paper 1] also uses a relatively constrained daily-summary feature set. These studies disagree implicitly on whether transportable ICU prediction should prioritize parsimony and routine availability or maximal feature inclusiveness.
- **Performance-focused modeling vs transparency-focused modeling.** [Paper 4] and [Paper 5] foreground interpretability, whereas [Paper 7] explicitly increases modeling complexity through an end-to-end generative imputation framework, and [Paper 2] emphasizes strong cross-dataset performance with calibration improvement. The notes therefore suggest a tension between transparent models for decision support and increasingly complex pipelines for performance and robustness.
- **Single-dataset benchmarking vs transport validation.** [Paper 1], [Paper 4], [Paper 6], and [Paper 8] provide useful methodological comparisons within one dataset, but [Paper 2], [Paper 5], and [Paper 7] place stronger emphasis on whether models survive transfer across datasets or health systems. [Paper 3] sits between these positions, since it uses two datasets but not a full transport design.

## 5. Literature Gaps

- **True external validation is still not routine, especially for multi-window studies.** The clearest external transport evidence comes from [Paper 2], [Paper 5], and [Paper 7], while the papers that most directly compare windows ([Paper 1], [Paper 4], [Paper 6], [Paper 8]) remain internally validated only. A major gap is therefore the lack of studies that jointly test window strategy and cross-dataset generalization.
- **The literature does not yet provide a clean cross-paper answer on the best observation-window strategy.** Multi-window studies exist, but they operationalize windows differently: daily cumulative windows, peri-admission decision windows, arbitrary real-time windows, or cumulative 12/24/48-hour comparisons. Because these designs are not standardized, it is difficult to infer whether one temporal framing is consistently superior across datasets.
- **Calibration and decision-analytic reporting are limited relative to discrimination reporting.** AUROC is widely emphasized, but explicit calibration improvement is clearer in [Paper 2] and [Paper 7] than elsewhere, and AUPRC is frequently absent or not highlighted despite class imbalance. This limits assessment of whether high-discrimination models are also well-behaved for deployment.
- **Clinically actionable interpretability is uneven.** Only [Paper 4] and [Paper 5] make explanation a central contribution in the notes. The rest may be clinically motivated, but the evaluation sheet does not show a comparable emphasis on transparent decision support.
- **Dataset diversity remains limited despite some recent improvement.** MIMIC and eICU dominate the evidence base, with broader coverage added mainly by CCHIC ([Paper 1]), AmsterdamUMCdb and SNUH ([Paper 2]), and SICdb ([Paper 7]). This concentration may constrain conclusions about transportability across different care settings.
- **Handling of missing temporal data is important but not systematically compared.** The papers use markedly different imputation or missingness strategies, yet only [Paper 7] makes missing-data recovery itself a central modeling innovation. There is little evidence in the notes of head-to-head evaluation showing when simpler imputation is sufficient and when learned recovery materially changes generalization.
- **Prospective evaluation appears limited in this set.** [Paper 2] explicitly states that prospective validation is still required, and [Paper 7] is described as retrospective. The notes for the remaining papers do not report prospective testing, so real-world workflow validation appears underdeveloped in the reviewed literature. [VERIFY]

## 6. Future Directions

- **Combine temporal-window comparison with external transport testing.** A strong next step would be to evaluate fixed, cumulative, peri-admission, and continuous-update designs within the same study and then validate them across external datasets, since current work tends to emphasize one axis or the other.
- **Standardize reporting beyond AUROC.** Future studies should report calibration, AUPRC, and decision-oriented measures more consistently so that dynamic ICU models can be compared on clinical usefulness rather than discrimination alone. This direction follows directly from the metric imbalance across the reviewed papers.
- **Develop interpretable real-time models with strong external validation.** The current set shows a split between explainability-focused work ([Paper 4], [Paper 5]) and strong transport-oriented real-time work ([Paper 2], [Paper 7]). A logical future direction is to bring these strengths together rather than treating them as separate priorities.
- **Evaluate missing-data strategies explicitly across datasets and model families.** Since ICU time-series incompleteness is handled in many different ways across the set, future work should compare conventional imputation, missingness-aware encoding, and learned recovery under matched validation settings.
- **Test whether compact routine-variable models or broader heterogeneous event-stream models generalize better.** The reviewed papers support both philosophies, but the notes do not yet show a direct comparison under common external-validation conditions. That makes feature-scope comparison a relevant future research question.
- **Move toward prospective or deployment-oriented validation.** This is especially relevant for the real-time models, since retrospective accuracy does not by itself show whether alerts would be timely, trusted, or operationally useful in ICU workflows. [VERIFY]

## 7. Takeaway for Discussion Section

- The reviewed literature agrees that ICU mortality prediction benefits from temporal modeling, but it does **not** agree on a single best temporal design; fixed early windows, explicit multi-window comparison, and continuous updating are all actively used.
- Studies that compare windows generally show better performance with more temporal information, but this creates a trade-off between predictive strength and early clinical actionability.
- External validation is a major differentiator: strong transport evidence appears in [Paper 2], [Paper 5], and [Paper 7], whereas most explicit multi-window studies remain single-dataset.
- The field still relies heavily on structured EHR variables and AUROC-based evaluation, leaving multimodal modeling, calibration-focused assessment, and richer deployment metrics less developed in this set.
- More complex deep or hybrid models do not remove the need for clinical transparency; interpretability is treated as a primary contribution in only a minority of the reviewed papers.
- Feature engineering philosophy remains unsettled: some papers favor compact routine-variable models for practicality, while others argue that broader minimally curated event streams can be predictive without manual selection.
- A particularly important gap is the lack of studies that are simultaneously multi-window, externally validated, calibration-aware, and explicitly interpretable.

Instructions:
- Structure the Discussion as follows:
    Paragraph 1 — Major findings: what the literature agrees on
    Paragraph 2 — Key tensions and disagreements across papers
    Paragraph 3 — Literature gaps (what is missing or underdeveloped)
    Paragraph 4 — Future directions that follow directly from the gaps
- Each paragraph must have a clear topic sentence.
- Use logical connectives to build arguments (e.g., "However,", "This tension suggests that...",
  "A notable gap is...", "Building on this,").
- Do NOT simply expand bullet points into sentences — synthesize and reason across them.
- Cite papers as [1] through [8].
- Items marked [VERIFY] in my notes should be written as "prospective evaluation appears limited
  in the reviewed literature" or similar hedged language — do not state them as confirmed facts.
- Do not introduce any claims not supported by my synthesis notes.
- Length: approximately 700–900 words.
```

---

## Section 4 — Introduction

**Submit order: Fourth (write after Discussion is finalized)**

```
You are helping me write the Introduction section of a course literature review paper formatted
for AMIA Annual Symposium submission. The topic is:

  "Early ICU Mortality Prediction Using Time-Series Data:
   Multi-Window Modeling and Cross-Dataset Generalization Evaluation"

Before writing, I will give you (A) the clinical background context and (B) the key gaps
identified in my literature review, so the Introduction can set up the review's purpose precisely.

(A) Clinical background (use this to motivate the problem):
ICU patients face high mortality risk that varies dynamically during their stay. Early and
accurate mortality prediction can support clinical decision-making, resource allocation, and
treatment escalation. Machine learning models trained on electronic health record time-series
data have shown promise, but the field lacks consensus on optimal temporal observation windows
and cross-dataset generalizability remains a practical concern.

(B) Literature gaps that motivate this review:

## 5. Literature Gaps

- **True external validation is still not routine, especially for multi-window studies.** The clearest external transport evidence comes from [Paper 2], [Paper 5], and [Paper 7], while the papers that most directly compare windows ([Paper 1], [Paper 4], [Paper 6], [Paper 8]) remain internally validated only. A major gap is therefore the lack of studies that jointly test window strategy and cross-dataset generalization.
- **The literature does not yet provide a clean cross-paper answer on the best observation-window strategy.** Multi-window studies exist, but they operationalize windows differently: daily cumulative windows, peri-admission decision windows, arbitrary real-time windows, or cumulative 12/24/48-hour comparisons. Because these designs are not standardized, it is difficult to infer whether one temporal framing is consistently superior across datasets.
- **Calibration and decision-analytic reporting are limited relative to discrimination reporting.** AUROC is widely emphasized, but explicit calibration improvement is clearer in [Paper 2] and [Paper 7] than elsewhere, and AUPRC is frequently absent or not highlighted despite class imbalance. This limits assessment of whether high-discrimination models are also well-behaved for deployment.
- **Clinically actionable interpretability is uneven.** Only [Paper 4] and [Paper 5] make explanation a central contribution in the notes. The rest may be clinically motivated, but the evaluation sheet does not show a comparable emphasis on transparent decision support.
- **Dataset diversity remains limited despite some recent improvement.** MIMIC and eICU dominate the evidence base, with broader coverage added mainly by CCHIC ([Paper 1]), AmsterdamUMCdb and SNUH ([Paper 2]), and SICdb ([Paper 7]). This concentration may constrain conclusions about transportability across different care settings.
- **Handling of missing temporal data is important but not systematically compared.** The papers use markedly different imputation or missingness strategies, yet only [Paper 7] makes missing-data recovery itself a central modeling innovation. There is little evidence in the notes of head-to-head evaluation showing when simpler imputation is sufficient and when learned recovery materially changes generalization.
- **Prospective evaluation appears limited in this set.** [Paper 2] explicitly states that prospective validation is still required, and [Paper 7] is described as retrospective. The notes for the remaining papers do not report prospective testing, so real-world workflow validation appears underdeveloped in the reviewed literature. [VERIFY]

Instructions:
- Structure the Introduction as follows:
    Paragraph 1 — Clinical motivation: why ICU mortality prediction matters
    Paragraph 2 — Current state of the field: what has been done (1–2 sentences only, broad strokes)
    Paragraph 3 — Gaps that remain: draw directly from my Section 5 notes above
    Final sentence — State the purpose of this review explicitly:
      "This review synthesizes eight recent studies on temporal machine learning models for ICU
       mortality prediction, with a focus on observation window design and cross-dataset
       generalization."
- Do NOT over-claim about the field — only reference what is supported by my notes.
- Do NOT introduce specific paper citations in the Introduction (save them for Related Work).
- Length: approximately 250–320 words.
- Tone: formal, third person, present tense for general statements.
```

---

## Section 5 — Conclusion

**Submit order: Fifth (write after Discussion is finalized)**

```
You are helping me write the Conclusion section of a short AMIA-format course literature review.
The topic is:

  "Early ICU Mortality Prediction Using Time-Series Data:
   Multi-Window Modeling and Cross-Dataset Generalization Evaluation"

I will provide (A) the key takeaway bullet points from my synthesis and (B) the final paragraph
of my Discussion section, so the Conclusion logically closes the paper without repetition.

(A) Key takeaways:

##  Takeaway for Discussion Section

- The reviewed literature agrees that ICU mortality prediction benefits from temporal modeling, but it does **not** agree on a single best temporal design; fixed early windows, explicit multi-window comparison, and continuous updating are all actively used.
- Studies that compare windows generally show better performance with more temporal information, but this creates a trade-off between predictive strength and early clinical actionability.
- External validation is a major differentiator: strong transport evidence appears in [Paper 2], [Paper 5], and [Paper 7], whereas most explicit multi-window studies remain single-dataset.
- The field still relies heavily on structured EHR variables and AUROC-based evaluation, leaving multimodal modeling, calibration-focused assessment, and richer deployment metrics less developed in this set.
- More complex deep or hybrid models do not remove the need for clinical transparency; interpretability is treated as a primary contribution in only a minority of the reviewed papers.
- Feature engineering philosophy remains unsettled: some papers favor compact routine-variable models for practicality, while others argue that broader minimally curated event streams can be predictive without manual selection.
- A particularly important gap is the lack of studies that are simultaneously multi-window, externally validated, calibration-aware, and explicitly interpretable.

(B) Final paragraph of my Discussion:

Building on these gaps, several future directions follow directly from the current state of the evidence. Most importantly, future studies should jointly evaluate temporal design and external transport rather than treating them as separate research questions. A particularly informative next step would be a common framework that compares fixed early windows, cumulative windows, peri-admission formulations, and continuous updating within the same study, followed by validation across external datasets. Such a design would directly address the current inability to disentangle window strategy from dataset-specific performance. Building on this, reporting standards should expand beyond AUROC to include calibration, AUPRC, and decision-oriented measures more consistently, so that models are compared on clinical usefulness rather than discrimination alone. The review also suggests a need to bring together strengths that currently appear separated across papers: interpretable models are often not the ones with the strongest transport emphasis, while externally validated real-time systems are often more complex and less explicitly explanation-centered [2,4,5,7]. Future work should therefore aim for interpretable real-time models that also demonstrate robust external performance. Similarly, missing-data strategies should be evaluated explicitly across datasets and model families under matched validation conditions, since the present literature does not yet clarify when conventional imputation, missingness-aware representations, or learned recovery offer meaningful advantages. Another priority is direct comparison of compact routine-variable models against broader heterogeneous event-stream approaches under common external-validation settings, which would help resolve whether parsimony or inclusiveness is more conducive to transportable ICU prediction. More broadly, prospective or deployment-oriented validation appears to be an important next step, particularly for dynamic models, because retrospective performance alone does not establish whether alerts would arrive early enough, be trusted by clinicians, or fit ICU workflow. Overall, the most important unmet need appears to be for studies that are simultaneously multi-window, externally validated, calibration-aware, and explicitly interpretable.

Instructions:
- Write a single paragraph of 100–150 words.
- Summarize the 2–3 most important cross-cutting findings from the takeaways above.
- End with one forward-looking sentence about what the field needs next.
- Do NOT introduce any new claims not already established in the paper.
- Do NOT simply restate the Discussion — bring closure with a higher-level framing.
- Do NOT use bullet points.
```

---

## Section 6 — Abstract

**Submit order: Last**

```
You are helping me write the Abstract for a course literature review paper formatted for AMIA
Annual Symposium submission. The topic is:

  "Early ICU Mortality Prediction Using Time-Series Data:
   Multi-Window Modeling and Cross-Dataset Generalization Evaluation"

AMIA abstract requirements:
- Length: 125–150 words (strict upper limit)
- Format: a single paragraph, written in italics in LaTeX (\textit{...})
- No citations in the abstract

I will provide the opening sentences of each major section so you can derive the abstract
faithfully from the paper itself.

Introduction: Patients in the intensive care unit (ICU) are at substantial risk of deterioration and death, and that risk changes dynamically over the course of admission. Early mortality prediction is therefore clinically important because it may support timely treatment escalation, triage, and resource allocation in a setting where decisions are highly time-sensitive.

Methods: A structured literature search was conducted to identify studies on early intensive care unit (ICU) mortality prediction using time-series clinical data. Three sources were searched: PubMed using Medical Subject Headings (MeSH), PubMed using free-text terms, and Google Scholar.

Related Work: Across the reviewed literature, the most consistent point of variation is not simply model choice but temporal framing. The studies split between fixed early-window prediction, explicit multi-window comparison, and fully dynamic real-time updating, reflecting different assumptions about when ICU mortality risk should be estimated.

Discussion: The reviewed literature converges on several broad conclusions about early ICU mortality prediction from time-series data. First, the studies consistently suggest that temporal information matters: whether through fixed early windows, cumulative multi-window designs, or continuously updated models, incorporating change over time is treated as central rather than optional in mortality prediction [1–8].

Conclusion: Across the reviewed studies, the clearest conclusion is that temporal information matters for ICU mortality prediction, but the literature does not support a single best strategy for using it. Fixed early windows, explicit multi-window comparisons, and continuously updated models all remain viable approaches, reflecting an unresolved trade-off between stronger performance from longer observation and the need for timely clinical action. A second cross-cutting finding is that evidence of generalizability remains uneven: although a subset of studies demonstrates meaningful external validation, many multi-window investigations are still confined to single datasets, limiting confidence in transportability. More broadly, the field continues to rely primarily on structured EHR inputs and discrimination-focused evaluation, while calibration, interpretability, and deployment-oriented assessment receive less consistent emphasis. Moving forward, the field needs integrated studies that compare temporal strategies within a common framework while also demonstrating external validity, calibration, and clinical interpretability.

Instructions:
- Structure: Background (1–2 sentences) → Objective (1 sentence) → Methods (1 sentence) →
  Main findings (2–3 sentences) → Conclusion (1 sentence).
- Strict word count: 125–150 words. Count carefully.
- Do NOT include any claim not present in the sections I provided.
- Output the abstract text only, ready to paste inside \textit{} in LaTeX.
```

---

## Quick Reference — Section Order and Word Targets

| Order | Section      | Source Material                      | Target Length |
| ----- | ------------ | ------------------------------------ | ------------- |
| 1     | Methods      | Search Strategy Log + criteria       | ~150–220 w   |
| 2     | Related Work | synthesis_notes §1–3 + key metrics | ~600–800 w   |
| 3     | Discussion   | synthesis_notes §4–7               | ~700–900 w   |
| 4     | Introduction | synthesis_notes §5 + background     | ~250–320 w   |
| 5     | Conclusion   | synthesis_notes §7 + Discussion end | ~100–150 w   |
| 6     | Abstract     | All finalized section opening lines  | 125–150 w    |

**Constraint to add to every prompt (copy-paste as needed):**

> Only use information explicitly present in the materials I have provided.
> Do not fabricate citations, statistics, or claims.
> If evidence is weak or absent for a point, omit it or hedge explicitly.
