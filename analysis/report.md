# Evaluation Report: LLM Performance on Author Name Disambiguation (AND)

## Objective

This report evaluates two large language models (LLMs) for performing the **AND** task for the ambiguous author **Koichi Furukawa**, based on 77 publications from the AMiner-12 dataset.

In this one-shot setup, we gave each model a prompt listing publication metadata and instructed it to group the publications by real-world author identity.

## Experimental Setup

- **Task**: Group publications likely authored by the same person.
- **Data**: 77 publications associated with the name *Koichi Furukawa*.
- **Prompt**: Included publication number, title, co-authors (excluding the ambiguous name), venue, and year.
- **Models Evaluated**:
 - `DeepSeek-R1-Distill-Llama-8B-GGUF`
 - `Gemma-3-12b-it-GGUF`

---

## Observations

### DeepSeek-R1-Distill

- **Grouping**: Assigned publications into two broad clusters.
- **Basis**: Focused loosely on authorship roles and research areas.
- **Shortcomings**:
 - Little explanation of groupings.
 - Did not account for patterns such as recurring co-authors or venue shifts.
 - Mixed unrelated publications, resulting in low alignment with ground truth.

### Gemma-3-12B-it

- **Grouping**: Organized into three clusters with well-defined reasoning.
- **Basis**: Considered co-author recurrence, research themes (e.g., FGCS, ILP), and timeframes.
- **Strengths**:
 - Demonstrated awareness of research phases.
 - Provided clear justifications for most clusters.
- **Limitations**:
 - Misclassified several edge cases.
 - Some overlap between clusters when the context was unclear.

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