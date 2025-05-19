# HuggingFace - BAAI - BGE Reranker v2 m3

This repo provides a hands-on demonstration of using BAAl's (Beijing Academy of Artificial Intelligence) `BGE-Reranker-v2-m3` model from Hugging Face for sequence reranking tasks. It includes two Jupyter notebooks:
- **BGE_Reranker_Local.ipynb**: For running the model locally using PyTorch and Hugging Face Transformers.
- **BGE_Reranker_AzureML.ipynb**: For deploying and running the model in an Azure AI environment.

> [!NOTE]
> Model weights are stored on the HuggingFace site and can be accessed at this [model card page](https://huggingface.co/BAAI/bge-reranker-v2-m3).

## Table of Contents

*   [Prerequisites](#prerequisites)
*   [Part 1: Configuring Environment](#part-1-configuring-environment)
*   [Part 2: Local use](#part-2-local-use)
*   [Part 3: Azure AI use](#part-3-azure-ai-use)
*   [Acknowledgements](#acknowledgements)

## Prerequisites
- Python 3.11+;
- GPU recommended for faster inference.

## Part 1: Configuring Environment
1. Install necessary packages:
``` bash
pip install transformers torch
```

## Part 2: Local use


## Part 3: Azure AI use
With `BGE_Reranker_AzureML.ipynb` you can deploy and run the model on Azure AI services: includes environment setup, script creation for inference, model registration, endpoint deployment and testing the deployed endpoint.

## Acknowledgements
- [BAAI](https://huggingface.co/BAAI) for developing the BGE Reranker v2 m3 model;
- [HuggingFace](https://huggingface.co/BAAI/bge-reranker-v2-m3) for hosting the model and providing the Transformers library;
- [Microsoft Azure](https://portal.azure.com) for cloud platform services.
