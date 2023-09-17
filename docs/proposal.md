## 1. Medical Named Entity Recognition

- Prepared for UMBC Data Science Master Degree Capstone by Dr Chaojie (Jay) Wang
- Author Name: Shraddha Sundaresan
- GitHub - <a href="https://github.com/Shraddha-boop"> shraddha </a>
- LinkedIn - <a href="https://www.linkedin.com/in/shraddha-sundaresan-676b8b93"> Shraddha Sundaresan </a>
- PowerPoint presentation file: TBD
- YouTube video: TBD
    
## 2. Background

### What is it about?
NER leverages its natural language understanding capabilities to assist researchers, healthcare professionals, and individuals in navigating the complex world of biomedical information.
It's like having a knowledgeable colleague or a helpful librarian who can effortlessly identify and organize disease-related knowledge, making it accessible, timely, and user-friendly
.
### Why does it matter?

The Medical NER is significant for several reasons:

**Biomedical Research:** NER streamlines research by automatically spotting disease-related insights in vast scientific literature. It saves time and ensures critical findings aren't overlooked, empowering researchers to stay updated and advance disease understanding.

**Clinical Applications:** In clinical settings, NER acts as a vigilant assistant, extracting disease mentions from patient records. This aids healthcare providers in swiftly accessing crucial patient information, enhancing decision-making, and delivering timely care while minimizing errors.

**Information Retrieval:** For information seekers, NER plays the role of an efficient librarian. It catalogues and retrieves relevant documents on specific diseases, simplifying searches and ensuring users quickly access accurate information from a sea of data.

### What are your research questions?

This project will focus on answering the following research questions:

1. What fine-tuning strategies (e.g., architecture modifications, training data, hyperparameter tuning) are most effective in optimizing the DilBERT model's performance for disease entity recognition?
2. How does the pretrained BioBert model leverage transfer learning to improve NER accuracy for disease entities compared to models trained from scratch?
3. Can the BioBert model be effectively adapted to recognize disease entities in specific subdomains of biomedicine, such as genetics, epidemiology, or clinical medicine?
4. How well does the BioBert-based NER model generalize to different types of texts, including research articles, clinical notes, and social media posts, while maintaining high accuracy?

## 3. Data 

Describe the datasets you are using to answer your research questions.

- **Source:** [Link](https://huggingface.co/datasets/ncbi_disease)
- **Size:** - 1.55 MB
- **Shape:** -
  - Train - 5433 rows
  - Validation - 924 rows
  - Test - 941 rows
 

#### Potential values (for categorical valuables, what are the categories?)

**id:** Sentence identifier.
**tokens:** Array of tokens composing a sentence.
**ner_tags:** Array of tags, where 0 indicates no disease mentioned, 1 signals the first token of a disease and 2 the subsequent disease tokens.

#### Which variable/column will be your target/label in your ML model?

This is a NER model

#### Which variables/columns may be selected as features/predictors for your ML models?

Using the ner tags and the pre-trained BioBert model
