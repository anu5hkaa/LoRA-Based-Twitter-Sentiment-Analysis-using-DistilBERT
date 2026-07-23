# 📖 Understanding LoRA (Low-Rank Adaptation)

This repository documents my learning journey while studying the **LoRA (Low-Rank Adaptation of Large Language Models)** research paper and implementing its core ideas using Hugging Face Transformers and the PEFT library.

The primary goal was to understand the motivation behind LoRA, its mathematical intuition, how it modifies transformer layers, and how different hyperparameters influence model performance.

---

# 📌 Why LoRA?

Traditional fine-tuning updates every parameter of a pretrained model, making the process computationally expensive and memory intensive, especially for large language models.

LoRA introduces a parameter-efficient approach by freezing the original pretrained weights and learning only small low-rank matrices that are injected into selected transformer layers. This significantly reduces the number of trainable parameters while maintaining competitive performance.

---

# 📚 Concepts Explored

While studying the paper, I explored and understood:

- Traditional Fine-Tuning
- Parameter-Efficient Fine-Tuning (PEFT)
- Low-Rank Adaptation (LoRA)
- Low-Rank Matrix Decomposition
- Why LoRA targets Query and Value projection layers
- Frozen vs Trainable Parameters
- LoRA Hyperparameters
  - Rank (r)
  - Alpha (α)
  - LoRA Dropout
- Sequence Classification using DistilBERT
- Model Evaluation Metrics
  - Accuracy
  - Precision
  - Recall
  - F1-Score

---

# 🧪 Hands-on Learning

To reinforce the concepts presented in the paper, I implemented LoRA using:

- DistilBERT
- Hugging Face Transformers
- PEFT Library
- TweetEval Sentiment Dataset

The implementation helped me understand how LoRA adapters are attached to transformer attention layers and how only a small subset of parameters are updated during training.

---

# 🔬 Hyperparameter Exploration

To better understand the behavior of LoRA, I experimented with different hyperparameter configurations and observed their impact on model performance.

| Rank (r) | Alpha (α) | Validation Accuracy | Validation F1 |
|----------|-----------|--------------------:|--------------:|
| 8 | 16 | 71.65% | 71.89% |
| **4** | **16** | **72.75%** | **72.76%** |
| 4 | 8 | 71.40%* | 71.48%* |

\*Values recorded during experimentation.

### Best Configuration

- **Rank (r):** 4
- **Alpha (α):** 16
- **Validation Accuracy:** 72.75%
- **Validation F1-Score:** 72.76%

### Test Performance

The final model was evaluated on the held-out test set using:

- Accuracy
- Precision
- Recall
- F1-Score
 Metric | Score |
|---------|------:|
| Test Loss | **0.6927** |
| Accuracy | **68.60%** |
| Precision | **68.86%** |
| Recall | **68.60%** |
| F1 Score | **68.64%** |

---

# 📝 Key Learnings

- LoRA enables efficient adaptation of pretrained transformer models by training only lightweight adapter matrices.
- The choice of **Rank (r)** and **Alpha (α)** directly affects model capacity and performance.
- Lower-rank adapters can perform competitively while requiring fewer trainable parameters.
- Hyperparameter tuning is important, as different configurations lead to different accuracy and F1 scores.
- LoRA offers a practical alternative to full fine-tuning for NLP tasks when computational resources are limited.

---

# 🛠️ Tools & Libraries

- Python
- PyTorch
- Hugging Face Transformers
- Hugging Face Datasets
- PEFT (LoRA)
- Scikit-learn
- NumPy
- Google Colab

---

# 📖 Reference

**LoRA: Low-Rank Adaptation of Large Language Models**

Hu et al., 2021
