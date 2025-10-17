---
layout: default
title: Autoformalizer with Tool Feedback
---

## Abstract
Autoformalization addresses the scarcity of data for Automated Theorem Proving (ATP) by translating mathematical problems from natural language into formal statements. 
Efforts in recent work shift from directly prompting large language models to training an end-to-end formalizer model from scratch, achieving remarkable advancements. 
However, existing formalizer still struggles to consistently generate valid statements that meet syntactic validity and semantic consistency. 
To address this issue, we propose the Autoformalizer with Tool Feedback (ATF), a novel approach that incorporates syntactic and consistency information as tools into the formalization process. 
By integrating Lean 4 compilers for syntax corrections and employing a multi-LLMs-as-judge approach for consistency validation, the model is able to adaptively refine generated statements according to the tool feedback, enhancing both syntactic validity and semantic consistency. 
The training of ATF involves a cold-start phase on synthetic tool-calling data, an expert iteration phase to improve formalization capabilities, and Direct Preference Optimization to alleviate ineffective revisions. 
Experimental results show that ATF markedly outperforms a range of baseline formalizer models, with its superior performance further validated by human evaluations.
Subsequent analysis reveals that ATF demonstrates excellent inference scaling properties.
Moreover, we open-source Numina-ATF, a dataset containing 750K synthetic formal statements to facilitate advancements in autoformalization and ATP research.

## Overview
Existing formalization approaches face the following issues: 
1. **Lack of Formal Knowledge**. The scarcity of formal language data in the pre-training
corpora limits the foundational models’ ability to inherently understand and generate formal state-
ments effectively. And the formalizer trained on specific versions of formal languages often lacks generalizability across versions.
2. **Rough Consistency Validation**. Previous work relies on LLMs to assess the consistency between informal and formal expressions. However, the reliability of such LLMs-as-judge approach has not been thoroughly validated.

To address these issues, we propose **Autoformalizer with Tool Feedback (ATF)**, which integrates syntactic and consistency information as tools into the formalization process, thereby guiding models to adaptively refine the statements during generation. Specifically, we develop distinct tools for
syntactic validity and semantic consistency. The integration of syntactic information effectively compensates for the model’s unfamiliarity with formal language, allowing adjustments tailored to different language versions. Besides, the incorporation of consistency information helps the model to
identify and address misalignments between informal and formal statements, enhancing semantic
consistency. The training of ATF involves a cold-start phase on synthetic data to teach the model
effective tool usage, an expert iteration phase to enhance the model’s formalization capability and
its ability to effectively implement revisions based on tool feedback, followed by a Direct Prefer-
ence Optimization (DPO) phase to reduce ineffective revisions.

## Key Features

### Tool Integration

We design two distinct tools: **Syntax Check** for syntactic validity and **Consistency Check** for semantic consistency. 

- The syntactic validity tool processes formal statements and returns detailed compilation feedback from Lean 4 compilers. We
employ a pre-check stage and a grouped execution method to ensure more stable and rapid tool
responses.

- The consistency check receives pairs of informal and formal statements and returns consistency results along with concise explanations. We implement a multi-LLMs-as-judge
approach in consistency check, which is benchmarked to effectively discriminate minor inconsistencies in formal statements.

### Progressive Training Pipeline

ATF is trained through a multi-phase process designed to optimize its formalization capabilities:

1. **Cold-Start Phase**: Introduces the model to tool usage with synthetic tool-calling data, establishing foundational formalization skills.
   
2. **Expert Iteration Phase**: Enhances the model's ability to generate valid formal statements through iterative refinement and feedback integration.

3. **Direct Preference Optimization (DPO)**: Reduces ineffective revisions by optimizing the model's decision-making process, ensuring efficient and effective formalization.

## Benchmark Performance

ATF has been rigorously evaluated across multiple benchmarks used in ATP, including two in-distribution datasets: **FormalMath-Lite** and **ProverBench**, along with an out-of-distribution dataset **CombiBench**. It excels in both in-distribution and out-of-distribution scenarios, demonstrating robust generalization capabilities. The model benefits significantly from increased sampling during inference, achieving remarkable pass rates even at higher sampling counts.

We assess both syntactic validity and consistency validity of generated statements using the tools designed above (only syntactically valid statements proceed to consistency evaluation), with further human evaluation as the gold standard.

## Citations
Feel free to adjust the content to better align with your project's specifics and objectives
