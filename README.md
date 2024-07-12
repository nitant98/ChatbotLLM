
# LOTR Conversational RAG Chatbot

This project is a Conversational Retrieval-Augmented Generation (RAG) Chatbot designed to answer questions about J.R.R. Tolkien's "The Lord of the Rings". The chatbot utilizes a combination of a pre-trained language model and a vector store for document retrieval to provide accurate and contextually relevant answers.

## Table of Contents
- [Overview](#overview)
- [Project Structure](#project-structure)
- [Setup Instructions](#setup-instructions)
- [Usage](#usage)
- [Debugging and Logs](#debugging-and-logs)

## Overview

The chatbot leverages the following components:
- **LangChain**: To create and manage the retrieval and generation chains.
- **Pinecone**: For storing and retrieving document embeddings.
- **HuggingFace Transformers**: For the language model and embeddings.
- **Streamlit**: To create the web interface for the chatbot.

## Project Structure

```
.
├── LOTR_books/
│   └── Tolkien-J.-The-lord-of-the-rings-HarperCollins-ebooks-2010.pdf
├── app.py
├── config.py
├── create_embeddings.py
├── model_setup.py
├── qa_setup.py
├── requirements.txt
└── README.md
```

### Files
- **`LOTR_books/`**: Directory containing the LOTR PDF book.
- **`app.py`**: Streamlit application file to run the chatbot interface.
- **`config.py`**: Configuration file for setting parameters.
- **`create_embeddings.py`**: Script to create and store document embeddings in Pinecone.
- **`model_setup.py`**: Script to set up the language model and HuggingFace pipeline.
- **`qa_setup.py`**: Script to set up the QA chain and handle query processing.
- **`requirements.txt`**: Contains the list of dependencies.
- **`README.md`**: This file.

## Setup Instructions

### Prerequisites
Ensure you have Python 3.8 or higher installed. You'll also need a Pinecone account and API key.

### Install Dependencies

```sh
pip install -r requirements.txt
```

### Configure Pinecone
Create an index in Pinecone with a dimension matching your embeddings (e.g., 768 for sentence-transformers/all-MiniLM-L6-v2).

Set your Pinecone API key and environment in your environment variables:

```sh
export PINECONE_API_KEY="your-api-key"
export PINECONE_ENV="your-environment"
```

### Create Embeddings
Run the create_embeddings.py script to process the LOTR PDF and store the embeddings in Pinecone.

```sh
python create_embeddings.py
```

### Start the Streamlit App
Run the Streamlit app to start the chatbot interface.

```sh
streamlit run app.py
```

## Usage
1. Open the Streamlit app in your browser.
2. Enter a question about "The Lord of the Rings" in the input field.
3. Click the "Ask" button to get an answer from the chatbot.

## Debugging and Logs
The `llm_ans` function in `qa_setup.py` includes debug statements to help identify issues. If you encounter errors, check the console output for detailed logs.

## Tasks

### 1. Domain Selection
- **Domain**: "The Lord of the Rings" (LOTR)
- **Scope**: Questions related to the LOTR books by J.R.R. Tolkien.

### 2. Data Collection and Preprocessing
- **Data Collection**: The LOTR books in PDF format.
- **Preprocessing Steps**:
  - Loaded the PDF using PYPDF and extracted text.
  - Cleaned the text by removing irrelevant information.
  - Handled any missing data.
  - Ensured the text is in a suitable format for the language model.

### 3. Vector Database Implementation
- **Database**: Pinecone
- **Implementation Steps**:
  - Created an index in Pinecone.
  - Stored the preprocessed dataset in Pinecone.
  - Ensured data is indexed for efficient retrieval based on semantic similarity.

### 4. Application Development
- **User Interface**: Streamlit
- **Backend Logic**:
  - Used GPT-3.5-turbo language model for query processing.
  - Retrieved data from the vector database.
  - Ensured the system returns relevant and accurate results.

