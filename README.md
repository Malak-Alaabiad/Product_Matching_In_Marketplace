# Product Name Similarity and Classification Using NLP

This project processes and matches product names from a seller's dataset to a master reference file using Natural Language Processing (NLP) techniques. The goal is to calculate the similarity between products using various methods like cosine similarity, fuzzy matching, and Levenshtein distance, and to assign the correct SKU (Stock Keeping Unit) from the master file.

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
- [Data Preprocessing](#data-preprocessing)
- [Similarity Calculation](#similarity-calculation)
- [Custom Scoring](#custom-scoring)
- [Dependencies](#dependencies)

---

## Installation

1. **Clone the Repository:**  
   Clone this repository or download the code files to your local environment.

2. **Install Required Libraries:**  
   Run the following commands to install the necessary Python libraries:

   ```bash
   pip install pandas numpy scikit-learn nltk fuzzywuzzy Levenshtein
   ```

3. **NLTK Downloads:**  
   The script also requires NLTK stopwords and tokenizers:

   ```python
   import nltk
   nltk.download('stopwords')
   nltk.download('omw-1.4')
   ```

---

## Usage

1. **Input Files:**  
   Ensure the following files are available in the same directory:
   - `Dataset.xlsx`: Seller dataset.
   - `Master File.xlsx`: Reference file containing master product details.

2. **Run the Code:**  
   Execute the script to preprocess data, calculate similarities, and map SKUs.

3. **Outputs:**  
   - `Dataset.csv`: Preprocessed seller dataset.
   - `Master.csv`: Preprocessed master file.
   - Predicted SKUs are calculated based on various similarity methods.

---

## Data Preprocessing

The code includes a function `preprocess_text` that:
- Converts text to lowercase.
- Removes Arabic diacritics and punctuation.
- Expands common abbreviations (e.g., mg → milligram).
- Normalizes spaces.

Another function `extract_dosage_form` is used to extract dosage and form (e.g., capsule, tablet) from product names.

---

## Similarity Calculation

The `calculate_similarity` function calculates the similarity between a seller's product and master products using:
- **Cosine Similarity:** Vector representation of product names.
- **Fuzzy Matching:** Token set ratio from `fuzzywuzzy`.
- **Levenshtein Distance:** Character-based string distance calculation.
- **Dosage/Form Similarity:** Checks if dosage and form match between seller and master records.

Weights for each similarity type are configurable in the function.

---

## Custom Scoring

The `custom_scorer` function evaluates model performance by comparing predicted SKUs with actual SKUs. It integrates seamlessly with `GridSearchCV` for hyperparameter tuning.

---

## Dependencies

- **Pandas:** Data manipulation and loading.
- **NumPy:** Numerical operations.
- **Scikit-learn:** Machine learning and similarity metrics.
- **NLTK:** Natural language processing (stopwords, tokenizers).
- **FuzzyWuzzy:** Fuzzy string matching.
- **Levenshtein:** String distance calculations.
