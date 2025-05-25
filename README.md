### **Product Name**: TaxMate – Your Personalized Tax Q\&A Assistant

### **Product Type**: Retrieval-Augmented Generation (RAG)

### **LLM Model**: [mistralai/Mistral-7B-Instruct-v0.1](https://huggingface.co/mistralai/Mistral-7B-Instruct-v0.1)

### **Interface**: Streamlit-based UI

### **Owner**: Varad Naik

### **Date**: May 24, 2025

---

## ✅ **1. Problem Statement**

Taxpayers with complex returns face difficulty in understanding evolving IRS tax rules. IRS publications are long, jargon-heavy, and updated yearly. There’s a need for an easy-to-use tool to ask personalized tax questions and get contextual, updated answers.

---

## 🎯 **2. Goal**

Build a user-friendly, RAG-powered web app that:

* Accepts tax-related queries
* Retrieves context from official IRS publications (e.g., Pub 17)
* Uses Mistral LLM to generate accurate answers
* Displays the source text used in responses

---

## 🧩 **3. Key Features & Scope**

| Feature                    | Description                                                                       |
| -------------------------- | --------------------------------------------------------------------------------- |
| 📄 IRS Document Ingestion  | Load, chunk, and store IRS PDF docs (starting with Pub 17 - Individual Tax Guide) |
| 🔍 Vector-based Retrieval  | Use FAISS and sentence-transformers to search top-N relevant chunks               |
| 🧠 RAG + Mistral LLM       | Combine retrieved chunks + user query to answer with Mistral                      |
| 💬 Streamlit UI            | Simple interface to enter a question and view the answer and source               |
| 🔄 Yearly Document Updates | Add new tax year’s documents and rebuild index                                    |
| ❗ Disclaimers              | Add clear note that this is not legal/financial advice                            |

---

## 🚫 **4. Out of Scope**

* Auto-generating tax forms like 1040 (possible future enhancement)
* Personalized tax filing, state-level taxation, or integration with tax platforms (TurboTax, H\&R Block)
* Voice input or real-time chatbot features

---

## 🛠️ **5. Technical Architecture**

| Component          | Technology                                                 |
| ------------------ | ---------------------------------------------------------- |
| PDF Parsing        | `PyMuPDF`, `pdfplumber`                                    |
| Chunking           | Token-based (e.g., 500–800 tokens per chunk)               |
| Embeddings         | `sentence-transformers/all-MiniLM-L6-v2` or `bge-small-en` |
| Vector Store       | `FAISS`                                                    |
| Backend Logic      | Python + `transformers` + `mistral` model loading          |
| UI                 | `Streamlit`                                                |
| Hosting (Optional) | Hugging Face Spaces or local Docker                        |

---

## 🔐 **6. Guardrails & Constraints**

| Guardrail Type         | Description                                                        |
| ---------------------- | ------------------------------------------------------------------ |
| ✅ Accuracy             | Only answer if context confidence > threshold                      |
| 🧠 Source Transparency | Display retrieved text used in answer                              |
| 🔁 Year Versioning     | Tag content by tax year to support future multi-year retrieval     |
| 📛 Disclaimer          | Clearly mention that this is not legal advice                      |
| 🇺🇸 Domain Scope      | Focus on U.S. Federal personal income tax (start with Pub 17 only) |

---

## 📊 **7. KPIs (Key Performance Indicators)**

| KPI                              | Target                                                        |
| -------------------------------- | ------------------------------------------------------------- |
| 🧠 Answer accuracy (manual test) | ≥85% relevance on top-3 retrieval                             |
| ⏱️ Avg. Query Response Time      | <10 seconds (local CPU/GPU)                                   |
| 🧪 User Testing Coverage         | Test 20 queries across deduction, credit, filing status, etc. |
| 🔁 Update Time per Year          | <30 minutes to ingest new year's documents                    |
| ✅ Query Confidence Threshold     | Adjustable — start at cosine similarity > 0.65                |

---

## 📦 **8. Data Sources**

| Type        | Source                                   | Format |
| ----------- | ---------------------------------------- | ------ |
| Tax Guide   | IRS Pub 17 (PDF, HTML)                   | PDF    |
| FAQs        | [irs.gov/faqs](https://www.irs.gov/faqs) | HTML   |
| Legal Rules | IRS Notices, Bulletins                   | PDF    |
| Blogs       | Optional (e.g., NerdWallet, Intuit)      | Web    |

---

## ⚠️ **9. Limitations**

* Mistral LLM might **hallucinate** if irrelevant chunks are retrieved
* Not suitable for **state tax laws** or business taxes
* Cannot generate tax documents (e.g., Form 1040) or file returns
* Retrieval works best for **well-phrased queries**
* Cannot validate data or numbers for user-specific returns

---

## 🌟 **10. Benefits**

| User Type           | Benefit                                                                      |
| ------------------- | ---------------------------------------------------------------------------- |
| Individual Filers   | Understand tax deductions, credits, filing status rules with minimal reading |
| Tax Pros            | Use as reference for FAQs backed by IRS sources                              |
| Portfolio Reviewers | Real-world RAG implementation with search, retrieval, and UI using open LLMs |

---

## 🧭 **11. Roadmap**

| Phase                         | Description                          |
| ----------------------------- | ------------------------------------ |
| ✅ 1. PRD Finalized            | Requirements locked                  |
| 🚧 2. Ingestion + Chunking    | Parse and chunk Pub 17               |
| 🔍 3. Embedding + FAISS Index | Store and retrieve tax content       |
| 🤖 4. Mistral RAG Pipeline    | Combine top-N chunks + prompt        |
| 🎨 5. Streamlit UI            | Interactive frontend to test queries |
| 🔁 6. Document Update Logic   | Add support for new tax years        |
| ✅ 7. Portfolio Packaging      | Add README, demo video, GitHub link  |
