# Evaluation of LLMs for Author Name Disambiguation (AND)

This repository presents a qualitative analysis of the performance of two large language models (LLMs) in the Author Name Disambiguation (AND) task, using a manually curated dataset for the ambiguous author **Koichi Furukawa**.

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

## Experimental Setup

We selected the author *Koichi Furukawa* with 77 publications. The XML ground truth groups the publications into classes (authors). The task given to both LLMs was to group the publications into clusters (classes), assuming each cluster corresponds to a distinct real-world author.

LLMs evaluated:
- **DeepSeek-R1-Distill-Llama-8B**
- **Gemma 3-12B-it**

Both models were prompted with the same instructions and publication metadata (titles, venues, co-authors, and years).

## Qualitative Analysis

### DeepSeek-R1-Distill-Llama-8B

- **Strategy**: Grouped based on relevance to Furukawa’s research areas and co-authorship patterns.
- **Pros**:
  - Demonstrated contextual awareness by identifying core publications.
  - Attempted to separate collaborative works from core authorship.
- **Cons**:
  - Classification was relatively coarse, dividing publications into just 2 classes.
  - Did not leverage venue/year consistency deeply.
  - Included ambiguous groupings like Class 1 and also in Class 2.

### Gemma 3-12B-it

- **Strategy**: Clustered by project involvement (e.g., FGCS), time period, research domain, and co-author networks.
- **Pros**:
  - Rich, well-structured explanation of reasoning.
  - Demonstrated strong semantic understanding of research themes.
  - Identified important project phases (e.g., ILP, FGCS).
  - Grouped publications across 3 detailed classes, reflecting deeper insight.
- **Cons**:
  - Occasionally over-explained borderline cases without decisively placing them.

## Verdict

While both models demonstrated reasonable understanding of the AND task, **Gemma 3-12B-it** produced a more nuanced and semantically rich classification. It showed better clustering consistency based on co-author networks, project involvement, and academic venues.

DeepSeek was competent, but less precise in capturing fine-grained distinctions.

## Recommendation

These results suggest that although LLMs show promising abilities in AND task based on textual metadata, further refinement and structure-aware processing (like graphs or embeddings) is still essential for higher reliability in AND tasks.

