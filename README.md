# T5 Disfluency Cleaner

This repository contains a single notebook, `T5_Disfluency_Cleaner_E2E.ipynb`, which implements an end-to-end pipeline for cleaning disfluent questions using a fine-tuned T5-base model.

## Task

Given a disfluent question like:
"What do petrologists no what do unstable isotope studies indicate?"
The model outputs:
"What do unstable isotope studies indicate?"

## Workflow

- Performed EDA on Disfl-QA dataset (`train.json`, `dev.json`)
- Removed malformed entries (e.g. "#VALUE!")
- Renamed columns for clarity
- Trained T5-base using Hugging Face Transformers
- Logged training with Weights & Biases
- Evaluated using BLEU, ROUGE-L, and Exact Match
- Pushed model to Hugging Face Hub
- Demonstrated inference on sample disfluent questions

## Final Evaluation Metrics

eval_loss: 1.6394  
eval_bleu: 0.9087  
eval_rougeL: 0.9584  
eval_exact_match: 0.7342  

## Model

- Model: t5-base
- Training framework: Hugging Face Transformers + Datasets
- GPU: Google Colab with fp16 mixed precision
- Decoding: Beam search (num_beams=4)
- Regularization: weight decay + label smoothing

## Hugging Face Model

Model is available at: https://huggingface.co/abdulbaseermohammedkhan/t5_disfluent_cleaner

## Inference

At the end of the notebook, the model is loaded from the Hugging Face Hub and used to generate cleaned outputs from disfluent inputs.

## File Structure

- T5_Disfluency_Cleaner_E2E.ipynb — single notebook covering EDA, training, and inference
- data/ — contains train.json, dev.json, optionally test.json

## How to Run

1. Open the notebook in Colab or Jupyter
2. Run all cells top to bottom
3. Replace or extend sample inference as needed
4. Optionally load test.json and save predictions to CSV
