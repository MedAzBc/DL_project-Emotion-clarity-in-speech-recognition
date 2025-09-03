# Speech Emotion Recognition — VAE + Diffusion (CRISP-DM) with Streamlit

This project reproduces the methodology from the paper *“A Generation of Enhanced Data by Variational Autoencoders and Diffusion Modeling” (Electronics, March 2024)* to improve emotion clarity in speech recognition. We work with *EmoDB* (German) and *RAVDESS* (English) and deploy an interactive *Streamlit* app for inference and demos.

---

## Objectives

* Reproduce the paper’s pipeline: data preparation → VAE representation learning → conditional diffusion generation → downstream classifier evaluation.
* Implement and evaluate additional models (e.g., CNN/ResNet/EfficientNet baselines) for comparison.
* Explain the used architectures and training choices.
* Evaluate with loss/accuracy and provide clear validation/test reporting.
* Package an annotated notebook following *CRISP-DM*.

---

## Datasets

* *EmoDB* — German emotional speech dataset.
* *RAVDESS* — English emotional speech dataset.

Data are preprocessed into *mel-spectrograms* and standardized to a common sampling/config for joint training and evaluation.

---

## Methodology (CRISP-DM)

1. *Business Understanding*

   * Goal: enhance emotion clarity and recognition performance using generative modeling.
   * Success: improved accuracy on held-out emotion labels and clearer class separation.
2. *Data Understanding*

   * Inspect class balance, speaker distribution, recording conditions.
   * Validate label mapping across EmoDB and RAVDESS.
3. *Data Preparation*

   * Audio loading, resampling, trimming/silence handling.
   * Mel-spectrogram feature extraction; normalization; train/val/test split (speaker-aware where applicable).
4. *Modeling*

   * *VAE*: latent bottleneck for compact, emotion-aware embeddings.
   * *Conditional Diffusion*: generate enhanced samples/features conditioned on emotion embeddings.
   * *Baselines*: CNN/ResNet/EfficientNet and a simple ANN for comparison.
5. *Evaluation*

   * Loss and accuracy across epochs; final test metrics.
   * Optional: t-SNE/PCA of embeddings to visualize emotion separability.
6. *Deployment*

   * Streamlit UI for uploading audio, visualizing mel-spectrograms, running inference, and comparing real vs. generated/enhanced representations.
