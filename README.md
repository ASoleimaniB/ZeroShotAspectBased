# Zero-Shot Aspect-Based Scientific Document Summarization using Self-Supervised Pre-training

This work has been accepted at BioNLP2022 at ACL2022. The paper will be added soon.

**Authors:** Amir Soleimani, Vassilina Nikoulina, Benoit Favre, Salah Ait-Mokhtar \
This work was done during Amir's internship at NAVER LABS Europe.

**Abstract:**
We study the zero-shot setting for the aspect-based scientific document summarization task. Summarizing scientific documents with respect to an aspect can remarkably improve document assistance systems and readers experience. However, existing large-scale datasets contain a limited variety of aspects, causing summarization models to over-fit to a small set of aspects and a specific domain. We establish baseline results in zero-shot performance (over unseen aspects and the presence of domain shift), paraphrasing, leave-one-out, and limited supervised samples experimental setups. We propose a self-supervised pre-training approach to enhance the zero-shot performance. We leverage the PubMed structured abstracts to create a biomedical aspect-based summarization dataset. Experimental results on the PubMed and FacetSum aspect-based datasets show promising performance when the model is pre-trained using unlabelled in-domain data.

## Dataset
For PubMed, you can get the data from https://github.com/armancohan/long-summarization or simply use the Huggingface datasets framework. Getting the FacetSum dataset is more complicated. You need to crawl it yourself because of copyright issues. A part of the dataset is open access, but you need subscriptions typically provided by your institute to get the complete data. Check https://github.com/hfthair/emerald_crawler


# Installation

        conda install pytorch==1.9.0 torchvision==0.10.0 torchaudio==0.9.0 cudatoolkit=10.2.89 -c pytorch
        pip install git+https://github.com/huggingface/transformers/releases/tag/v4.10.0.dev (install from source, 4.10.0.dev0)
        pip install datasets 
        pip install nltk
        pip install beautifulsoup4
        pip install lxml
        
        
