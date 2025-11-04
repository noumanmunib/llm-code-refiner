LLM Code Refiner
Bridging the correctness-quality trade-off in Large Language Model-generated code through a hybrid two-stage pipeline.

Paper
License
Python

Overview
LLM-generated code often exhibits a fundamental trade-off: high correctness but poor quality (via few-shot prompting) or high quality but low correctness (via fine-tuning/refinement). This repository presents a solution through a hybrid Generate-and-Refine pipeline that decouples these concerns:

Stage 1: Code Generation → Prioritize correctness with few-shot prompting (Pass@1 ≥ 0.80)

Stage 2: Code Refinement → Improve quality without sacrificing correctness

We evaluate three distinct refinement strategies:

LLM-based Refiner: Semantic understanding for holistic refactoring

Rule-based Refiner: Deterministic automated transformations

RAG Refiner: Retrieval-Augmented Generation for exemplar-guided refinement

Research Paper
Bridging Correctness and Quality in LLM Code Generation: A Hybrid Generate-and-Refine Pipeline

Authors: Munib, N.
Status: Extended Abstract submitted to ICSE 2026
Year: 2025

📄 Read the Extended Abstract

Key Features
✅ Modular Architecture - Easy substitution of refinement strategies
✅ Correctness Validation - Test case re-execution after each refinement step
✅ Multiple Quality Metrics - SonarQube integration (bugs, code smells, maintainability)
✅ Empirical Evaluation - APPS dataset with 480 programming problems
✅ Reproducible - Open-source code and detailed documentation

Quick Start
Prerequisites
bash
Python 3.8+
pip install -r requirements.txt
Installation
bash
git clone https://github.com/yourusername/llm-code-refiner.git
cd llm-code-refiner
pip install -r requirements.txt
Basic Usage
python
from pipeline import GenerateAndRefinePipeline

# Initialize pipeline
pipeline = GenerateAndRefinePipeline(
    llm_model="gpt-4",
    refinement_strategy="rag"  # Options: "llm", "rule-based", "rag"
)

# Generate and refine code
problem = "Write a function to find the longest palindromic substring"
result = pipeline.run(problem)

print(f"Generated Code:\n{result['generated_code']}")
print(f"Refined Code:\n{result['refined_code']}")
print(f"Correctness Score: {result['correctness']}")
print(f"Quality Score: {result['quality_metrics']}")
Architecture
Pipeline Flow
text
Input Problem
    ↓
[Stage 1] Generate Code (Few-Shot LLM)
    ↓
[Validation] Test Case Execution
    ↓
     ├─→ [Stage 2a] LLM Refiner
     ├─→ [Stage 2b] Rule-Based Refiner
     └─→ [Stage 2c] RAG Refiner
    ↓
[Validation] Test Case Re-execution
    ↓
Output: High-Correctness, High-Quality Code
Evaluation
Dataset
APPS Dataset: 480 programming problems

Difficulty Levels: Easy, Medium, Hard

Language: Python

Metrics
Metric	Description
Pass@1	Correctness: % of solutions passing all test cases
Bugs	SonarQube: Critical and major bugs detected
Code Smells	Code quality issues (unused variables, duplication, etc.)
Maintainability Index	Overall code maintainability score
Results
(To be populated upon full paper completion)

Refinement Strategies
1. LLM-Based Refiner
Uses semantic understanding to identify and fix quality issues while preserving correctness.

python
strategy = "llm"
# Uses prompt-based approach with LLM feedback loops
2. Rule-Based Refiner
Applies deterministic refactoring rules from industry best practices.

python
strategy = "rule-based"
# Deterministic, interpretable transformations
3. RAG Refiner (Retrieval-Augmented Generation)
Retrieves high-quality code examples and uses them to guide refinement.

python
strategy = "rag"
# Grounds refinement in real-world exemplars
Project Structure
text
llm-code-refiner/
├── README.md
├── requirements.txt
├── LICENSE
├── paper/
│   └── extended_abstract.pdf          # Submitted paper
├── src/
│   ├── pipeline.py                    # Main pipeline
│   ├── generators/
│   │   └── llm_generator.py          # Few-shot generation
│   ├── refiners/
│   │   ├── llm_refiner.py
│   │   ├── rule_based_refiner.py
│   │   └── rag_refiner.py
│   ├── validators/
│   │   └── test_validator.py         # Test case execution
│   └── metrics/
│       └── quality_metrics.py        # SonarQube integration
├── data/
│   └── apps_dataset/                 # APPS dataset (not included)
├── experiments/
│   ├── run_evaluation.py             # Evaluation script
│   └── results/                      # Experimental results
└── tests/
    └── test_pipeline.py
Configuration
Create config.yaml to customize settings:

text
# LLM Configuration
llm:
  model: "gpt-4"
  temperature: 0.7
  max_tokens: 2048

# Refinement Strategy
refinement:
  strategy: "rag"  # "llm", "rule-based", or "rag"
  max_iterations: 3
  
# Validation
validation:
  re_execute_tests: true
  correctness_threshold: 0.80

# Metrics
metrics:
  use_sonarqube: true
  quality_dimensions: ["bugs", "code_smells", "maintainability"]
Citation
If you use this code or extend this work, please cite:

text
@misc{munib2025bridging,
  title={Bridging Correctness and Quality in LLM Code Generation: A Hybrid Generate-and-Refine Pipeline},
  author={Munib, N.},
  year={2025},
  howpublished={Extended Abstract submitted to the 47th International Conference on Software Engineering (ICSE 2026)}
}
Future Work
✨ Developer-centric evaluation with human experts

✨ Multi-language support (Java, C++, JavaScript)

✨ Integration with real-world development workflows

✨ Fine-tuned LLM models for refinement

✨ Interactive refinement feedback loops

License
This project is licensed under the MIT License - see LICENSE file for details.

Contributing
Contributions are welcome! Please open an issue or submit a pull request.

Contact
For questions or collaborations, reach out to:

Munib, N. - [Your Email/GitHub Profile]

Acknowledgments
APPS Dataset creators (Hendrycks et al.)

OpenAI for GPT-4 API access

SonarQube for code quality metrics

Professor [Name] for guidance and feedback

Last Updated: November 4, 2025
Status: Extended Abstract Submitted to ICSE 2026
