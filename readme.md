# IMDB Sentiment Analysis 🎬📝

This project is a **comparative study of deep learning architectures** for sentiment classification on the **IMDB movie reviews dataset**.
The goal is to analyze how different sequential models perform on text data and how techniques like **bidirectionality** and **attention** improve results.

---


## 🛠️ Models Implemented

1. **Vanilla RNN**
2. **GRU (Gated Recurrent Unit)**
3. **LSTM (Long Short-Term Memory)**
4. **BiLSTM (Bidirectional LSTM)**
5. **BiLSTM + Luong Attention**

---

## 📊 Results

| Model                    | Accuracy |
| ------------------------ | -------- |
| Vanilla RNN              | 49%      |
| GRU                      | 75%      |
| LSTM                     | 87%      |
| BiLSTM                   | ~88%     |
| BiLSTM + Luong Attention | ~90%     |

✅ Performance steadily improves as we move from simple RNNs → GRU/LSTM → BiLSTM → Attention.
✅ Attention mechanism further boosts interpretability by highlighting key words in reviews.

---

## 🔑 Key Insights

* **RNNs struggle** with long sequences due to vanishing gradients.
* **GRUs/LSTMs** solve this with gating mechanisms, leading to a big performance boost.
* **BiLSTMs** capture context from both directions in the review text.
* **Attention** lets the model “focus” on the most relevant words (e.g., *boring*, *amazing*, *waste*), improving both accuracy and interpretability.

---

## 🚀 How to Run

1. Clone this repo:

   ```bash
   git clone https://github.com/Nikunj7185/IMDB-Sentiment-Analysis.git
   cd IMDB-Sentiment-Analysis
   ```

2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

   *(make sure to create a `requirements.txt` with packages like `tensorflow`, `keras`, `numpy`, `pandas`, `matplotlib`)*

3. Open any notebook and run:

   ```bash
   jupyter notebook 01_rnn.ipynb
   ```

---

## 📌 Future Improvements

* Add **attention visualization** to show which words the model focuses on.
* Package the best model into a **web app (Flask / Streamlit / Gradio)** for live sentiment prediction.
* Benchmark against **Transformer-based models (e.g., BERT)** for comparison.

---
