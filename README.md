# Zero-Shot Aspect-Based Scientific Document Summarization using Self-Supervised Pre-training

This work has been accepted at BioNLP2022 at ACL2022. The paper will be added soon.

**Authors:** Amir Soleimani, Vassilina Nikoulina, Benoit Favre, Salah Ait-Mokhtar \
This work was done during Amir's internship at NAVER LABS Europe.

**Abstract:**
We study the zero-shot setting for the aspect-based scientific document summarization task. Summarizing scientific documents with respect to an aspect can remarkably improve document assistance systems and readers experience. However, existing large-scale datasets contain a limited variety of aspects, causing summarization models to over-fit to a small set of aspects and a specific domain. We establish baseline results in zero-shot performance (over unseen aspects and the presence of domain shift), paraphrasing, leave-one-out, and limited supervised samples experimental setups. We propose a self-supervised pre-training approach to enhance the zero-shot performance. We leverage the PubMed structured abstracts to create a biomedical aspect-based summarization dataset. Experimental results on the PubMed and FacetSum aspect-based datasets show promising performance when the model is pre-trained using unlabelled in-domain data.

## Dataset
For PubMed, you can get the data from https://github.com/armancohan/long-summarization or simply use the Huggingface datasets framework. Getting the FacetSum dataset is more complicated. You need to crawl it yourself because of copyright issues. A part of the dataset is open access, but you need subscriptions typically provided by your institute to get the complete data. Check https://github.com/hfthair/emerald_crawler


## Installation

        conda install pytorch==1.9.0 torchvision==0.10.0 torchaudio==0.9.0 cudatoolkit=10.2.89 -c pytorch
        pip install git+https://github.com/huggingface/transformers/releases/tag/v4.10.0.dev (install from source, 4.10.0.dev0)
        pip install datasets 
        pip install nltk
        pip install beautifulsoup4
        pip install lxml
        
        
## Train and Test

        python -u run_summarization.py \
        --model_name_or_path facebook/bart-base  \
        --aspect_based \
        --do_predict \
        --train_file trainfile.json \
        --validation_file validationfile.json \
        --test_file testfile.json \
        --text_column text \
        --summary_column abstract \
        --aspect_column aspect \
        --output_dir /output/dir \
        --per_device_train_batch_size=8 \
        --per_device_eval_batch_size=4 \
        --overwrite_output_dir \
        --overwrite_cache \
        --predict_with_generate \
        --gradient_accumulation_steps 4 \
        --num_train_epochs 2 \
        --save_strategy "epoch" \
        --learning_rate=3e-04 \
        --weight_decay=0.01 \
        --max_grad_norm=0.1 \
        --lr_scheduler_type=polynomial \
        --warmup_steps=500 \
        --label_smoothing_factor=0.1 \
        --max_target_length=256 \
        --max_source_length=1024 \
