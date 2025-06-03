# HuggingFace - BAAI - BGE Reranker v2 m3

This repo provides a hands-on demonstration of using BAAl's (Beijing Academy of Artificial Intelligence) `BGE-Reranker-v2-m3` model from Hugging Face for sequence reranking tasks. It includes two Jupyter notebooks:
- **BGE_Reranker_Local.ipynb**: For running the model locally using PyTorch and Hugging Face Transformers.
- **BGE_Reranker_AzureML.ipynb**: For deploying and running the model in Azure Machine Learning inference environment.

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
1. *Loading the Model*: Import necessary libraries and load the BAAI/bge-reranker-v2-m3 model and tokenizer.
2. *Creating a Reranking Function*: Define a Python function rerank that takes a query and returns documents sorted by relevance score.
3. *Testing*: Demonstrate the rerank function with simple and more complex examples to show how the model's capability.

Sample reranking query results:
``` JSON
Query: What are the benefits of regular exercise?

Ranked Documents (most to least relevant):

1. Score: 6.7963
   Document: Regular exercise improves cardiovascular health, boosts mood, and helps maintain a healthy weight.

2. Score: 1.7936
   Document: Exercise has been shown to reduce the risk of chronic diseases such as diabetes and heart disease.

3. Score: 0.7743
   Document: Physical activity strengthens muscles and bones, and can improve sleep quality.

4. Score: -9.6014
   Document: Coffee contains caffeine which can improve alertness and concentration.

5. Score: -11.0410
   Document: The capital of France is Paris, which is known for its beautiful architecture.
```

## Part 3: BGE Reranker - Azure AI use
With `BGE_Reranker_AzureML.ipynb` you can deploy and run the model on Azure Machine Learning online endpoint.

Key steps include:
1. *Connecting to Azure ML*: Authenticating and establishing a connection to your Azure Machine Learning workspace.
2. *Finding the BGE Reranker Model*: Identifying the baai-bge-reranker-v2-m3 model within the Hugging Face registry in Azure ML.
3. *Deploying to Online Endpoint*: Creating a managed online endpoint and deploying the BGE Reranker model to it.
4. *Testing the Deployed Model*: Sending sample query and text data to the deployed endpoint and processing the reranker's response.
5. *Cleaning up Resources (Optional)*: Providing instructions for deleting the deployed endpoint and associated resources to avoid unnecessary costs.

Sample reranking query results:
``` JSON
================================================================================
PROCESSED RERANKING RESULTS:
================================================================================
Query: What is Deep Learning?
================================================================================
Rank Score      Text
================================================================================
1    0.999879   Deep learning is a subset of machine learning that uses neural network...
2    0.013742   Machine learning is a method of data analysis that automates analytica...
3    0.010945   Artificial intelligence is the simulation of human intelligence proces...
4    0.000142   Python is a high-level programming language widely used for web develo...

================================================================================
```

## Acknowledgements
- [BAAI](https://huggingface.co/BAAI) for developing the BGE Reranker v2 m3 model;
- [HuggingFace](https://huggingface.co/BAAI/bge-reranker-v2-m3) for hosting the model and providing the Transformers library;
- [Microsoft Azure](https://portal.azure.com) for cloud platform services.
