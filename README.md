# Two-Stage BERT for Sports News Classification Using LLM

## Table of Contents
1. [Project Description](#project-description)
2. [Data Collection and Scraping](#data-collection-and-scraping)
3. [Methodology](#methodology)
4. [Model Architecture](#model-architecture)
5. [Training and Evaluation](#training-and-evaluation)
6. [Results](#results)
7. [Conclusion](#conclusion)
8. [License](#license)

## Project Description
This project focuses on classifying sports news articles into categories such as **Liga Inggris**, **Liga Indonesia**, **Liga Spanyol**, **Liga Italia**, and **Olahraga Non Sepak Bola** using two approaches. The first model (**LLM 1-Stage**) classifies all five categories in one model, while the second model (**LLM 2-Stage**) classifies the articles in two stages: the first stage distinguishes between football and non-football news, and the second stage further classifies football news into specific leagues.

Data was scraped from prominent news websites like **Liputan6.com**, **Detik.com**, and **Antaranews.com**, and the model uses **Large Language Models (LLM)** for text classification, specifically leveraging **BERT**.

## Data Collection and Scraping
The data for this project was scraped from the following news websites:
- **Liputan6.com**
- **Detik.com**
- **Antaranews.com**

A web scraper was used to collect articles with the following categories:
- **Liga Inggris** (English Premier League)
- **Liga Indonesia** (Indonesian League)
- **Liga Spanyol** (Spanish League)
- **Liga Italia** (Italian League)
- **Olahraga Non Sepak Bola** (Non-football Sports)

The data was then processed and structured into a format suitable for training the models.

## Methodology
![Flowchart Methodology](https://github.com/user-attachments/assets/bf83d454-39bc-44fa-bec4-20e076fca56c)

1. **Web Scraping**: Data was collected from the specified news sources using Python libraries like `BeautifulSoup`.
2. **Data Preprocessing**: The text data was cleaned, tokenized, and lemmatized to remove unnecessary characters and ensure consistency.
3. **Modeling**:
   - **LLM 1-Stage**: This model directly classifies articles into five categories: **Liga Inggris**, **Liga Indonesia**, **Liga Spanyol**, **Liga Italia**, and **Olahraga Non Sepak Bola**.
   - **LLM 2-Stage**:
     - **Stage 1**: This stage classifies the articles into two groups: **Sepak Bola** (Football) and **Non Sepak Bola** (Non-football Sports).
     - **Stage 2**: For articles classified as **Sepak Bola**, this stage further classifies them into one of four football leagues: **Liga Inggris**, **Liga Indonesia**, **Liga Spanyol**, or **Liga Italia**.

## Model Architecture
![Bert-Base-Uncased-Architecture](https://github.com/user-attachments/assets/00300ca7-b4fd-42f8-999c-b7e1b77f67b1)

The project uses **BERT (Bidirectional Encoder Representations from Transformers)**, a state-of-the-art language model, for both stages of classification:
- **Stage 1 (LLM 2-Stage)**: The BERT model classifies articles as **Sepak Bola** (Football) or **Non Sepak Bola** (Non-football).
- **Stage 2 (LLM 2-Stage)**: For football-related articles, a second BERT model classifies them into one of the football leagues (Liga Inggris, Liga Indonesia, Liga Spanyol, Liga Italia).
- **LLM 1-Stage**: A single BERT model classifies all articles into one of the five categories (including both football and non-football news) in one step.

**Input**: News article text.  
**Output**: The predicted category: either **football vs non-football** in the first model or one of the five categories in the second model.

## Training and Evaluation
The dataset was split into **Training (70%)**, **Validation (15%)**, and **Test (15%)** sets. The model was trained using the **HuggingFace transformers** library, and performance was evaluated using the following metrics:
- **Accuracy**
- **Precision**
- **Recall**
- **F1 Score**

The confusion matrices for both models show the classification performance across all stages.

## Results
![Evaluation Table](https://github.com/user-attachments/assets/64170f55-b705-49ef-9679-008775fbbb03)

### **1-Stage BERT Model (Classifying All Labels)**
The **LLM 1-Stage model** classifies all 5 categories in one model.

**Confusion Matrix for LLM 1-Stage Model:**
- **Accuracy**: 92.41% (Test)
- **Precision**: 93.08% (Test)
- **Recall**: 92.41% (Test)
- **F1 Score**: 92.57% (Test)

![CF One Stage](https://github.com/user-attachments/assets/d1ab846f-1aff-4a0c-b592-86678a5cb5d7)

### **2-Stage BERT Model**
The **LLM 2-Stage model** performs classification in two stages.

**Confusion Matrix for LLM 2-Stage Model (Stage 1 - Football vs Non-football):**
- **Accuracy**: 100% (Test)

**Confusion Matrix for LLM 2-Stage Model (Stage 2 - Football Category Classification):**
- **Liga Inggris**: 94.08% (Test)
- **Liga Indonesia**: 96.83% (Test)
- **Liga Spanyol**: 90.94% (Test)
- **Liga Italia**: 91.32% (Test)

![CF Two Stage](https://github.com/user-attachments/assets/7d44c78e-2ba6-440d-93b8-2f41e948b115)

## Conclusion
This project demonstrates the effectiveness of using a **Two-Stage BERT model** for sports news classification. The **LLM 1-Stage model** efficiently classifies all categories in a single step, while the **LLM 2-Stage model** provides more granular classification for football-related articles. Both models achieve high accuracy, with the **two-stage model** performing particularly well in distinguishing between football and non-football news and further classifying football articles into the correct leagues.

Future improvements could include:
- Expanding the dataset with more diverse sources of sports news.
- Fine-tuning the BERT models with domain-specific data.
- Exploring other techniques like multi-task learning to improve performance across both stages.

## License

This project is licensed under the [MIT License](LICENSE). You are free to use, modify, and distribute this project as long as proper attribution is given to the original author.

