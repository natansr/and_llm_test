# LLM-Based Evaluation Report: AND Task 

## Introduction

This report presents the evaluation of two state-of-the-art Large Language Models (LLMs) on the Author Name Disambiguation (AND) task using the publications of the ambiguous author **Koichi Furukawa**. The goal is to assess how well LLMs can group publications from different real-world authors with the same name into clusters that reflect true authorship.

## Models Evaluated

- `DeepSeek-R1-Distill-Llama-8B-GGUF`
- `Gemma-3-12b-it-GGUF`

## Prompt Setup

The prompt included metadata for 77 publications (title, co-authors, venue, and year) and instructed the model to group publications into classes based on likely authorship.

### Prompt Template Example

```text
Below are publications by different authors with the same name. Group the publications you believe belong to the same author. List the publication numbers grouped by class (e.g., Class 1: [1, 4, 5], Class 2: [2, 3]):
...
```

## Observations

### DeepSeek-R1-Distill-Llama-8B

- **Approach**: Focused mostly on co-authors and general themes but lacked deeper contextual analysis.
- **Output**: Provided two broad clusters with minimal rationale and relied heavily on vague similarity notions.
- **Strengths**: Very fast response and readable format.
- **Limitations**: Mixed documents from different authors and failed to leverage rich contextual relationships.

### Gemma-3-12b-it

- **Approach**: Presented a detailed breakdown of clusters with supporting reasoning.
- **Output**: Provided three classes aligning reasonably well with themes in the ground truth (FGCS logic programming, ILP, general topics).
- **Strengths**: Strong contextual understanding, good use of venues, years, and recurring co-authors.
- **Limitations**: Some misclassifications and overlapping clusters due to uncertainty in ambiguous entries.

## Verdict

- **Gemma-3-12b-it** outperforms DeepSeek in this task by a notable margin due to its structured rationale, domain alignment, and use of historical co-author data.
- LLMs show promise for the AND task but still suffer from limitations in consistency and precision across ambiguous or overlapping topics.
- Compared to our proposed GCN+GHAC framework, LLMs lack robustness, scalability, and precision control.

## Recommendation

The LLM responses and prompt examples are available in the `/analysis` directory. 
