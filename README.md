# 📰 Fake News Detection with Retrieval-Augmented Generation (RAG) using Azure Phi-4 Mini

This project demonstrates how to use **Retrieval-Augmented Generation (RAG)** with **Microsoft Azure’s Phi-4 Mini** model to detect and analyze potential fake news.
It combines a **retriever** (for factual grounding) with **Azure’s LLM** (for reasoning) to evaluate whether a given news article or snippet is reliable.

---

## 📌 Features

* Preprocessing and embedding of news articles
* Vector database (**FAISS**) for semantic retrieval
* Integration with **Azure Phi-4 Mini** for reasoning
* Hybrid approach: ML classifier + LLM explanation
* Real-time **web scraping** for live news verification
* Interactive **Gradio interface** for testing
* Evaluation on benchmark datasets and live news

---

## 🏗️ Architecture

```
News Input → Text Processing → Embedding → FAISS Retrieval
        ↳ ML Classification → Decision Fusion → Output
        ↳ Azure Phi-4 Mini Analysis →
```

---

## 🔎 Methodology

1. **Data Preprocessing** – Clean and normalize raw text
2. **Embedding Generation** – Encode articles with Sentence Transformers
3. **Vector Database** – Store embeddings in FAISS for fast lookups
4. **Azure Phi-4 Mini** – Query model for reasoning and explanation
5. **RAG Pipeline** – Fuse retriever evidence with LLM reasoning
6. **Evaluation** – Test on ISOT dataset + live scraped articles

---

## ⚙️ Azure Setup

### Prerequisites

* Azure account with **Azure OpenAI** access
* Quota for **Phi-4 Mini**

### Steps

1. **Create Azure OpenAI resource**

   * Portal → *Create Resource* → “Azure OpenAI”
   * Choose subscription, region, and resource group

2. **Deploy Phi-4 Mini**

   * In your resource → *Model deployments*
   * Deploy `phi-4-mini` (name it, e.g., `phi4mini-deploy`)

3. **Get Keys & Endpoint**

   * Resource → *Keys and Endpoint*
   * Copy endpoint + one API key

4. **Set Environment Variables**

   ```python
   import os
   os.environ["AZURE_OPENAI_ENDPOINT"] = "https://<your-resource>.openai.azure.com/"
   os.environ["AZURE_OPENAI_API_KEY"] = "<your-api-key>"
   os.environ["AZURE_OPENAI_DEPLOYMENT"] = "phi4mini-deploy"
   ```

---

## 📊 Dataset

* **ISOT Fake News Dataset** (True.csv + Fake.csv) – [Dataset link](https://www.uvic.ca/ecs/ece/isot/datasets/fake-news/index.php)
* Custom scraped articles from Bangladeshi sources
* Optional live scraping for real-time testing

---

## ▶️ Usage

1. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```
2. Configure Azure credentials (see above)
3. Place datasets in `/data/raw/`
4. Run the pipeline:

   ```bash
   jupyter notebook Fake_News_Detection_RAG.ipynb
   ```
5. Launch Gradio UI (runs locally):

   * Enter text or URL
   * Get classification + explanation
   * Inspect retrieved evidence

---

## ✅ Example Output

* **Classification**: Real / Fake / Uncertain
* **Confidence score** (probability)
* **Reasoning explanation** (from Phi-4 Mini)
* **Retrieved evidence** used in decision

---

## 🏁 Conclusion & Future Work

* Expand to larger and multilingual datasets
* Fine-tune Phi-4 Mini on fake news corpora
* Add multiple retrieval sources
* Real-time alerts for misinformation
* Extend to image-based news verification

---

## 📜 License

MIT License – free to use and modify.

---

## ⚠️ Disclaimer

This tool is for **research and support** in misinformation detection.
It is **not an absolute authority** on truth. Always verify critical information with trusted sources.

---

Do you want me to also add a **ready-to-copy code snippet** in the README showing how to call `phi-4-mini` with `azure.ai` SDK (instead of just env vars), so users can test the connection before running the pipeline?
