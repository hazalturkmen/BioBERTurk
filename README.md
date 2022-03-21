# BioBERTurk- Turkish Biomedical Language Models

BioBERTurk on Hugging Faces repo:

[BioBERTurkcased-(con)+(trM)](https://huggingface.co/hazal/BioBERTurkcased-con-trM): BioBERTurkcased-(con)+(trM), was pretrained only on [Turkish biomedical text](https://huggingface.co/datasets/hazal/Turkish-Biomedical-corpus) and applied the continual training approach, initializing weights from available general Turkish [BERTurk](https://github.com/stefan-it/turkish-bert).\
[BioBERTurkcased-(con)+(trM+trR)](https://huggingface.co/hazal/BioBERTurkcased-con-trM-trR): BioBERTurkcased-(con)+(trM+trR), was pretrained on Turkish biomedical text and [radiology thesis](https://huggingface.co/datasets/hazal/electronic-radiology-phd-thesis-trR/tree/main) and applied the continual training approach, initializing weights from available general Turkish [BERTurk](https://github.com/stefan-it/turkish-bert).

# Text classification Experiment in Turkish radiology dataset
To evaluate our model’s performance at the clinical text classification task, we created a dataset using an in-house corpus of 45,304 deidentified Turkish CT head radiology reports produced at Ege University Hospital, Turkey. The reports cover the period from 2016 to present. “impression” part were extracted from the original reports to prepare a labeled dataset. Before data analysis, we filtered out texts that have less than 300 characters and removed newlines and domain specific encodings. After the cleaning process, the final dataset had 3749 reports, 59,157 sentences and 764,848 words. 

The annotation schema included three classes- ”Presence of Intracranial Pathology (Abnormal)”, ”No Intracranial Pathology (Normal)” and ”Out of Series”, respectively, to indicate the presence or absence of an intracranial medical abnormality and not to be included in the evaluation of intracranial pathology. This study was approved by the Ege University Ethical Committee with reference number: 21-11T/11.

All Fine-tuned models are available in the Hugging Faces repository.
