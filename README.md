# Overview
This project focused on improving how job postings are analyzed to extract a specific detail: the minimum years of work experience required for a given education level. 
This information is often buried in complex, varied, and sometimes informal wording that traditional keyword-based hiring software struggles to interpret. 
Our client, a startup company that connects job seekers with relevant opportunities, needed a faster, lower-cost, and more accurate solution.

The team first used a large, advanced AI model to read and label a carefully chosen set of job postings. These labels captured 
nuanced combinations of education and experience requirements that existing systems missed. A smaller, task-specific AI model was then trained on these labeled examples using a 
method known as knowledge distillation. This approach transferred the capabilities of the larger model into the smaller one, resulting in a tool that could run quickly and inexpensively without relying on costly third-party AI services.

The final system was able to handle multiple requirement options, informal phrasing, and complex sentence structures while meeting strict speed and accuracy 
requirements. Although performance varied with rare or ambiguous cases, the approach met the client’s needs and can be extended to extract other valuable details from job postings in the future.

The techniques demonstrated in this project—combining high-quality label generation from a large language model with a fine-tuned, efficient model for local deployment—can be applied well beyond job postings. 
Similar approaches could be used in intelligence gathering, where vast amounts of unstructured text must be mined for specific signals such as threat indicators, organizational relationships, or shifts in sentiment. 
They could also be adapted for contract analysis, regulatory compliance checks, customer feedback mining, or any scenario where nuanced, context-dependent information must be extracted 
quickly and cost-effectively. By distilling the capabilities of a powerful model into a lightweight, targeted system, organizations can gain fast, accurate, 
and scalable extraction tools without the cost and latency of relying on large external AI services.

# Notes
:heavy_check_mark: Business Goal: Enable faster and more accurate matching of job seekers to positions by improving extraction of education and experience requirements.

:heavy_check_mark: Challenge: Traditional parsing tools fail when requirements are expressed in varied, nuanced, or informal language, or when multiple options are presented.

:heavy_check_mark: Data: Dataset of 1.2M job postings, with a balanced 50k sample used for model training.

:heavy_check_mark: Method:

  * Used Google’s Gemini LLM to produce high-quality training labels.
  * Combined these with parser-generated labels for improved accuracy.
  * Applied regex-based text extraction to preserve key requirement details.
  * Fine-tuned a lightweight DistilRoBERTa model for multi-label, multi-class classification.

:heavy_check_mark: Performance:

  * Hamming Accuracy: 99%; Exact Match (0/1) Accuracy: 66%.
  * Precision: ~79%, Recall: ~80% at the chosen threshold.
  * Inference time: ~288 ms for a single posting; ~19 ms in batch.

:heavy_check_mark: Advantages:

  * Runs locally, eliminating recurring API costs.
  * Meets cost, speed, and performance requirements.
  * Flexible enough to handle other extraction tasks in the future.

:heavy_check_mark: Limitations:

  * Reduced accuracy for rare or unseen education/experience combinations.
  * Occasional confusion between minimum requirements and preferences.
  * Dependent on label quality and text extraction precision.
