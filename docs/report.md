## 1. Title and Author

- **Project Title:** **Named Entity Recognition** - NER of NCBI(medical) data
- Prepared for UMBC Data Science Master Degree Capstone by Dr Chaojie (Jay) Wang
- **Author Name:** Shraddha Sundaresan
- **Semester** - Fall 2023
- <a href="https://github.com/Shraddha-boop"><img align="left" src="https://img.shields.io/badge/-GitHub-CD5C5C?logo=github&style=flat" alt="icon | GitHub"/></a> 
- <a href="https://www.linkedin.com/in/shraddha-sundaresan-676b8b93/"><img align="left" src="https://img.shields.io/badge/-LinkedIn-1E90FF?logo=linkedin&style=flat" alt="icon | LinkedIn"/></a>
- <a href="https://github.com/DATA-606-2023-FALL-MONDAY/Sundaresan_Shraddha/blob/main/docs/Presentation/Capstone.pptx"><img src="https://img.shields.io/badge/-PowerPoint Presentation Download-B7472A?logo=microsoftpowerpoint&style=flat" alt="icon | GitHub"/></a>  
- Link to your YouTube video - In progress
  
      
## 2. Background

NER leverages its natural language understanding capabilities to assist researchers, healthcare professionals, and individuals in navigating the complex world of biomedical information. It's like having a knowledgeable colleague or a helpful librarian who can effortlessly identify and organize disease-related knowledge, making it accessible, timely, and user-friendly.

The Medical NER is significant for several reasons:

**Biomedical Research:** NER streamlines research by automatically spotting disease-related insights in vast scientific literature. It saves time and ensures critical findings aren't overlooked, empowering researchers to stay updated and advance disease understanding.

**Clinical Applications:** In clinical settings, NER acts as a vigilant assistant, extracting disease mentions from patient records. This aids healthcare providers in swiftly accessing crucial patient information, enhancing decision-making, and delivering timely care while minimizing errors.

**Information Retrieval:** For information seekers, NER plays the role of an efficient librarian. It catalogues and retrieves relevant documents on specific diseases, simplifying searches and ensuring users quickly access accurate information from a sea of data.


### Research questions

This project will focus on answering the following research questions:

1. What fine-tuning strategies (e.g., architecture modifications, training data, hyperparameter tuning) are most effective in optimizing the BioBert model's performance for disease entity recognition?
2. How does the pretrained BioBert model leverage transfer learning to improve NER accuracy for disease entities compared to models trained from scratch?
3. Can the BioBert model be effectively adapted to recognize disease entities in specific subdomains of biomedicine, such as genetics, epidemiology, or clinical medicine?  


## 3. Data 

- **Source:** [Link](https://huggingface.co/datasets/ncbi_disease)  
- **Size:** - 1.55 MB 
- **Shape:** -
  - Train - 5433 rows
  - Validation - 924 rows
  - Test - 941 rows

  
| Column Name           | Description                                                   | Type             |
| ----------------------| ------------------------------------------------------------- | ----------------- |
| id                    | Unique identifier for each sentence                           | Numeric          |
| tokens                | List of words in each sentence                                | Plain Text       |
| ner_tags              | Array of tags  0 = No disease mentioned, 1 = First token of a disease, 2 = Subsequent disease tokens                      | Numeric    |


*Potential values:*

- **id:** Sentence identifier.
- **tokens:** Array of tokens composing a sentence.
- **ner_tags:** Array of tags
  - 0 = No disease mentioned 
  - 1 = First token of a disease 
  - 2 = Subsequent disease tokens

## 4. Data Wrangling
### Data Cleaning-

In this stage, we will preprocess the text by eliminating punctuation, special characters, and stop words, while also converting the text to lowercase. Subsequently, we will perform lemmatization to ensure accurate identification of similar occurrences of words. This is performed to the column "tokens" which constitute the words in the NCBI medical dataset.

### EDA-

In this phase, we create a WordCloud to analyze the prevalent words in the medical dataset. The size of the words in the visualization corresponds to their frequency, with larger words indicating higher occurrences.

![image](https://github.com/DATA-606-2023-FALL-MONDAY/Sundaresan_Shraddha/assets/55248640/02c0ba1c-c921-4709-b47f-51ec46343a69)

The visualization above indicates that the words "gene," "mutation," "patient," and "cancer," among others, are the most frequently occurring. Additionally, it can be observed from the visualization that the prevalent disease in the dataset is likely to be cancer.

## 5. Fine-tuning
### Tokenizing

The initial phase of fine-tuning involves tokenization, where the text in the "tokens" column is tokenized using the BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext pre-trained tokenizer. Additionally, the data undergoes truncation and padding to ensure a consistent sequence of vectors across the entire dataset.

### Model Evaluation

To assess the performance of our models, I will create a function that computes metrics such as accuracy, precision, recall, and F1-score. The `classification_report` function from scikit-learn will provide a comprehensive overview of the model's performance, including precision, recall, and F1-score for each class.

### Data Collator

A data collator collates batches of dict-like objects and performs special handling for potential keys named. For token classification task I made use of a dedicated DataCollatorForTokenClassification which expects a list of dicts, where each dict represents a single example in the dataset and dynamically pads the inputs recieved as well as the ner_tages.

### Parameters for training the model
1. NUM_OF_EPOCHS = 3

In this case, the model will iterate over the entire medical dataset three times during the training process.

2. BATCH_SIZE = 16

During each training step, 16 medical samples will be processed together to update the model's parameters.

3. STRATEGY = "epoch"

In this context, the strategy is set to "epoch," implying that certain actions or adjustments may take place after each epoch.

4. REPORTS_TO = "tensorboard"

The training progress and metrics will be reported to TensorBoard, a visualization tool for monitoring and analyzing the training process.

5. WEIGHT_DECAY = 0.01

A weight decay of 0.01 means that the optimization process will be biased towards smaller weights, helping prevent overfitting.

6. LR = 2e-5

The learning rate is set to 2e-5, indicating a relatively small step size to avoid overshooting the optimal parameters during training.

7. DEVICE = torch.device("cpu")

In this case, the model is set to train on the CPU, which might be suitable for smaller datasets or when GPU resources are limited.

8. STEPS = 35
The training process will involve 35 steps or batches of medical data before completing the specified number of epochs.


### Trainer Argument and Trainer Class

We can define the training parameters in the TrainingArguments and Trainer class as well as train the model with a single command.Next, we specify some training parameters, set the pretrained model, train data and evaluation data in the TrainingArgs and Trainer class.

After we have defined the parameters , simply run trainer.train() to train the model.

## 6. RESULT
On applying the trained model to the validation dataset it produces a confusion metrics as below-
![image](https://github.com/DATA-606-2023-FALL-MONDAY/Sundaresan_Shraddha/assets/55248640/86288a8c-ac19-4e25-9619-7f1afa8986a9)

| Metrics       | Validation                                                    | Train             |
| ----------------------| ------------------------------------------------------------- | ----------------- |
| Precision                    | 0.96                         | 0.95          |
| Recall                | 0.95                               | 0.93     |
| F1-Score              | 0.95                     | 0.94    |


