## **Overview**
This repository contains solutions for two tasks assigned during the Vijayi WFH Internship:

Task 1: Ticket Classification & Entity Extraction
Task 2: Quote Retrieval System using Semantic Search (Offline JSONL Version)

Both tasks were completed using Python and popular open-source libraries. I worked primarily in Google Colab for ease of package installation, data handling, and experimentation.

# **Task 1: Ticket Classification & Entity Extraction**

For Task 1, the goal was to analyze customer support tickets and automatically predict two things:

Issue type (e.g., delivery problem, product defect)
Urgency level (e.g., high, medium, low)

Additionally, I built a simple system to pull out important details (entities) from the ticket text — like product names, relevant dates, and complaint keywords.

**How it works**

Loaded the Excel dataset containing 1000+ tickets.

Cleaned and preprocessed the text by removing punctuation, converting to lowercase, removing stop words, and lemmatizing words to their root forms.

Converted text to numerical features using TF-IDF vectorization.

Added extra features like ticket length and sentiment polarity.

Trained two models: Logistic Regression for issue classification, and Random Forest for urgency classification.

Built a function to extract entities such as product names (matching known products), dates (using regex), and complaint keywords.

Created a combined inference function to predict both labels and extract entities for any new ticket text.

Tested the system on sample tickets to verify performance.

**How to run**

Run the Python notebook or script that contains the code.

Make sure to have the dataset file ai_dev_assignment_tickets_complex_1000.xls in your environment.

The notebook is set up to install and import all required libraries.

You can test the inference function by passing your own ticket text.

# **Task 1 Output**

--- Issue Type Classification Report ---
                    precision    recall  f1-score   support

    Account Access       1.00      1.00      1.00        23
   Billing Problem       0.95      1.00      0.97        19
   General Inquiry       1.00      1.00      1.00        25
Installation Issue       1.00      1.00      1.00        29
     Late Delivery       1.00      1.00      1.00        17
    Product Defect       1.00      0.97      0.98        30
        Wrong Item       1.00      1.00      1.00        23

          accuracy                           0.99       166
         macro avg       0.99      1.00      0.99       166
      weighted avg       0.99      0.99      0.99       166


--- Urgency Level Classification Report ---
              precision    recall  f1-score   support

        High       0.36      0.30      0.33        66
         Low       0.28      0.40      0.33        43
      Medium       0.35      0.30      0.32        57

    accuracy                           0.33       166
   macro avg       0.33      0.33      0.33       166
weighted avg       0.33      0.33      0.33       166


Test Ticket Analysis Result:
{'issue_type': 'Product Defect', 'urgency_level': 'Low', 'entities': {'product': None, 'dates': ['2024-12-01'], 'keywords': ['late']}}
Gradio not installed or running in non-Colab environment.




# **Task 2: Semantic Quote Retrieval System (Offline JSONL Version)**

Task 2 involved building a search system to find relevant quotes based on the meaning of a user’s query. Unlike keyword search, this uses semantic similarity so it understands the context and intent behind the query.

**How it works**

Loaded a local JSONL file containing quotes, authors, and tags.

Cleaned the quotes by removing line breaks and lowercasing.

Used a pretrained SentenceTransformer model to convert each quote into a vector embedding.

Created a FAISS index to quickly search for quotes with embeddings similar to the user’s query embedding.

Wrote a search function to return the top matching quotes for any query.

Built a Streamlit app script that runs locally, providing a neat interface for users to enter queries and get results.

**How to run**

Upload your quotes.jsonl file to the working directory or Google Colab.

Run the notebook cells to:

Install dependencies (faiss-cpu, sentence-transformers, etc.)

Load and preprocess data

Build embeddings and FAISS index

Test the search function with sample queries

Save the cleaned dataset (quotes.csv) and Streamlit app script (streamlit_quote_app.py)

