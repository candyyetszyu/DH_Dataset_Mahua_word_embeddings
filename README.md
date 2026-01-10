# DH Mahua Literary Journal Dataset

## Overview

This dataset contains text files from the Mahua (Malayan Chinese) literary journal corpus, organized by year from 1955 to 1961. The corpus includes original text files and processed data for word embedding analysis, with some specialized folders for rationality-related content and yearly-based model data.

## Project Website

For interactive visualizations and additional resources, visit: **https://dh-dataset-mahua-word-embeddings-lm.vercel.app/**

## Project Aim

The project seeks to move beyond traditional frameworks—Malayan (national assimilation) and Chinese (diasporic or linguistic)—in analyzing the Mahua literary journal. Instead, it explores conceptual and thematic connections through digital humanities methods, engaging with broader literary and cultural debates.

A key research focus is the computational analysis of important concepts and keywords as they appear in various forms throughout the journal. The project leverages BERT and other word embedding models to better capture contextual meanings and semantic nuances across the literary corpus, enabling new insights into the evolution of ideas and themes over time.

## Dataset Documentation Guide

This dataset includes comprehensive documentation across four files to ensure reproducibility and facilitate reuse:

### Core Documentation Files

1. **[README.md](README.md)** (this file) - Overview, project context, and usage guidance
2. **[DATA_STRUCTURE.md](DATA_STRUCTURE.md)** - Detailed breakdown of directory hierarchy, file naming conventions, coverage statistics, and known data anomalies
3. **[PREPROCESSING_SPECIFICATIONS.md](PREPROCESSING_SPECIFICATIONS.md)** - Text preprocessing pipeline, tokenization methods, and statistical metadata for all model types
4. **[MODEL_TRAINING_SPECIFICATIONS.md](MODEL_TRAINING_SPECIFICATIONS.md)** - Training parameters, configurations, and technical specifications for Word2Vec, FastText, and BERT models

**For journal reviewers**: Start with this README for project context, then consult `DATA_STRUCTURE.md` for data coverage and quality information.

**For researchers planning to reuse this dataset**: Review all four documentation files to understand the data structure, preprocessing decisions, and model configurations before beginning your analysis.

## Funding Statement

This research, as part of the Early Career Scheme (ECS) project, “Visualizing Keywords in Malaysian-Chinese Literary History via Digital Humanities Methods," was funded by the Research Grants Council (RGC) of the Hong Kong Special Administrative Region, China, under Grant No. 27609122. 

## Submission Context

This dataset will be submitted for:

**Call for Papers: The Journal of Open Humanities Data (JOHD) Special Collection on Benchmarking in Digital Humanities**

Edited by Dr Jenny C.Y. Kwok and Dr. Liam Jianliang Gao, this collection explores the critical role of benchmarking in advancing humanities research, highlighting how the creation of shared evaluation data and systematic comparison of tools can drive progress.

## Dataset Structure

This dataset is organized into three main components. For complete structural details, file naming conventions, coverage statistics, and data quality notes, see **[DATA_STRUCTURE.md](DATA_STRUCTURE.md)**.

- **corpus/:** Contains the original text files organized by year (1955-1961), with each file representing a specific half-month issue (1955–1958) or single monthly issue (November 1958 onward) following the `YYYY-MM-first|second-issue-XXX.txt` convention.
- **rationality-related/:** Contains specialized folders for analysis of rationality-related content from specific issues (`1959_04_1_jf78` and `1959_05_1_jf79`), retained for historical traceability.
- **yearly-based-model-data/:** Contains processed model data organized by year for embedding and analysis purposes.

### Quick Reference: Coverage Summary

| Year | Issues | Character Count | Notes |
|------|--------|----------------|-------|
| 1955 | 4 | 93,773 | Nov–Dec only |
| 1956 | 24 | 647,956 | Complete coverage |
| 1957 | 24 | 669,896 | Complete coverage |
| 1958 | 21 | 617,044 | Complete coverage; monthly publication from November 1958 onward |
| 1959 | 12 | 431,252 | Single monthly issues |
| 1960 | 12 | 386,075 | Single monthly issues |
| 1961 | 1 | 32,315 | Jan only |

*Full details available in [DATA_STRUCTURE.md](DATA_STRUCTURE.md)*

## Data Processing and Models

This dataset provides three types of word embedding models trained on the corpus text. For comprehensive technical specifications, see **[MODEL_TRAINING_SPECIFICATIONS.md](MODEL_TRAINING_SPECIFICATIONS.md)** and **[PREPROCESSING_SPECIFICATIONS.md](PREPROCESSING_SPECIFICATIONS.md)**.

### Available Models

1. **Word2Vec** - Traditional word embeddings using CBOW algorithm
2. **FastText** - Subword-aware embeddings for better handling of Chinese morphology  
3. **BERT** - Contextualized embeddings using pre-trained Chinese models

### Preprocessing Pipeline

The text preprocessing pipeline applies consistent tokenization across all years:
- Chinese text segmentation using standard methods
- No stopword removal (preserving historical language patterns)
- Top 50 most frequent tokens tracked per model type
- Statistical compilation of sentence counts and vocabulary size

**Sample Statistics (1956)**:
- Sentences: 1,708
- Total Tokens: 36,845  
- Unique Vocabulary: 39,403 tokens

*Complete preprocessing specifications and yearly statistics available in [PREPROCESSING_SPECIFICATIONS.md](PREPROCESSING_SPECIFICATIONS.md)*

## Data Formats

- **TXT:** Original literary journal texts in the `corpus/` folder.
- **JSON:** Processed data files containing structured analysis results, word embeddings, and model outputs in `rationality-related/` and `yearly-based-model-data/` folders.

## How to Reuse This Dataset

### Quick Start Guide

1. **For Literary Analysis**: Use original text files in `corpus/` folder, organized chronologically from 1955-1961
2. **For NLP Research**: Access processed embeddings in `yearly-based-model-data/` with three model types (Word2Vec, FastText, BERT)
3. **For Historical Studies**: Focus on rationality-related analysis in the specialized `rationality-related/` folders

### Understanding the Data Structure

- **File Naming**: `YYYY-MM-first|second-issue-XXX.txt` (e.g., `1955-11-first-issue-001.txt`)
- **Temporal Coverage**: 1955-1961 with varying completeness (see coverage table above)
- **Language**: All texts in Traditional Chinese with UTF-8 encoding
- **Format**: Plain text (.txt) for corpus; JSON for processed model data

### Research Applications

#### Computational Literary Studies
- **Diachronic Analysis**: Track semantic shifts across the 6-year period using word embeddings
- **Thematic Evolution**: Compare BERT contextual embeddings across years for concept analysis  
- **Cross-temporal Comparison**: Use consistent preprocessing pipeline for reliable year-to-year comparisons

#### Digital Humanities Methods
- **Keyword Networks**: Utilize pre-computed embeddings for semantic similarity networks
- **Topic Modeling**: Apply to chronologically organized corpus for temporal topic analysis
- **Stylometric Analysis**: Compare linguistic features across different years and authors

#### Historical and Cultural Studies  
- **Post-colonial Literary History**: Examine evolving themes in Malayan Chinese literature
- **Cultural Identity**: Analyze conceptual frameworks beyond traditional national/diasporic categories
- **Comparative Literature**: Position within broader Southeast Asian Chinese literary traditions

### Technical Implementation Guide

#### Getting Started with Word Embeddings

```python
# Example: Loading preprocessed BERT embeddings for 1956
import json
with open('yearly-based-model-data/1956/bert_embeddings.json', 'r') as f:
    data_1956 = json.load(f)
    
# Access tokenized text and embeddings
tokens = data_1956['processed_tokens']
embeddings = data_1956['embeddings']
```

#### Model Selection Guidelines

| Research Goal | Recommended Model | Rationale |
|--------------|------------------|-----------|
| Semantic similarity analysis | **BERT** | Contextual embeddings capture nuanced meanings |
| Cross-temporal comparison | **Word2Vec** | Consistent static embeddings across years |
| Morphological analysis | **FastText** | Subword information for Chinese character analysis |
| Historical language patterns | **Word2Vec/FastText** | Faster processing for large-scale analysis |

*Complete model specifications and training parameters in [MODEL_TRAINING_SPECIFICATIONS.md](MODEL_TRAINING_SPECIFICATIONS.md)*

### Technical Considerations and Requirements

- **Encoding**: All text files use UTF-8 encoding; ensure your analysis tools support Chinese text processing
- **Dependencies**: Processed embeddings require Python libraries (transformers, gensim) - see model specifications
- **Hardware**: BERT processing benefits from GPU acceleration; Word2Vec/FastText run efficiently on CPU
- **Historical Context**: Consider publication era (1955-1961) when interpreting linguistic variations and terminology
- **Data Quality**: OCR-processed texts with manual verification; see [DATA_STRUCTURE.md](DATA_STRUCTURE.md) for quality notes

### Reproducibility and Validation

All preprocessing steps and model training parameters are documented to ensure reproducibility:
- **Tokenization**: Consistent Chinese segmentation methods across all years
- **Model Parameters**: Identical configurations for each model type (detailed in [MODEL_TRAINING_SPECIFICATIONS.md](MODEL_TRAINING_SPECIFICATIONS.md))
- **Statistical Validation**: Complete token counts and vocabulary statistics per year (in [PREPROCESSING_SPECIFICATIONS.md](PREPROCESSING_SPECIFICATIONS.md))

### Data Quality

**Strengths:**
- Consistent OCR processing with manual verification
- Systematic file organization and naming
- Comprehensive documentation and metadata
- Multiple embedding model types for comparison

*Complete coverage details and anomalies documented in [DATA_STRUCTURE.md](DATA_STRUCTURE.md)*

## Data Schema and File Structure

### Processed JSON Files Schema
The `yearly-based-model-data/` directory contains structured JSON files with the following fields:

- `year`: Publication year (1955-1961)
- `processed_tokens`: List of segmented tokens from corpus text
- `token_frequency`: Dictionary of top 50 most frequent tokens with counts
- `sentence_count`: Number of sentences in the year's corpus
- `total_tokens`: Total token count after segmentation  
- `unique_vocabulary_count`: Number of unique tokens (complete vocabulary size)
- `embeddings`: Model-specific vector representations
- `model_type`: Embedding model identifier ("bert", "word2vec", "fasttext")

### Raw Text Files
- **Encoding**: UTF-8
- **Format**: Plain text, one file per issue
- **Content**: OCR-processed literary texts with manual verification
- **Language**: Traditional Chinese characters

*Complete data structure documentation in [DATA_STRUCTURE.md](DATA_STRUCTURE.md)*

## Citation and Usage

### How to Cite This Dataset

If you use this dataset in your research, please cite:

```
Wong, Nicholas Y. H., Candy Ye Tsz Yu, and Allie Xiang Haiyin.
"DH Mahua Literary Journal Dataset: Word Embeddings for Malayan Chinese Literature (1955-1961)."
[Dataset] v1.2.0. University of Hong Kong, January 8, 2026.
DOI: 10.5281/zenodo.18205166
Funded by Hong Kong Research Grants Council ECS Grant No. 27609122.
```

### License and Permissions

This dataset is provided for academic and research purposes. Commercial use or redistribution requires permission from the project author.

### Acknowledgments

**Funding**: Research Grants Council (RGC) of Hong Kong SAR, China - Early Career Scheme (ECS) Grant No. 27609122 for "Visualizing Keywords in Malaysian-Chinese Literary History via Digital Humanities Methods"

**Contributing to the Special Collection**: This dataset supports the Journal of Open Humanities Data (JOHD) Special Collection on "Benchmarking in Digital Humanities" edited by Dr. Jenny C.Y. Kwok and Dr. Liam Jianliang Gao.

### Project Author

**Nicholas Y. H. Wong**  
Assistant Professor, School of Chinese  
The University of Hong Kong  
Email: nyhwong@hku.hk  
Website: [nyhwong.com](https://nyhwong.com) | [ORCID: 0000-0003-3953-5179](https://orcid.org/0000-0003-3953-5179)

### Contributed by

**Ye Tsz Yu Candy**  
Bachelor of Arts  
Majors: Chinese Language and Literature, Computer Science  
The University of Hong Kong  
Email: u3607570@connect.hku.hk  
Role: Visualization generation and dataset creation

**Allie Xiang Haiyin**  
Bachelor of Arts  
Majors: Translation and Comparative Literature  
Minor: Art History  
The University of Hong Kong  
Role: Text vetting and OCR validation
