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
- Python 3.11+
- `pip` Python package installer
- GPU recommended for faster inference.

## Part 1: Configuring Environment
This section outlines setting up your local environment for the BGE Reranker v2 m3 model using `BGE_Reranker_Local.ipynb`.
1.1 Installation

Install necessary packages:

```bash
pip install transformers torch
```
Use code with caution.
Markdown
1.2 Loading the BGE Reranker Model
Load the BAAI/bge-reranker-v2-m3 model and its tokenizer, automatically utilizing GPU if available.
import torch
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model_name = "BAAI/bge-reranker-v2-m3"
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForSequenceClassification.from_pretrained(model_name)

device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
model = model.to(device)
print(f"Using device: {device}")
Use code with caution.
Python
1.3 Creating a Reranking Function
A rerank function processes a query and documents, returning them sorted by relevance score.
def rerank(query, documents, model, tokenizer, device, top_n=None):
    pairs = [[query, doc] for doc in documents]
    with torch.no_grad():
        inputs = tokenizer(pairs, padding=True, truncation=True, return_tensors="pt", max_length=512).to(device)
        # The model outputs logits. For BGE reranker, a higher logit means more relevant.
        scores_tensor = model(**inputs).logits.flatten() # Use .flatten() if batch size is 1 or you want all scores in a 1D tensor
        # Or use .squeeze(-1) if you are sure the output is [batch_size, 1] and want [batch_size]
        # For multiple pairs, logits might be [num_pairs, num_classes (1 for reranker)]
        # .logits gives [batch_size, 1] for this model, so .flatten() or .squeeze() works.
        scores = scores_tensor.cpu().tolist()

    doc_score_pairs = list(zip(documents, scores))
    # Sort by score in descending order
    ranked_results = sorted(doc_score_pairs, key=lambda x: x[1], reverse=True)
    
    return ranked_results[:top_n] if top_n is not None else ranked_results
Use code with caution.
Python
Part 2: Local use
2.1 Testing with a Simple Example
Demonstrates reranking a set of documents for the query "What are the benefits of regular exercise?".
Query: "What are the benefits of regular exercise?"
Expected Top Ranked Document (Illustrative): "Regular exercise improves cardiovascular health, boosts mood, and helps maintain a healthy weight." (Actual document will depend on the list provided to the reranker).
2.2 Testing with a More Complex Example
Illustrates the reranker's capability with a more specific query: "What programming language is best for machine learning?".
Query: "What programming language is best for machine learning?"
Expected Top Ranked Document (Illustrative): "Python is widely regarded as the leading programming language for machine learning due to its extensive libraries like Scikit-learn, TensorFlow, and PyTorch." (Actual document will depend on the list provided to the reranker).
Part 3: Azure AI use
(Details to be completed in BGE_Reranker_AzureML.ipynb - This section will cover deploying and running the model on Azure Machine Learning services, including environment setup, script creation for inference, model registration, endpoint deployment, and testing the deployed endpoint.)
Acknowledgements
Special thanks to:
BAAI for developing the BGE Reranker v2 m3 model.
HuggingFace for hosting the model and providing the Transformers library.
Microsoft Azure for their cloud platform services.
**Key changes and considerations:**

*   **Model Card Link:** I've made the model card text a proper hyperlink.
*   **Table of Contents Links:** The links in the Table of Contents (`[Section Name](#section-name)`) will work with GitHub's automatic anchor generation for headings.
*   **Code Blocks:**
    *   The `pip install` command is in a `bash` block (more appropriate than just `!pip` from Jupyter).
    *   Python code blocks are marked with `python`.
*   **Rerank Function:** I've added a small comment in the `rerank` function regarding `logits.flatten()` vs `logits.squeeze(-1)` as this can sometimes be a point of confusion depending on the exact model output shape (though for rerankers, it's typically `[batch_size, 1]`, making `flatten()` or `squeeze()` fine).
*   **Part 2 Examples:** The "Top Ranked Document" lines are presented as illustrative descriptions, as the actual output depends on the input documents provided to the function in the notebook. I've slightly rephrased one to be more typical.
*   **Part 3 Placeholder:** I've expanded the placeholder text for Part 3 slightly to give a better idea of what it might contain.
*   **Acknowledgements:** Formatted as a bulleted list for better readability.
