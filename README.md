Read on Medium: https://medium.com/@vieira.r.luis/supercharging-llm-fine-tuning-unsloth-lora-and-orpo-for-travel-q-a-classification-on-a-budget-db416f41fa2e

## Introduction

This project aims to develop a simple text classification system using large language models (LLMs). The model is tasked with categorising travel-related questions into predefined classes. The approach includes prompt design, zero-shot and few-shot testing, as well as supervised fine-tuning (SFT), followed by performance evaluation using metrics such as accuracy.

### Research Questions

1. How can LLMs be effectively optimized for travel-related text classification tasks?
2. What are the differences in performance between zero-shot, one-shot, and few-shot prompting for travel question classification?
3. How does ORPO-SFT impact model performance in travel classification tasks?
4. What additional improvements can be achieved by leveraging advanced prompting and fine-tuning strategies?

### **Summary**

#### **1. Data Loading and Preparation:**
- A dataset of 5000 travel-related questions is loaded, cleaned, and split into training (4000), validation (300), and test (700) sets.
- Each question is categorized into one of the predefined classes: **Things to Do (TTD)**, **Travel Guide (TGU)**, **Accommodation (ACM)**, **Transport (TRS)**, **Weather (WTH)**, **Food (FOD)**, and **Entertainment (ENT)**.
- The dataset is formatted into a structured form for input to the LLMs.
- Source: Kahaduwa, H., Pathirana, D., Arachchi, P.L., Dias, V., Ranathunga, S. and Kohomban, U., 2017, May. Question Answering system for the travel domain. In Engineering Research Conference (MERCon), 2017 Moratuwa (pp. 449-454). IEEE. (https://github.com/suralk/travel_domain_data/)

#### **2. Model Selection and Loading:**
- Multiple models are considered, with the primary focus on compact models such as **Phi 3.5 mini-instruct** from Unsloth, which is efficient for zero-shot and few-shot learning tasks.
- The model and tokenizer are loaded, with tokenization adjustments such as adding a padding token if necessary.
- **4-bit quantization** is used to optimise memory usage without sacrificing much performance.

#### **3. Prompt Engineering:**
- Various prompt templates are designed to test the classification performance of the models. The templates range from concise, direct prompts to more detailed Chain of Thought (CoT) prompts.
- These prompts guide the model in understanding the travel question and mapping it to one of the predefined classes.
- Prompts include zero-shot, one-shot, and three-shot examples to test how well the model performs with varying amounts of context.

#### **4. Evaluation:**
- The prompts are evaluated on small test samples and full test datasets, with results being analyzed in terms of accuracy.
- **Zero-shot** and **few-shot** learning evaluations are performed on the test dataset, comparing the accuracy across different prompt designs and shot levels.
- Classification metrics such as precision, recall, and F1-score are reported for each class.
- **Misclassification analysis** is also performed to understand where the model struggles, identifying incorrect predictions and their possible causes.

#### **5. Fine-Tuning with ORPO:**
- The code includes SFT using **Odds Ratio Preference Optimization (ORPO)**, a method that merges supervised fine-tuning with preference-based learning.
- The **ORPO** configuration optimizes the model based on chosen/rejected responses for each prompt, further refining the model's ability to classify questions accurately.

#### **6. Post-Fine-Tuning Evaluation:**
- After fine-tuning with ORPO, the model's performance is re-evaluated on the test set to measure improvements.
- Post-fine-tuning results show significant accuracy gains, with **Phi 3.5 mini-instruct** reaching an accuracy of **82.86%**, up from 62% in zero-shot evaluation, and **Gemma 2 9B-it** reaching an accuracy of **87.71%**, up from 69.71% in zero-shot evaluation.

---

### **Conclusion**

The project successfully demonstrates the use of compact language models like **Phi 3.5 mini-instruct** in classifying travel-related questions. By leveraging effective prompt engineering, few-shot learning, and **ORPO**-based fine-tuning, the model's accuracy improves significantly. The process involves careful dataset preparation, prompt design, and iterative evaluation.

---
