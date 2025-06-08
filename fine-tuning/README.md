## 🤖 `hyrox_fine-tuning-gpt2` — First Attempt: Fine-tuning GPT-2

This notebook captures my first attempt at fine-tuning a language model to generate personalized performance feedback for Hyrox athletes, using the initial feedback data generated in the hyrox_ml analysis.

### 📌 Goal

To train a lightweight model (`gpt2`) to understand structured performance data (e.g., predicted time, actual time, cluster info) and produce helpful, human-readable feedback.


### 🧪 What I Did

* I took guidance from the fine-tuning Colab shared in class to structure my approach.

  * `input`: instruction
  * `context`: performance metrics per athlete
  * `response`: the ground-truth feedback message
* Combined those fields into full instruction-style prompts.
* Tokenized the prompts using GPT-2 tokenizer.
* Fine-tuned `gpt2` using Hugging Face’s `Trainer` API on Colab.
* Evaluated outputs by manually testing sample generations.

### 📈 Results

* The model learned to structure responses and replicate tone reasonably well.
* However, it seemed to lack deeper reasoning.

### 🔚 Conclusion

While GPT-2 worked as a proof of concept, its limitations in understanding structured context and generating more dynamic feedback led me to explore a stronger model.

➡️ I decided to continue with **Mistral-7B** using **LoRA fine-tuning**.
