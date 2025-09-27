# Comparative Study of Recurrent Architectures for Sentiment Analysis

## 🎯 Project Goal  
This project benchmarked the performance of five different **Recurrent Neural Network (RNN)** architectures—ranging from the simple **Vanilla RNN** to an **Attention-enhanced BiLSTM**—on the task of binary sentiment classification using the **IMDB Movie Review Dataset**.  

The primary objective was to demonstrate the effectiveness of modern architectural components (gates, bidirectionality, and attention) in overcoming fundamental challenges like the **Vanishing Gradient Problem**.  

---

## ⚙️ Architectures Benchmarked  

| Model | Key Innovation | Performance | Why it Works |
|-------|---------------|-------------|--------------|
| **Vanilla RNN** | Simple Recurrence | **49.20%** | Baseline failure due to Vanishing Gradients on long sequences. |
| **GRU (Gated Recurrent Unit)** | Two Gates (Update, Reset) | **74.39%** | Uses gates to maintain long-term information flow. Significant jump from RNN. |
| **LSTM (Long Short-Term Memory)** | Three Gates (Input, Forget, Output) + Cell State | **87.61%** | Dedicated memory (Cell State) proved more effective than GRU for complex dependencies. |
| **BiLSTM (Bidirectional LSTM)** | Processes input Forward & Backward | **88.93%** | Captures context from both the past and the future of a word, yielding a small but measurable boost. |
| **BiLSTM + Luong Attention** | Contextual Weighting | **90.25%** | Dynamically weighs the importance of each word's hidden state, focusing on keywords for the final classification. |

---

## 📈 Key Results and Conclusion  

The final results clearly validate the effectiveness of advanced RNN architectures. Performance improved consistently with increased model complexity:  

| Model | Test Accuracy (%) | Key Takeaway |
|-------|------------------|--------------|
| **Vanilla RNN** | 49.20 | Failure; confirmed Vanishing Gradient problem. |
| **GRU** | 74.39 | Success; confirmed necessity of gating mechanisms. |
| **LSTM** | 87.61 | Strong Benchmark; superior memory management. |
| **BiLSTM** | 88.93 | Architectural Gain; confirmed the value of bidirectional context. |
| **BiLSTM + Attention** | 90.25 | Best Performance; confirmed attention's ability to boost final accuracy. |

**Conclusion:**  
The use of **gating units (LSTM)** was the most significant factor for initial performance gain, while the addition of **Attention** provided the final, crucial performance lift, establishing the **Attention-BiLSTM** as the optimal model for this task.  

---

## 🛠️ Implementation Details  

### Framework and Tools  
- **Framework:** PyTorch  
- **Language:** Python  
- **Optimization:** Adam Optimizer  
- **Loss Function:** Cross-Entropy Loss  

### Critical Architectural Fixes  
Two key implementation challenges were addressed to ensure accurate benchmarking:  

1. **BiLSTM Output Handling**  
   - The initial BiLSTM implementation ignored the backward pass.  
   - Fixed by setting the final fully-connected layer to receive an input of size **2 × Hidden_Dim** and explicitly concatenating the final forward and backward hidden states.  

2. **Overfitting Management**  
   - All high-capacity models were highly prone to overfitting.  
   - Mitigated with a strict **Early Stopping** mechanism, monitoring validation accuracy with a **Patience of 5 epochs**, and saving model weights only at peak generalization.  

### Delayed Learning Observation  
- The **LSTM** and **BiLSTM** models exhibited a **"Delayed Learning" effect**, remaining at ≈50% accuracy for the first 7 epochs before suddenly converging.  
- This suggests an initial sub-optimal weight initialization that required several epochs to break out of a flat loss region.  

---
