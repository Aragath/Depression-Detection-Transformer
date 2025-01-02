# Automatic Depression Detection Using An Interpretable Audio-Textual Multi-modal Transformer-based Model

This repository contains the code for a research project focused on detecting depression through a multi-modal approach, utilizing both audio and textual data from clinical interviews. The model is based on a transformer architecture, leveraging the self-attention mechanism to improve both diagnostic accuracy and interpretability. The model outperforms baseline models and provides insights into key factors influencing depression diagnosis through attention analysis.

### Authors:
- Mehrshad Saadatinia (saadatin@usc.edu)
- Pin-Tzu Lee (pintzule@usc.edu)
- Sreya Reddy Chinthala (chinthal@usc.edu)
- Om Jodhpurkar (jodhpurk@usc.edu)
- Sneh Thorat (snehpram@usc.edu)

## Abstract
In this study, we propose a multi-modal transformer-based framework for the detection of depression using audio and text modalities from clinical interview data. Our approach leverages the self-attention mechanism in transformers and improves both diagnostic accuracy and interpretability. The proposed model achieves an average improvement of 4.5% in diagnostic accuracy for audio-textual depression detection on two benchmark datasets. By analyzing attention weights, we identify the most influential features in audio and text that drive the model’s predictions, offering valuable insights into key factors contributing to depression diagnosis.

## Introduction
Depression is a serious mental health disorder that often goes undiagnosed due to the challenges associated with traditional diagnostic methods. This project proposes an automated solution that combines audio and textual data from clinical interviews to improve the detection of depression. The proposed transformer-based model offers improved diagnostic accuracy and interpretability, with potential for use in clinical settings for early intervention.

## Datasets
We use the following two datasets for training and evaluation:

1. **DAIC-WOZ (Distress Analysis Interview Corpus Wizard-of-Oz)**  
   A dataset designed to aid in diagnosing psychological distress, including depression, anxiety, and PTSD. The dataset contains audio and text data annotated with depression labels based on PHQ-8 scores.  
   [Link to Dataset](https://dcapswoz.ict.usc.edu/)

2. **EATD (Emotional Audio-Textual Dataset Corpus)**  
   A dataset consisting of Chinese audio and text interview data with depression levels based on the SDS (Self-Rating Depression Scale). It includes both positive and negative sentiments for each subject.  
   [Link to Dataset](https://github.com/speechandlanguageprocessing/ICASSP2022-Depression)

## Methodology
We propose a multi-modal framework for depression detection that integrates audio and text features. The steps are as follows:

1. **Feature Extraction**  
   - **Text**: Use BERT embeddings to extract text features. Each subject’s sentence is represented by the mean of BERT word-level embeddings.
   - **Audio**: Represent audio through mel-spectrograms, then apply NetVLAD to extract embeddings.

2. **Model Architecture**  
   - Transformer encoders for both audio and text modalities.
   - Concatenate features from both modalities and pass through fully connected layers for classification.

3. **Interpretability**  
   - Analyze attention weights to understand the influential features in audio and text data that affect depression diagnosis.

## Results
In experiments conducted on the EATD dataset, our model achieved an F1 score of 0.84, outperforming baseline models, including text-only and audio-only LSTM models. The results demonstrate the effectiveness of the multi-modal transformer-based approach.

| Model | F1 Score |
|-------|----------|
| Audio LSTM | 0.80 |
| Text LSTM | 0.79 |
| Text & Audio Bi-LSTM & GRU + Attention | 0.71 |
| **Text & Audio Transformer (Proposed)** | **0.84** |