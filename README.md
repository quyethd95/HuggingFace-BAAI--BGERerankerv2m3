# HuggingFace - BAAI - BGE Reranker v2 m3

This repo provides a hands-on demonstration of using BAAl's (Beijing Academy of Artificial Intelligence) `BGE-Reranker-v2-m3` model from Hugging Face for sequence reranking tasks. It includes two Jupyter notebooks:
- **BGE_Reranker_Local.ipynb**: For running the model locally using PyTorch and Hugging Face Transformers.
- **BGE_Reranker_AzureML.ipynb**: For deploying and running the model in an Azure AI environment.

> [!NOTE]
> Model weights are stored on the HuggingFace site and can be accessed at this [model card page](https://huggingface.co/BAAI/bge-reranker-v2-m3).

## Table of Contents
- [Prerequisites](#prerequisites)
- [Part 1: Configuring Environment](#part-1-configuring-environment)
- [Part 2: BGE Reranker - Local use](#part-2-bge-reranker---local-use)
- [Part 3: BGE Reranker - Azure AI use](#part-3-bge-reranker---azure-ai-use)
- [Acknowledgements](#acknowledgements)

## Prerequisites
- Python 3.11+;
- GPU recommended for faster inference.

## Part 1: Configuring Environment
1. Install necessary Python packages:
``` PowerShell
pip install -r requirements.txt
```

## Part 2: BGE Reranker - Local use
This section covers the using of the BGE Reranker v2 m3 model locally with the `BGE_Reranker_Local.ipynb` notebook.

Key steps include:
1. *Loading the Model*: Import necessary libraries (torch, transformers) and load the BAAI/bge-reranker-v2-m3 model and tokenizer, automatically detecting and using a GPU if available.
2. *Creating a Reranking Function*: Define a Python function rerank that takes a query and a list of documents, uses the loaded model to score each document's relevance to the query and returns the documents sorted by relevance score.
3. *Testing*: Demonstrate the rerank function with simple and more complex examples to show how the model reorders documents based on the query.

## Part 3: BGE Reranker - Azure AI use
With `BGE_Reranker_AzureML.ipynb` you can deploy and run the model on Azure AI services: includes environment setup, script creation for inference, model registration, endpoint deployment and testing the deployed endpoint.

## Acknowledgements
- [BAAI](https://huggingface.co/BAAI) for developing the BGE Reranker v2 m3 model;
- [HuggingFace](https://huggingface.co/BAAI/bge-reranker-v2-m3) for hosting the model and providing the Transformers library;
- [Microsoft Azure](https://portal.azure.com) for cloud platform services.
