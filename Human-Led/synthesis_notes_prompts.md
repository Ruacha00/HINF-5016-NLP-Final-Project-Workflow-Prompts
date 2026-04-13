## Synthesis Notes

You are helping me prepare synthesis notes for a literature review in health informatics.

I will provide a completed paper evaluation sheet separately. It contains structured notes for 8 research papers, including their datasets, prediction targets, time-window design, methods, results, contributions, limitations, and validation settings.

Your task is NOT to write the literature review yet.
Your task is to generate synthesis notes that will later be used to write the Discussion and part of the Introduction.

Instructions:

1. Use only the information explicitly available in my evaluation sheet.
2. Do not fabricate missing details.
3. If a conclusion is plausible but not fully supported by my notes, mark it as [VERIFY].
4. Do not organize the output paper-by-paper.
5. Organize the output by themes and cross-paper comparison.
6. Refer to studies by their paper numbers, such as [Paper 1], [Paper 2], etc.
7. Keep the tone analytical, concise, and evidence-based.
8. Focus on synthesis, not summary repetition.

Please generate the synthesis notes using the following structure:

## 1. Theme Grouping

Group the papers into meaningful categories based on dimensions such as:

- model family
- dataset type
- time-window strategy
- prediction horizon
- external validation / cross-dataset generalization
- interpretability / explainability
  For each group, briefly explain why those papers belong together.

## 2. Common Trends

Identify the major patterns that appear across the papers.
Examples may include:

- common modeling choices
- commonly used datasets
- recurring evaluation metrics
- repeated claims about temporal modeling
- patterns in validation practice
  Each trend should mention which papers support it.

## 3. Key Similarities and Differences

Compare the papers across important dimensions.
Focus especially on:

- how they define the prediction task
- how they design the observation window or prediction horizon
- what kinds of input features they use
- what kinds of models they apply
- whether they perform external validation
- whether they discuss clinical usability or interpretability
  This section should highlight both agreements and meaningful contrasts.

## 4. Key Disagreements or Tensions

Identify places where the papers appear to differ in assumptions, design choices, findings, or emphasis.
Examples:

- fixed-window vs dynamic prediction
- single-dataset performance vs external generalization
- accuracy-focused modeling vs interpretability-focused modeling
- structured-only data vs multimodal data
  Only include disagreements that are supported by the evaluation sheet.

## 5. Literature Gaps

Identify the most important gaps in the current literature represented by these papers.
Examples may include:

- limited external validation
- narrow dataset diversity
- weak calibration reporting
- insufficient prospective evaluation
- lack of clinically actionable interpretability
- poor comparison across observation-window choices
  Make the gaps specific to the evidence in my notes.

## 6. Future Directions

Propose promising future directions that logically follow from the papers and the identified gaps.
These should be suitable for the future work discussion in a course literature review.
Do not propose ideas that are unrelated to the reviewed literature.

## 7. Takeaway for Discussion Section

Write 5-8 concise bullet points that could later be turned into a Discussion section.
Each bullet should be high-value, comparative, and directly supported by the reviewed papers.

Additional constraints:

- Do not write full review paragraphs.
- Do not produce an abstract, introduction, or conclusion.
- Do not restate every paper individually.
- Prefer cross-paper synthesis over isolated description.
- If evidence is weak or incomplete, say so explicitly.

Output only the synthesis notes.
