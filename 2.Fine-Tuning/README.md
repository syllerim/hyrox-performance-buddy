## 🤖 `hyrox_fine-tuning-gpt2` — First Attempt: Fine-tuning GPT-2

----

**Note**
Visualizing the notebook shows **Invalid Notebook** so here is the link to the [Hyrox_Fine_tuning_GPT2.ipynb Colab](https://drive.google.com/file/d/1bY7h1cpv7hyNAuGilJd0-1m3TEGM4JiJ)

----

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

I decided to continue with **Mistral-7B** using **LoRA fine-tuning**.


## 🔄 `hyrox_fine-tuning-mistral` — Second Attempt: Fine-tuning Mistral-7B with LoRA

This second iteration focused on fine-tuning the more powerful `Mistral-7B-Instruct` model using **LoRA (Low-Rank Adaptation)** to improve the quality and personalization of the generated feedback.

### 📌 Goal

To generate feedback that’s more natural, dynamic, and contextually rich than what GPT-2 could provide — while keeping the training lightweight using LoRA and quantization techniques.

### 🧪 What I Did

- Prepared the same dataset using instruction-style prompts (`input`, `context`, `response`), adapted for larger context windows.  
- Set up a 4-bit quantized model loading configuration (BitsAndBytes).  
- Configured LoRA adapters for key attention layers (`q_proj`, `v_proj`).  
- Used Hugging Face’s `Trainer` to begin fine-tuning on Google Colab.  
- Tokenized data with longer sequence limits to take advantage of Mistral’s capacity.

### ⚠️ Challenges

- Training took **over 2 hours** on Google Colab.  
- I ran into an infrastructure issue: I didn't define the required `offload_folder` when using `device_map="auto"` for CPU+disk offloading.  
- After training, I was unable to load the model for inference, and Colab GPU time had run out.

### 📈 Observations
- It showed the importance of properly managing training configuration and Colab session limits.

### 🔚 Conclusion

This step revealed the real-world challenges of working with larger models. While the results couldn’t be finalized due to resource limits, the model was successfully trained, and the experience highlighted the need for a more scalable alternative, such as **RAG (Retrieval-Augmented Generation)** for future iterations.
