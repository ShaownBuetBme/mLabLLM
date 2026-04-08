[![AAAI 2025](https://img.shields.io/badge/AAAI-2025-blue?style=flat-square&logo=academia&logoColor=white)](https://openreview.net/forum?id=E6J9IFPE0w)

mLabLLM — Antihallucinogenic AI for Tropical Disease Differential Diagnosis
mLabLLM is a fine-tuned adaptation of LLaMA 3.2 3B optimized for clinical differential diagnosis in resource-constrained, tropical medicine settings. Developed at the mHealth Lab, BUET, it addresses a critical gap in AI-assisted healthcare for low- and middle-income countries (LMICs) — where diseases like Dengue, Malaria, and Chikungunya are prevalent yet frequently misdiagnosed.
The system combines efficient fine-tuning (LoRA + pruning + 8-bit quantization) with a dynamic probabilistic diagnosis framework that iteratively questions the patient, extracts medical entities, queries biomedical literature, and ranks diagnoses using Bayesian reasoning — all within a lightweight, deployable footprint.
📄 Read the paper on OpenReview: Efficient Antihallucinogenic AI for Tropical Medicine: A Probabilistic Framework for Differential Diagnosis

✨ Highlights

🏆 82.8% Top-3 Differential Diagnosis Accuracy — outperforming Phi-3-128k (75.1%) and base LLaMA 3.2 3B (72.4%)
⚡ LoRA fine-tuning reduces trainable parameters by ~256× vs. full fine-tuning
🔬 Bayesian probabilistic ranking integrates symptom frequencies with epidemiological priors
📚 PubMed-augmented reasoning via real-time literature retrieval (PyMed + SciBERT)
🩺 NER-driven symptom extraction using SciSpaCy
🌍 Designed for low-resource deployment in tropical and sub-tropical healthcare systems


🧠 How It Works

The model opens a structured clinical conversation with the patient
Symptoms are extracted via Named Entity Recognition (SciSpaCy)
Extracted terms query PubMed for supporting biomedical literature
A weighted frequency dictionary accumulates symptom-disease associations over turns
Bayesian posterior probabilities rank the most likely diagnoses in real time
Questioning stops when diagnosis scores converge or a turn limit is reached


📊 Performance
ModelUSMLE Acc.MedQA Acc.Top-3 Diag.Symptom F1ROUGE-LBLEULLaMA 3.2 3B55.0%51.5%72.4%0.6842.1%38.5%Phi-3-128k57.8%54.3%75.1%0.7244.0%40.2%mLabLLM65.2%62.1%82.8%0.7949.3%45.6%

🗂️ Dataset
SourceEntriesTropical Diseases Dataset (custom)50,000PubMedQA — Labeled1,000PubMedQA — Unlabeled61,200PubMedQA — Artificial211,300USMLE + MedQA QA Pairs~60,000

🛠️ Tech Stack
LLaMA 3.2 3B · HuggingFace Transformers · PEFT / LoRA · SciSpaCy · PyMed · SciBERT · PyTorch

📄 Citation
If you use this work, please cite:
bibtex@inproceedings{sani2025mlabllm,
  title     = {Efficient Antihallucinogenic {AI} for Tropical Medicine: 
               A Probabilistic Framework for Differential Diagnosis},
  author    = {Sani, S. M. Sakeef and Miah, Md. Shaown and Hasan, Taufiq},
  booktitle = {AAAI 2025 Workshop},
  year      = {2025},
  url       = {https://openreview.net/forum?id=E6J9IFPE0w},
  note      = {mHealth Lab, Department of Biomedical Engineering, 
               Bangladesh University of Engineering and Technology (BUET)}
}
