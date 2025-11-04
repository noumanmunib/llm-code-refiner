# 🧠 LLM Code Refiner  
**Bridging the correctness-quality trade-off in Large Language Model-generated code through a hybrid two-stage pipeline**

---

## 📘 Overview

LLM-generated code often exhibits a fundamental trade-off:

- **High correctness but poor quality** → via few-shot prompting  
- **High quality but low correctness** → via fine-tuning/refinement  

**LLM Code Refiner** addresses this issue through a **hybrid Generate-and-Refine pipeline** that decouples correctness and quality concerns.

### 🧩 Two-Stage Pipeline

1. **Stage 1: Code Generation →** Prioritize correctness (Pass@1 ≥ 0.80) using few-shot prompting  
2. **Stage 2: Code Refinement →** Improve code quality **without sacrificing correctness**

We evaluate **three distinct refinement strategies**:
- **LLM-Based Refiner:** Semantic understanding for holistic refactoring  
- **Rule-Based Refiner:** Deterministic automated transformations  
- **RAG Refiner:** Retrieval-Augmented Generation for exemplar-guided refinement

---

## 📄 Research Paper

**Title:** *Bridging Correctness and Quality in LLM Code Generation: A Hybrid Generate-and-Refine Pipeline*  
**Author:** Munib, N.  
**Status:** Extended Abstract submitted to **ICSE 2026**  
**Year:** 2025  

📑 *Read the Extended Abstract* (available in /paper/Bridging_Correctness_and_Quality_in_LLM_Code_Generation__A_Hybrid_Generate_and_Refine_Pipeline.pdf)

---

## 🚀 Key Features

✅ **Modular Architecture** – Easily swap refinement strategies  
✅ **Correctness Validation** – Automatic re-execution of test cases  
✅ **Multiple Quality Metrics** – Integrated with **SonarQube** (bugs, smells, maintainability)  
✅ **Empirical Evaluation** – Benchmarked on the **APPS dataset** (480 problems)  
✅ **Reproducible** – Open-source and well-documented

---

## ⚙️ Quick Start

### **Prerequisites**
Python 3.8+
pip install -r requirements.txt

### **Installation**
git clone https://github.com/yourusername/llm-code-refiner.git
cd llm-code-refiner
pip install -r requirements.txt

### **Basic Usage**
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

## 🧠 Architecture
### **Pipeline Flow**
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

## **📊 Evaluation**
### **Dataset**

APPS Dataset: 480 programming problems

Difficulty Levels: Easy, Medium, Hard

Language: Python

Metrics
Metric	Description
Pass@1	Correctness: % of solutions passing all test cases
Bugs	SonarQube: Critical and major bugs detected
Code Smells	Quality issues (unused vars, duplication, etc.)
Maintainability Index	Overall maintainability score

_Results will be published upon full paper completion._

## **🔍 Refinement Strategies**
### **1. LLM-Based Refiner**
Uses semantic understanding to improve code structure while preserving correctness.

### **2. Rule-Based Refiner**
Applies deterministic transformations inspired by industry best practices.

### **3. RAG Refiner (Retrieval-Augmented Generation)**
Retrieves exemplar solutions and refines generated code using contextual guidance.

## **📚 Citation**
If you use this code or extend this work, please cite:

@misc{munib2025bridging,
  title={Bridging Correctness and Quality in LLM Code Generation: A Hybrid Generate-and-Refine Pipeline},
  author={Munib, N.},
  year={2025},
  howpublished={Extended Abstract submitted to the 47th International Conference on Software Engineering (ICSE 2026)}
}

## **🔮 Future Work**

✨ Developer-centric evaluation with human experts

🌍 Multi-language support (Java, C++, JavaScript)

🧩 Integration into real-world development workflows

🎯 Fine-tuned LLM models for refinement

🔁 Interactive refinement feedback loops

🪪 License

This project is licensed under the MIT License — see the LICENSE
 file for details.

## **🤝 Contributing**

Contributions are welcome!
Please open an issue or submit a pull request to contribute.

## **📬 Contact**

Author: Nouman Munib
📧 noumanmunib27@gmail.com

## **🙏 Acknowledgments**

APPS Dataset creators (Hendrycks et al.)

OpenAI for GPT-4 API access

SonarQube for quality metrics integration

Professor Fabio Santos for valuable guidance and feedback

🕓 Last Updated: November 4, 2025
📄 Status: Extended Abstract Submitted to ICSE 2026
