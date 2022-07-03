# Binary_Classification_on_Text_for_Voting
The purpose of this competition is to build a binary classification model to predict whether the given text could get large voting numbers or small ones. The metric of performance is accuracy.

**Kaggle Competition LINK**: https://www.kaggle.com/competitions/bt5153-applied-machine-learning-2022

## Techniques
- Feature Engineering: Simple Vectorization, Word2Vector, Bert Transformer
- Classification Models: NB, LR, RF, SVM, XGBoost, NN, and CNN

## Content
In this project, several different combinations of data preprocessing, feature engineering, validation methods, and classification models have been tried. In this paper, different methods in each stage will be elaborated on in advance. Then, the whole process of exploratory will be introduced. In the end, the final model with the best performance will be shown.

## Exploration Process
- **First Try:** Use improved cleaning for word-level and basic cleaning for W2V and Bert, split the training datasets before feature engineering, and conduct oversampling. The combination of word-level and CNN can only reach about 0.68 (in the validation set, same below), while the W2V with CNN could reach 0.72 and Bert with NN could reach 0.71. In the following steps, I stop exploring on the word-level model.
- **Second Try:** Because I found sometimes in the first several epochs the loss of validation is lower than the loss of training, which might be the problem of data augmentation. Therefore, I decided to remove the oversampling.
- **Third Try:** The limited accuracy might be because the information remaining is not enough. So, I start to test on easy cleaning and no preprocessing and split the training dataset after feature engineering. The performance of W2V with CNN improves a little.
- **Fourth and Fifth Try:** In order to keep more information after feature engineering, I ignore the data leakage problem and use both training and test texts to do feature engineering. Use no preprocessing strategy on the fourth try and use easy preprocessing on the fifth try. In this case, the performance of LR (chosen as one of the final submissions) with Bert reaches 0.73. 
- **Sixth Try:** Try to explore other packages for Bert. Use Simpletransformers and Kashgari. Ironically, the Simpletransformers outperforms all the previous models as a black box, which is chosen as the final model with the best performance of 0.75.

## Some thoughts
Regardless of the final black-box algorithm, there is some step in my exploratory process that cannot be reproduced in the practical application. For example, I use the whole corpus to train the W2V, which is a kind of data leakage. But in reality, if we want to predict something in the future we won’t get the information. So, a better way might be to use a pre-trained model and to conduct fine-tune.

## Collaborators
Nanhai Zhong
