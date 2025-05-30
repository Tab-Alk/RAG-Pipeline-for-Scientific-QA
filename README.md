# RAG-Pipeline-for-Scientific-QA

## Introduction

This project explores how Retrieval-Augmented Generation (RAG) can be used to build an intuitive, conversational system for question answering over academic research papers. The pipeline combines vector-based document retrieval with a local language model, enabling users to ask natural language questions and receive grounded, document-based answers. The goal is to create a flexible and offline-capable framework for synthesizing and interacting with complex material in a more human-centered way.

The idea for this project stems from my background at the intersection of neuroscience and AI. As a data science student with a strong interest in how biological neural networks inspire modern machine learning, I wanted to explore how retrieval-based architectures can support deeper understanding of dense, technical texts. This pipeline was developed as a hands-on experiment in applying RAG techniques to research literature, with a focus on making the interaction process more intuitive and transparent.

---

## Methodology

- **Document Preparation**
  The system was tested on a neuroscience-inspired AI research paper focused on the parallels between biological neural networks and transformer models. The PDF was parsed and split into smaller document chunks for processing. The following papers were included:
    * **Attention Is All You Need (Vaswani et al., 2017)**
        * Introduces the Transformer architecture and self-attention mechanism.
        * Highlights parallels between attention in neural circuits and self-attention in models.
    * **BioinspiredLLM: Conversational Large Language Model for the Mechanics of Biological and Bio-Inspired Materials**
        * Demonstrates fine-tuning generative models on biologically inspired design principles.
        * Uses RAG-like retrieval to ground generated concepts in biological mechanics.
    * **Spiking Neural Networks: A Survey**
        * Surveys computational models of spiking neurons and their dynamics.
        * Provides insights into temporal coding and plasticity in the brain.


- **Embedding Generation**  
  Each document chunk was embedded into vector space using a pre-trained sentence embedding model (`sentence-transformers/all-MiniLM-L6-v2`), producing dense semantic representations suitable for retrieval.

- **Vector Indexing**  
  The resulting embeddings were indexed using FAISS, an efficient vector database that enables fast similarity-based search across the document corpus. The index was saved locally for reuse.

- **Language Model Integration**  
  A local Hugging Face language model (`google/flan-t5-base`) was used to generate conversational answers, conditioned on the top-retrieved document chunks.

- **Conversational Retrieval Chain**  
  The entire flow was orchestrated through a conversational retrieval chain, enabling multi-turn interactions and maintaining chat history to support context-aware Q&A.


## Pipeline Architecture

<p align="center">
  <img width="1100" alt="Screenshot 2025-05-30 at 1 09 01 PM" src="https://github.com/user-attachments/assets/625cf34d-4af7-4b2c-bf69-2968db1bab45" />
</p>


## Example Q&A

**Question:** How are biological neural networks similar to Transformers?  
**Answer:** The system retrieves relevant sections and provides a grounded explanation.

**Question:** How do biological neurons differ from Transformer neurons?  
**Answer:** The model offers a comparison based on the document content.

---

## Key Insights & Conclusion

This project highlights the potential of RAG pipelines as a tool for making complex academic material more accessible through conversational AI. By combining embeddings, vector search, and language models, the system enables users to engage with dense texts in a more natural and transparent way. The modular design supports easy extension to other documents and domains, offering a foundation for future applications in research assistance, education, and private knowledge management. Building this pipeline also deepened my understanding of retrieval-augmented systems and their role in bridging search and reasoning.
