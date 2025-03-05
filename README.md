# Transformer-based-Speaker-Classification
This repository contains the code for a transformer-based approach to speaker classification. The task is to predict the speaker identity (among 600 speakers) from short audio segments, represented as sequences of extracted audio features. By leveraging self-attention mechanisms introduced in the paper "Attention Is All You Need", the model is able to capture global context efficiently.

![image](https://github.com/user-attachments/assets/cbd826f7-37b0-401a-9f5a-ed23deed809b)


Overview
Task: Multiclass classification (speaker identification)
Input: Audio features for each utterance (sequence data)
Output: Predicted speaker label (integer from 0 to 599)
Model: Transformer-based network utilizing self-attention
![image](https://github.com/user-attachments/assets/ec7c73e9-5976-4af2-9f97-87dee55e4dfe)


Data
Training Set: 62,464 utterances (each with a label indicating one of the 600 speakers)
Test Set: 6,944 utterances (no labels provided)
Each utterance is a sequence of preprocessed audio features. The model reads these features and outputs a predicted speaker ID.

Transformer Model
Self-Attention:
Allows the model to attend to different positions within the input sequence to learn context more effectively than a simple RNN or CNN.
Positional Encoding:
Injects sequence order information into the model, since self-attention alone does not inherently encode positional details.
Feedforward Layers:
Applied after the self-attention block, adding non-linearity and increasing model capacity.
Classification Head:
A final linear layer to map the pooled output or final hidden representation to a speaker class (0–599).
Training Procedure
Data Segmentation:

Each utterance is treated as a sequence of audio frames/features.
The model processes the sequence in parallel using self-attention.
![image](https://github.com/user-attachments/assets/db60e2ec-8f3b-4c5e-abba-c3bbad465421)


Loss & Optimization:

A cross-entropy loss is used for speaker classification.
The optimizer is typically Adam, balancing training speed and convergence.
Hyperparameter Tuning:

Number of transformer layers, hidden dimensions, and attention heads are adjusted to achieve better performance.
The training epochs are selected to ensure the model converges while avoiding overfitting.
Evaluation
Metric: Accuracy on the test set (i.e., the proportion of correctly predicted speaker labels).
Output Format:
A CSV file with two columns:
Id: uttr0, uttr1, uttr2, ...
Category: predicted speaker label (0, 1, 2, ...)
Code Structure
Notebook:
Week5_HW_ap2938 (1).ipynb – Contains:
Data loading and preprocessing.
Definition of the Transformer-based model with self-attention.
Training loop, including the cross-entropy loss function and optimizer setup.
Evaluation loop for measuring classification accuracy.
Generation of the final CSV submission file.
Getting Started
Clone the Repository & Install Dependencies:

Ensure you have a Python environment with the necessary libraries (e.g., PyTorch, NumPy).
Download the Data:

Obtain the training set (62,464 utterances) and test set (6,944 utterances).
Place them in the appropriate directory so the notebook can load them.
Run the Notebook:

Week5_HW_ap2938 (1).ipynb to train the transformer model and produce predictions.
Generate Submission:

The notebook will output a CSV file with the format:
Id,Category
uttr0,123
uttr1,45
...
Conclusion
By adopting a transformer-based model for speaker classification, we harness the power of self-attention to capture long-range dependencies in audio feature sequences. This approach can outperform or match more traditional RNN/CNN models in terms of both speed and accuracy. All the relevant code and experiments are provided in this repository.
