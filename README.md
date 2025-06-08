# 🏋️‍♂️ HyroxGPT: Personalized Feedback Generator for Hyrox Athletes

*KeepCoding Full-Stack AI Bootcamp III*

**Author:** Mirellys Arteta Davila

**Module:** Large Language Models (LLMs)

💡 What It Does

HyroxGPT is an intelligent system that analyzes race performance data from Hyrox competitions and generates personalized feedback for athletes. It combines classical machine learning with LLM fine-tuning techniques to deliver insights such as:
	•	Whether the athlete over- or under-performed vs expected
	•	What their cluster/group performance looks like
	•	Recommendations for improvement

 🗂️ Project Structure

📊 1.Hyrox_ML/ — Machine Learning Performance Analysis
💻 File:
	•	Hyrox_ML.ipynb

 This notebook contains the first stage of the project where:
 
	•	Raw Hyrox results were preprocessed and converted into numerical features.
	•	Feature engineering was applied (z-scores, MinMax scaling, clustering).
	•	Models (Linear Regression and LightGBM) were trained to predict total race time.
	•	An intermediate performance_feedback column was generated, used later for LLM fine-tuning.

🤖 2.Fine-Tuning/ — LLM Fine-Tuning (GPT-2 and Mistral-7B + LoRA)
💻 Files:
	•	Hyrox_Fine_tuning_GPT2.ipynb
	•	Hyrox_Fine_tuning_Mistral7B_LoRA.ipynb

This folder contains attempts at fine-tuning language models to generate more human-like feedback:
	•	GPT-2 was used in the first iteration. It was easy to train but limited in expressiveness and generalization.
	•	Mistral-7B + LoRA later explored to improve output quality, but training was interrupted due to limited Colab GPU time and missing configuration (offload folder).
	•	Instruction-style prompts were created from the ML feedback for use in model training.

 📎 Files in Root
	•	Presentation.pdf: Summary slides of the project and results.
	•	LICENSE: Open source license.
	•	README.md: This file.

 📂 Resources & Data
	•	hyrox_data_1.csv: Cleaned dataset used for ML model training and feedback generation.
	•	hyrox_json_instructed.jsonl: Instruction-formatted dataset used for GPT-2 and Mistral fine-tuning.
	•	hyrox_split_dataset/: Contains the train/val/test splits of the instruction dataset.
	•	hyrox_gpt2_model/: Fine-tuned GPT-2 model artifacts (model weights, tokenizer config, etc.) --> 🤗 https://huggingface.co/Syllerim/gpt2-hyrox
 
