# Preprocessing Specifications

This document provides detailed information about the text preprocessing pipeline and model-specific statistics for the Mahua literary journal dataset.

## Overview

The preprocessing pipeline applies consistent tokenization and analysis across all years of the corpus, with separate processing for three different model types: BERT, Word2Vec, and FastText. Each model type receives the same preprocessed text but maintains separate statistical tracking.

## Preprocessing Pipeline

### Text Processing Steps
1. **Tokenization**: Chinese text segmentation using standard tokenization methods
2. **Frequency Analysis**: Extraction of top 50 most frequent tokens per model type
3. **Statistical Compilation**: Collection of sentence counts, token counts, and vocabulary statistics
4. **No Stopword Removal**: The preprocessing pipeline does not apply stopword filtering

## Data Structure Explanation

- **Total Vocabulary**: The complete number of unique tokens in each year's corpus varies significantly (ranging from ~11,000 to ~85,000+ tokens)
- **Vocabulary**: The "50" refers to the top 50 most frequent tokens that were tracked for frequency analysis

## Model-Specific Statistics

### 1955 Data
- **BERT Model**
  - Sentences: 364
  - Total Tokens: 8,133
  - Total Unique Vocabulary: 11,270
  - Most Frequent Tokens Tracked: 50

- **Word2Vec Model**
  - Sentences: 364
  - Total Tokens: 8,133
  - Total Unique Vocabulary: 11,270
  - Most Frequent Tokens Tracked: 50

- **FastText Model**
  - Sentences: 364
  - Total Tokens: 8,133
  - Total Unique Vocabulary: 11,270
  - Most Frequent Tokens Tracked: 50

### 1956 Data
- **BERT Model**
  - Sentences: 1,708
  - Total Tokens: 36,845
  - Total Unique Vocabulary: 39,403
  - Most Frequent Tokens Tracked: 50

- **Word2Vec Model**
  - Sentences: 1,708
  - Total Tokens: 36,845
  - Total Unique Vocabulary: 39,403
  - Most Frequent Tokens Tracked: 50

- **FastText Model**
  - Sentences: 1,708
  - Total Tokens: 36,845
  - Total Unique Vocabulary: 39,403
  - Most Frequent Tokens Tracked: 50

### 1957 Data
- **BERT Model**
  - Sentences: 1,724
  - Total Tokens: 37,227
  - Total Unique Vocabulary: 39,861
  - Most Frequent Tokens Tracked: 50

- **Word2Vec Model**
  - Sentences: 1,724
  - Total Tokens: 37,227
  - Total Unique Vocabulary: 39,861
  - Most Frequent Tokens Tracked: 50

- **FastText Model**
  - Sentences: 1,724
  - Total Tokens: 37,227
  - Total Unique Vocabulary: 39,861
  - Most Frequent Tokens Tracked: 50

### 1958 Data
- **BERT Model**
  - Sentences: 1,468
  - Total Tokens: 31,651
  - Total Unique Vocabulary: 38,124
  - Most Frequent Tokens Tracked: 50

- **Word2Vec Model**
  - Sentences: 1,468
  - Total Tokens: 31,651
  - Total Unique Vocabulary: 38,124
  - Most Frequent Tokens Tracked: 50

- **FastText Model**
  - Sentences: 1,468
  - Total Tokens: 31,651
  - Total Unique Vocabulary: 38,124
  - Most Frequent Tokens Tracked: 50

### 1959 Data
- **BERT Model**
  - Sentences: 892
  - Total Tokens: 19,302
  - Total Unique Vocabulary: 25,378
  - Most Frequent Tokens Tracked: 50

- **Word2Vec Model**
  - Sentences: 892
  - Total Tokens: 19,302
  - Total Unique Vocabulary: 25,378
  - Most Frequent Tokens Tracked: 50

- **FastText Model**
  - Sentences: 892
  - Total Tokens: 19,302
  - Total Unique Vocabulary: 25,378
  - Most Frequent Tokens Tracked: 50

### 1960 Data
- **BERT Model**
  - Sentences: 8,849
  - Total Tokens: 171,012
  - Total Unique Vocabulary: 85,063
  - Most Frequent Tokens Tracked: 50

- **Word2Vec Model**
  - Sentences: 8,849
  - Total Tokens: 171,012
  - Total Unique Vocabulary: 85,063
  - Most Frequent Tokens Tracked: 50

- **FastText Model**
  - Sentences: 8,849
  - Total Tokens: 171,012
  - Total Unique Vocabulary: 85,063
  - Most Frequent Tokens Tracked: 50

### 1961 Data
- **BERT Model**
  - Sentences: 667
  - Total Tokens: 13,851
  - Total Unique Vocabulary: 18,507
  - Most Frequent Tokens Tracked: 50

- **Word2Vec Model**
  - Sentences: 667
  - Total Tokens: 13,851
  - Total Unique Vocabulary: 18,507
  - Most Frequent Tokens Tracked: 50

- **FastText Model**
  - Sentences: 667
  - Total Tokens: 13,851
  - Total Unique Vocabulary: 18,507
  - Most Frequent Tokens Tracked: 50

## Technical Notes

- All statistics are derived from the processed JSON files in the `yearly-based-model-data/` directory
- The "Most Frequent Tokens Tracked" refers to the top 50 tokens stored in the `token_frequency` field for analysis purposes
- The "Total Unique Vocabulary" represents all distinct tokens found in the `processed_tokens` list
- Model training parameters and embeddings are included in the respective JSON files
- The preprocessing pipeline maintains consistency across all years and model types