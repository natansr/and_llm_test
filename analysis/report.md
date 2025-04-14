# Evaluation Report

This report evaluates two large language models (LLMs) for performing the **AND** task for the ambiguous author **Koichi Furukawa**, based on 77 publications from the AMiner-12 dataset.

In this one-shot setup, we gave each model a prompt listing publication metadata and instructed it to group the publications by real-world author identity.

## Experimental Setup

- **Task**: Group publications likely authored by the same person.
- **Data**: 77 publications associated with the name *Koichi Furukawa*.
- **Prompt**: Included publication number, title, co-authors (excluding the ambiguous name), venue, and year.
- **Models Evaluated**:
 - `DeepSeek-R1-Distill-Llama-8B`
 - `Gemma 3-12B-it`

---

## Observations

### DeepSeek-R1-Distill

- **Grouping**: Assigned publications into two broad clusters.
- **Basis**: Focused loosely on authorship roles and research areas.
- **Shortcomings**:
 - Little explanation of groupings.
 - There is a low alignment with the ground truth, considering author clustering.

### Gemma-3-12B-it

- **Grouping**: Created three clusters.
- **Basis**: Considered co-author patterns, research topics (e.g., FGCS, ILP), and publication periods.
- **Strengths**:
  - Identified different research phases over time.
  - Gave understandable explanations for most groupings.
- **Limitations**:
  - Made mistakes in cases where information was unclear or borderline.
  - Sometimes grouped similar papers together when there wasn’t enough context to separate them.

---

## Key Takeaways

While both models show the potential to reason over academic metadata, their predictions lacked consistency. They often struggled to resolve ambiguity where co-author sets, or research topics overlapped, and neither model consistently matched the known ground truth.

LLMs treated this task as a semantic grouping problem based on text, which is insufficient for high-precision AND tasks. The absence of structural understanding (e.g., graphs, temporal patterns, co-author networks) limited their performance.

---

## Final Remarks

LLMs offer an intuitive interface for AND and are helpful in low-resource or exploratory settings. However, their lack of structured reasoning, supervision, and scalability makes them unsuitable as standalone methods in production-scale AND systems.

> For a complete breakdown of cluster predictions versus ground truth, see:
>
> - `analysis/koichi_furukawa_llm_analysis.md`
> - `analysis/koichi_furukawa_llm_analysis.xls`