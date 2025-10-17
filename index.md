---
layout: default
title: Autoformalizer with Tool Feedback
---

## Overview

Autoformalization is a critical aspect of ATP, tasked with converting mathematical problems articulated in natural language into formal statements that can be rigorously proven within formal systems like Lean or Isabelle. ATF tackles the persistent challenges of syntactic validity and semantic consistency by embedding sophisticated tools directly into the formalization workflow, thereby ensuring higher accuracy and reliability.

## Key Features

### Tool Integration

ATF seamlessly integrates Lean 4 compilers to automatically correct syntax errors and employs a multi-LLMs-as-judge approach to validate semantic consistency. This dual-tool strategy ensures that the generated statements are not only syntactically valid but also semantically aligned with the original mathematical problems.

### Adaptive Refinement

By leveraging tool feedback, ATF dynamically refines the generated formal statements, adapting to errors and inconsistencies in real-time. This iterative refinement process significantly enhances both syntactic validity and semantic consistency, setting a new standard in autoformalization.

### Progressive Training Pipeline

ATF is trained through a multi-phase process designed to optimize its formalization capabilities:

1. **Cold-Start Phase**: Introduces the model to tool usage with synthetic tool-calling data, establishing foundational formalization skills.
   
2. **Expert Iteration Phase**: Enhances the model's ability to generate valid formal statements through iterative refinement and feedback integration.

3. **Direct Preference Optimization (DPO)**: Reduces ineffective revisions by optimizing the model's decision-making process, ensuring efficient and effective formalization.

### Open-Source Dataset

We are proud to release Numina-ATF, a comprehensive dataset containing 750K synthetic formal statements derived from competition-level mathematical queries. This dataset serves as a valuable resource for researchers and developers, facilitating further advancements in the fields of autoformalization and ATP.

## Performance

ATF has been rigorously evaluated across multiple benchmarks, consistently outperforming existing formalizers. It excels in both in-distribution and out-of-distribution scenarios, demonstrating robust generalization capabilities. The model benefits significantly from increased sampling during inference, achieving remarkable pass rates even at higher sampling counts.

## Get Involved

Explore our repository to access the ATF model, dataset, and detailed documentation. We welcome contributions, discussions, and collaborations from the community to further advance the field of autoformalization and ATP. Whether you're a researcher, developer, or enthusiast, your involvement is invaluable to us.

## Contact

For inquiries, collaborations, or feedback, please reach out to us via [GitHub Issues](https://github.com/qguo-create/Autoformalizer-with-Tool-Feedback/issues) or contact the project maintainers directly. We look forward to hearing from you and working together to push the boundaries of automated theorem proving.

---

Feel free to adjust the content to better align with your project's specifics and objectives
