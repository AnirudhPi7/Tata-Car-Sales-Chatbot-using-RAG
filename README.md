# Persuasive Car Sales Chatbot for Tata Motors (RAG)

---

## Introduction
This project builds a **Retrieval-Augmented Generation (RAG)** chatbot tailored for **Tata Motors’ car sales**.  
It combines factual retrieval from brochures and FAQs with **persuasive conversational techniques**, making it a digital sales assistant that is both informative and influential.

---

## Background
Traditional chatbots in sales often:
- Provide static FAQ answers
- Lack personalization
- Fail to persuade customers into action
- Not reliable, prone to factual errors

With the advent of **Large Language Models (LLMs)** and retrieval systems, it is possible to create chatbots that are:
- **Grounded** in verified knowledge  
- **Conversationally engaging**  
- **Aligned with sales objectives**

---

## Problem Statement
Car buyers frequently ask detailed questions about:
- Features, specifications, and price comparisons  
- Financing and warranty options  
- Why they should choose Tata over competitors  

Conventional bots cannot handle this dynamically, leading to:
- **Hallucinations** (incorrect answers)  
- **Loss of customer trust**  
- **Lower lead conversions**  

---

## Terminologies
- **RAG (Retrieval-Augmented Generation):** Framework where an LLM retrieves knowledge chunks before generating an answer.  
- **FAISS:** Facebook AI Similarity Search, used for vector database indexing and retrieval.  
- **MiniLM:** A lightweight transformer for embedding text into dense vectors.  
- **LoRA (Low-Rank Adaptation):** Efficient fine-tuning technique for large models.  
- **TinyLlama-1.1B:** A small open-source LLM used as the generative backbone.  

---

## Dataset
- **Sources:** Tata Motors brochures, official website FAQs, and marketing materials.  
- **Format:** Text extracted from PDFs and web pages.  
- **Size:** ~20 documents (brochures + FAQs).  
- **Preprocessing:**  
  - Chunking text into 500–700 token segments  
  - Embedding using MiniLM (Sentence-Transformers)  
  - Stored in FAISS vector database  

---

## Data Cleaning & Imputation
- Removed irrelevant text (headers, footers, disclaimers).  
- Normalized text encoding.  
- Deduplicated repeated FAQ entries.  
- Missing warranty/financing details filled from official Tata documents.  

---

## Methodology
1. **Knowledge Ingestion**  
   - Convert PDFs & FAQs into structured text.  
   - Chunk documents into passages.  
   - Store embeddings + metadata in FAISS.  

2. **Retrieval**  
   - At each user query, fetch top-k (k=5) semantically similar chunks.  

3. **Response Generation**  
   - Pass retrieved chunks + user query to TinyLlama (LoRA-finetuned).  
   - Apply persuasion layer: integrates sales techniques (e.g., scarcity, authority).  

4. **Evaluation**  
   - LLM-as-a-judge framework: rated on groundedness, correctness, persuasiveness, tone.  

---

## Model Architecture
