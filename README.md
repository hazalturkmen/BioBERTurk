# BioBERTurk- Turkish Biomedical Language Models

BioBERTurk on Hugging Faces repo:

[BioBERTurkcased-(con)+(trM)](https://huggingface.co/hazal/BioBERTurkcased-con-trM): BioBERTurkcased-(con)+(trM), was pretrained only on [Turkish biomedical text](https://huggingface.co/datasets/hazal/Turkish-Biomedical-corpus-trM) and applied the continual training approach, initializing weights from available general Turkish [BERTurk](https://github.com/stefan-it/turkish-bert).\
[BioBERTurkcased-(con)+(trM+trR)](https://huggingface.co/hazal/BioBERTurkcased-con-trM-trR): BioBERTurkcased-(con)+(trM+trR), was pretrained on Turkish biomedical text and [radiology thesis](https://huggingface.co/datasets/hazal/electronic-radiology-phd-thesis-trR/tree/main) and applied the continual training approach, initializing weights from available general Turkish [BERTurk](https://github.com/stefan-it/turkish-bert).

# Text classification Experiment in Turkish radiology dataset
To evaluate our model’s performance at the clinical text classification task, we created a dataset using an in-house corpus of 45,304 deidentified Turkish CT head radiology reports produced at Ege University Hospital, Turkey. The final dataset had 3749 reports, 59,157 sentences and 764,848 words.

The annotation schema included three classes- ”Presence of Intracranial Pathology (Abnormal)”, ”No Intracranial Pathology (Normal)” and ”Out of Series”, respectively, to indicate the presence or absence of an intracranial medical abnormality and not to be included in the evaluation of intracranial pathology. This study was approved by the Ege University Ethical Committee with reference number: 21-11T/11.

All Fine-tuned models are available in the Hugging Faces repository.

|   Labels  | Metric |   Berturk |         | Bioberturk(con) |               |   Bioberturk(sc)  | mBert(cased) |
|:---------:|:------:|:---------:|:-------:|:----------------:|:-------------:|:-----------------:|:------------:|
|           |        |  +trW(c)  | +trW(u) |      +trM(c)     | +(trM+trR)(c) | +(trW+trM+trR)(u) |              |
|   Normal  |   F1   |   94.24%  |  94.10% |    **94.97%**    |     94.80%    |       92.13%      |    93.63%    |
|  Abnormal |   F1   |   90.61%  |  91.01% |    **93.02%**    |     92.84%    |       89.33%      |    91.06%    |
| Out of Series |   F1   |   85.39%  |  82.95% |    **85.91%**    |     85.29%    |       80.33%      |    84.15%    |
|  Model F1 score |        |   91.86%  |  91.48% |    **92.99%**    |     92.75%    |       89.48%      |    91.42%    |

For each model, we performed hyperparameters searches for learning rate values ϵ {2e-4, 3e-5, 5e-5}, max sequence length ϵ {128, 256, 512}, batch size ϵ {16, 32} and the number of the training ϵ {3, 4, 5}. Batch size 64 was not utilized due to the memory limitations. 
Following table presents the hyperparameters and their tested options.



|  Parameter |      Settings      |   Berturk(cased) |   Berturk (uncased) | Bioberturk(cont) +trM | Bioberturk(con) +(trM+trR) | Bioberturk(sc)+ | mBert(cased) |
|:----------:|:------------------:|:----------------:|:----------------:|:------------------------:|:------------------------------:|:-------------------------------:|:--------------:|
| Batch size |      [16, 32]      |        32        |        32        |            16            |               16               |                32               |       16       |
| Max Length |     [256, 512]     |        256       |        512       |            256           |               256              |               256               |       256      |
|     LR     | [2e-5, 3e-5, 5e-5] |       5e-5       |       5e-5       |           2e-5           |              5e-5              |               5e-5              |      2e-5      |
|    Epoch   |      [3, 4, 5]     |         5        |         4        |             5            |                5               |                5                |        3       |
|  F1 score  |                    |      91.86%      |      91.48%      |        **92.99%**        |             92.75%             |              89.48%             |     91.42%     |




#  How to use model

# Acknowledgements
We would like to acknowledge the support we received from the Tensorflow Research Cloud (TRC) team in providing access to TPUv3 units.
