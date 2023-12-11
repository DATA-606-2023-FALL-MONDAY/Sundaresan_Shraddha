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

**id:** Sentence identifier.
**tokens:** Array of tokens composing a sentence.
**ner_tags:** Array of tags
  0 = No disease mentioned 
  1 = First token of a disease 
  2 = Subsequent disease tokens

