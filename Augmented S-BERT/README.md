# Augmented SBERT (AugSBERT)

Augmented SBERT (AugSBERT) is a method designed to enhance Bi-encoder models by leveraging Cross-encoders to label or augment training datasets. It is particularly useful in scenarios with limited or no labeled data, helping improve the model's performance in sentence pair similarity tasks.

## Key Scenarios for AugSBERT Application

### 1) Full Labeled Datasets:

When you have a fully annotated dataset, you can apply word-level data augmentation techniques, such as using contextual word embeddings (BERT, RoBERTa) or lexical resources (e.g., WordNet), to generate diverse sentence pair variations. These augmented pairs are then added to the training dataset to help the Bi-encoder generalize better.

### 2) Few Annotated Samples:

For limited labeled data, AugSBERT uses Cross-encoders to weakly label a larger set of unlabeled sentence pairs, creating a "silver" dataset. These weak labels are then used to augment the small gold dataset, allowing the Bi-encoder to train on a larger dataset and improve performance, even with limited annotations.

### 3) No Annotated Samples:

In scenarios with no labeled data, a Cross-encoder is first trained on a related source domain with annotated sentence pairs (e.g., Quora Question Pairs). This model is then used to label sentence pairs in the target domain, creating weak labels. The Bi-encoder is then fine-tuned on this pseudo-labeled data, enabling it to handle tasks in domains with no direct annotations.

## Key Steps for AugSBERT

### 1)  Data Augmentation:

For fully labeled datasets, generate augmented sentence pairs by substituting words using contextual embeddings or lexical resources. These augmented pairs are added to the original dataset to improve the Bi-encoder’s ability to generalize.

### 2) Cross-Encoder Fine-Tuning:

For small labeled datasets, fine-tune a Cross-encoder (e.g., BERT) to predict sentence similarity. Use this model to label a larger set of unlabeled sentence pairs, generating a weakly labeled dataset for further training.

### 3) Bi-Encoder Training:

Train the Bi-encoder (e.g., SBERT) on the combined "gold" (human-labeled) and "silver" (weakly labeled) datasets to enhance its performance.

## Advantages

- Enhanced Performance with Limited Data: AugSBERT helps Bi-encoders perform better even with limited labeled data by using weak labels from Cross-encoders.
- Efficient Inference: While Cross-encoders are used for training, Bi-encoders provide efficient inference for real-time applications.
- Flexible for Various Scenarios: AugSBERT can handle fully labeled, partially labeled, and even completely unlabeled datasets.
- AugSBERT is a powerful technique that significantly boosts the performance of Bi-encoders, even in data-scarce situations, making it a great choice for tasks involving sentence pair similarity or semantic textual similarity.
