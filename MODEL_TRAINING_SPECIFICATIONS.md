# Word Embedding Models Training Specifications

This document provides detailed information about the training parameters and model configurations for the word embedding models available in this tool.

---

## Table of Contents

1. [Word2Vec Model](#word2vec-model)
2. [FastText Model](#fasttext-model)
3. [BERT Model](#bert-model)
4. [Comparison Table](#comparison-table)
5. [Configuration Guide](#configuration-guide)

---

## Word2Vec Model

Word2Vec is a shallow neural network model for learning word embeddings. This implementation uses Gensim's Word2Vec.

### Training Parameters

| Parameter | Default Value | Configurable Range | Description |
|-----------|---------------|-------------------|-------------|
| `vector_size` | 100 | 50-300 | Dimensionality of the word vectors |
| `window` | 5 | 3-10 | Context window size (words before and after target) |
| `min_count` | 2 | 1-10 | Minimum frequency threshold for vocabulary inclusion |
| `workers` | 4 (auto-optimized) | 1-8 | Number of worker threads for parallel training |
| `epochs` | 10 | 5-50 | Number of training iterations over the corpus |
| `sg` | 0 (CBOW) | Not exposed | Training algorithm: 0=CBOW, 1=Skip-gram |
| `seed` | 42 | Not exposed | Random seed for reproducibility |

### Training Algorithm: CBOW (Continuous Bag of Words)

**Important**: This implementation uses **CBOW exclusively** (`sg=0`). Skip-gram is not currently exposed as an option.

- **CBOW**: Predicts the target word from surrounding context words. Generally faster to train and works better with smaller datasets.
- **Skip-gram**: Predicts surrounding context words from the target word. Often performs better with larger datasets and rare words.

### Learning Rate

- Uses Gensim's default learning rate schedule
- Initial learning rate: ~0.025
- Decreases gradually during training

### Negative Sampling

- Uses Gensim default: 5 negative samples
- Used to optimize training by only updating a small subset of weights per iteration

### GPU Acceleration

When GPU is available, the system automatically:
- Optimizes worker count (up to 8 workers on GPU systems)
- Monitors GPU memory usage
- Falls back to CPU if GPU is unavailable

---

## FastText Model

FastText extends Word2Vec by learning representations for subword units (character n-grams), making it effective for handling out-of-vocabulary words and morphologically rich languages like Chinese.

### Training Parameters

| Parameter | Default Value | Configurable Range | Description |
|-----------|---------------|-------------------|-------------|
| `vector_size` | 100 | 50-300 | Dimensionality of the word vectors |
| `window` | 5 | 3-10 | Context window size |
| `min_count` | 2 | 1-10 | Minimum frequency threshold |
| `workers` | 4 (auto-optimized) | 1-8 | Number of worker threads |
| `epochs` | 10 | 5-50 | Number of training iterations |
| `sg` | 0 (CBOW) | Not exposed | Training algorithm (CBOW only) |
| `seed` | 42 | Not exposed | Random seed for reproducibility |

### Subword Embeddings

FastText learns embeddings for:
- Complete words (like Word2Vec)
- Character n-grams (subword units)

This provides:
- **Better handling of rare words**: Unknown words can be approximated from their subword components
- **Morphological awareness**: Captures morphological patterns in Chinese characters
- **Robustness**: More tolerant of spelling variations and character-level errors

### GPU Acceleration

Same optimization strategy as Word2Vec:
- Automatic worker optimization on GPU systems
- GPU memory monitoring
- CPU fallback when needed

---

## BERT Model

This tool uses **pre-trained BERT models** for Traditional Chinese. **No fine-tuning is performed** - the models are used for inference only.

### Pre-trained Model Variants

The system attempts to load models in the following order of preference:

| Priority | Model Name | Description |
|----------|-----------|-------------|
| 1 | `ckiplab/bert-base-chinese` | CKIP Lab model specifically designed for Traditional Chinese |
| 2 | `hfl/chinese-bert-wwm-ext` | Chinese BERT with Whole Word Masking extension |
| 3 | `bert-base-chinese-cased` | Original BERT cased version for Chinese |
| 4 | `bert-base-chinese` | Original BERT base model (fallback) |

### Model Characteristics

| Model | Vocabulary Size | Special Features |
|-------|----------------|------------------|
| `ckiplab/bert-base-chinese` | ~21K tokens | Optimized for Traditional Chinese, trained on CKIP corpus |
| `hfl/chinese-bert-wwm-ext` | ~21K tokens | Whole Word Masking improves Chinese tokenization |
| `bert-base-chinese` | ~21K tokens | Standard BERT, general purpose |

### Mode of Operation

- **Inference Only**: No training or fine-tuning on user data
- **Contextual Embeddings**: Returns different embeddings for the same word in different contexts
- **Evaluation Mode**: `model.eval()` - disables dropout and other training-specific layers

### GPU Acceleration

BERT processing is fully GPU-accelerated with:
- Batch processing for efficient GPU utilization
- Automatic batch size adjustment based on available GPU memory
- Contextual window processing (2 sentences before/after for better context)

### Output Types

The BERT implementation returns:

1. **Sentence-level embeddings**: Mean-pooled token embeddings per sentence
2. **Word-level embeddings**:
   - `averaged_word_embeddings`: Mean across all occurrences of each word
   - `contextualized_word_embeddings`: Separate embedding for each context occurrence

---

## Comparison Table

| Feature | Word2Vec | FastText | BERT |
|---------|----------|----------|------|
| **Training Required** | Yes | Yes | No (pre-trained) |
| **Architecture** | Shallow NN (1 layer) | Shallow NN (1 layer) | Deep Transformer (12 layers) |
| **Vector Dimensions** | 50-300 | 50-300 | 768 (fixed) |
| **Subword Information** | No | Yes (character n-grams) | Yes (BPE tokenization) |
| **Contextual Embeddings** | No | No | Yes |
| **OOV Handling** | Returns error | Uses subword averages | Uses [UNK] token |
| **Training Speed** | Fast | Fast | N/A (inference only) |
| **Inference Speed** | Very Fast | Very Fast | Moderate (requires GPU) |
| **GPU Required** | No | No | Recommended |
| **CBOW/Skip-gram** | CBOW only | CBOW only | N/A |

---

## Configuration Guide

### For Best Results

#### Small Datasets (< 100KB text)
- **Word2Vec**: vector_size=100, epochs=20, window=5
- **FastText**: vector_size=100, epochs=20, window=5
- Rationale: More epochs compensate for limited data

#### Medium Datasets (100KB - 1MB)
- **Word2Vec**: vector_size=200, epochs=10, window=5
- **FastText**: vector_size=200, epochs=10, window=5
- Rationale: Larger vectors capture more semantic information

#### Large Datasets (> 1MB)
- **Word2Vec**: vector_size=300, epochs=5-10, window=7
- **FastText**: vector_size=300, epochs=5, window=7
- Rationale: Less epochs needed; larger window captures broader context

### For Specific Tasks

#### Semantic Similarity
- Use larger vector dimensions (200-300)
- Increase epochs for better convergence
- Consider BERT for nuanced contextual similarity

#### Word Analogy Tasks
- Larger vector dimensions help
- May need Skip-gram (not currently available)
- FastText often performs better for morphological patterns

#### Rare Word Handling
- Use **FastText** instead of Word2Vec
- Lower `min_count` threshold
- FastText's subword handling improves OOV predictions

#### Real-time Applications
- **Word2Vec/FastText**: Fastest inference, suitable for real-time
- **BERT**: Use GPU acceleration; consider caching common embeddings

---

## Technical Notes

### Gensim Word2Vec Default Parameters

```python
Word2Vec(
    sentences=sentences,
    vector_size=100,      # Word vector dimensionality
    window=5,             # Context window size
    min_count=2,          # Ignores words with total frequency lower than this
    workers=4,            # Training threads
    epochs=10,            # Number of iterations over corpus
    sg=0,                 # Training algorithm: 0=CBOW, 1=Skip-gram
    seed=42               # Random seed
)
```

### BERT Inference Configuration

```python
# Model configuration
model_name = 'ckiplab/bert-base-chinese'  # or other variants
max_length = 512                           # Token sequence limit
batch_size = 8 (GPU) / 4 (CPU)             # Processing batch size

# Processing options
context_window = 2                          # Sentences before/after for context
overlap = True                              # Overlapping contexts
```

---

## Performance Considerations

### Training Time

| Model | Small Corpus | Medium Corpus | Large Corpus |
|-------|--------------|---------------|--------------|
| Word2Vec | < 1 min | 1-5 min | 5-30 min |
| FastText | < 1 min | 1-5 min | 5-30 min |
| BERT | N/A (inference) | ~30 sec | ~2 min |

### Memory Requirements

| Model | Training (RAM) | Inference (RAM) | GPU Memory |
|-------|---------------|-----------------|------------|
| Word2Vec | 2-4 GB | < 1 GB | Not required |
| FastText | 2-4 GB | < 1 GB | Not required |
| BERT | N/A | 2-4 GB | 2-4 GB (recommended) |

---

## References

- [Gensim Word2Vec Documentation](https://radimrehurek.com/gensim/models/word2vec.html)
- [FastText Documentation](https://fasttext.cc/)
- [Transformers BERT Documentation](https://huggingface.co/transformers/model_doc/bert.html)
- [CKIP Lab Chinese BERT](https://github.com/ckiplab/ckiptagger)
- [Chinese BERT with Whole Word Masking](https://github.com/ymcui/Chinese-BERT-wwm)
