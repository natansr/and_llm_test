# Evaluation of LLMs for Author Name Disambiguation (AND)

This repository presents a structured *one-shot* evaluation of two large language models (LLMs) applied to the AND task. The experiment uses metadata from 77 publications attributed to the ambiguous author **Koichi Furukawa**, extracted from the AMiner-12 dataset.

The objective is to evaluate whether LLMs can perform the AND task — grouping publications written by the same real-world author — using only textual metadata and a carefully designed prompt.


## Repository Structure

```
llm-evaluation/
├── prompts/
│   └── koichi_furukawa_prompt.txt         # Prompt used for LLMs
├── responses/
│   ├── deepseek_r1_response.txt           # Output from DeepSeek-R1-Distill-Llama-8B
│   └── gemma_3b_response.txt              # Output from Gemma 3-12B
├── ground_truth/
│   └── koichi_furukawa.xml                # Ground truth labels in XML format        
├── analysis/
│   └── report.md                          # Markdown report with detailed analysis
│   └── koichi_furukawa_llm_analysis.md                          
│   └── koichi_furukawa_llm_analysis.xls
└── README.md                              # Overview and repository guide
```

## Objective

The goal is to assess whether LLMs can group publications written by the same real-world author — a core challenge in AND. Both models received the same prompt containing metadata from 77 publications, including titles, co-authors, venues, and publication years.

LLMs evaluated:
- [DeepSeek-R1-Distill-Llama-8B](https://lmstudio.ai/model/deepseek-r1-llama-8b)

- [Gemma 3-12B-it](https://lmstudio.ai/model/gemma-3-12b)


## Prompt Structure

Each model received the same instruction, designed to simulate a real-world AND scenario:

> *"Below are publications by different authors with the same name. Group the publications you believe belong to the same author..."*

The metadata provided includes:
- Title
- Co-authors
- Venue
- Year



## Observations

- Both LLMs attempted to use co-authorship, research themes, and venues to group documents.
- **DeepSeek-R1** provided a split of publications, often clustering documents broadly without clear justification.
- **Gemma 3-12B-it** gave more thoughtful groupings and richer explanations, splitting the publications into multiple classes based on project phases and domain-specific knowledge.
However, neither model accurately matched the ground truth, and both failed to distinguish more subtle disambiguation cases.

## Verdict

Although LLMs showed some ability to identify publication patterns and themes, **they fall short in accurately performing AND tasks**. Their reasoning lacks the precision to distinguish closely related authors, especially in shared collaborators and overlapping venues cases.

## Full Analysis

We provide a detailed analysis comparing both LLMs and their strategies. The files below offer a more granular comparison:

- **`analysis/report.md`**: In-depth discussion comparing model strategies and behavior.
- **`analysis/koichi_furukawa_llm_analysis.md`**: Side-by-side cluster vs. ground-truth breakdown.
- **`analysis/koichi_furukawa_llm_analysis.xls`**: Spreadsheet with all predictions and ground-truth labels.


The results summarize the ground truth label for each publication with the cluster predictions made by each LLM.



---
