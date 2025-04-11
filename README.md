# Evaluation of LLMs for Author Name Disambiguation (AND)

This repository presents a qualitative analysis of the performance of two large language models (LLMs) in the AND task, using a manually curated dataset for the ambiguous author **Koichi Furukawa**.

## Repository Structure

```
llm-evaluation/
├── prompts/
│   └── koichi_furukawa_prompt.txt         # Prompt used for LLMs
├── responses/
│   ├── deepseek_r1_response.txt           # Output from DeepSeek-R1-Distill
│   └── gemma_3b_response.txt              # Output from Gemma 3B
├── ground_truth/
│   └── koichi_furukawa.xml                # Ground truth labels in XML format        
├── analysis/
│   └── report.md                          # Markdown report with detailed analysis
└── README.md                              # Overview and repository guide
```

## Objective

The goal is to assess whether LLMs can group publications written by the same real-world author — a core challenge in AND. Both models received the same prompt containing metadata from 77 publications, including titles, co-authors, venues, and publication years.

LLMs evaluated:
- `DeepSeek-R1-Distill-Llama-8B`
- `Gemma 3-12B-it`

## Summary of Observations

- Both LLMs attempted to use co-authorship, research themes, and venues to group documents.
- **DeepSeek-R1** provided a basic split of publications, often clustering documents broadly without clear justification.
- **Gemma 3-12B-it** gave more thoughtful groupings and richer explanations, splitting the publications into multiple classes based on project phases and domain-specific knowledge.
- However, neither model matched the ground truth accurately, and both failed to distinguish more subtle disambiguation cases.

## Verdict

Although LLMs showed some ability to identify publication patterns and themes, **they fall short in accurately performing AND task**. Their reasoning lacks the precision required for distinguishing closely related authors, especially in cases of shared collaborators and overlapping venues.

## Full Analysis

A detailed qualitative analysis comparing both LLMs and their strategies can be found in:

`analysis/report.md`

---
