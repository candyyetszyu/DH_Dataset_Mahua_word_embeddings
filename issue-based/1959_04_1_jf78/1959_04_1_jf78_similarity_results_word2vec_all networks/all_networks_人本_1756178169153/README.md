# Network Visualizations Export

## Export Information
- **Target Word**: 人本
- **Models Included**: word2vec
- **Methods Included**: cosine, euclidean, manhattan, jaccard, pearson, spearman
- **Total Networks**: 6
- **Export Date**: 2025-08-26 11:16:07
- **Minimum Similarity**: 0.3

## Directory Structure
Each model has its own directory, with subdirectories for each method:
```
人本_networks/
├── model1/
│   ├── method1/
│   │   ├── network_model1_method1_人本.csv
│   │   ├── network_model1_method1_人本.json  
│   │   └── network_model1_method1_人本.html
│   └── method2/
└── model2/
```

## Files Included
1. **word2vec/cosine/network_word2vec_cosine_人本.json**
2. **word2vec/cosine/network_word2vec_cosine_人本.csv**
3. **word2vec/cosine/network_word2vec_cosine_人本.html**
4. **word2vec/euclidean/network_word2vec_euclidean_人本.json**
5. **word2vec/euclidean/network_word2vec_euclidean_人本.csv**
6. **word2vec/euclidean/network_word2vec_euclidean_人本.html**
7. **word2vec/manhattan/network_word2vec_manhattan_人本.json**
8. **word2vec/manhattan/network_word2vec_manhattan_人本.csv**
9. **word2vec/manhattan/network_word2vec_manhattan_人本.html**
10. **word2vec/jaccard/network_word2vec_jaccard_人本.json**
11. **word2vec/jaccard/network_word2vec_jaccard_人本.csv**
12. **word2vec/jaccard/network_word2vec_jaccard_人本.html**
13. **word2vec/pearson/network_word2vec_pearson_人本.json**
14. **word2vec/pearson/network_word2vec_pearson_人本.csv**
15. **word2vec/pearson/network_word2vec_pearson_人本.html**
16. **word2vec/spearman/network_word2vec_spearman_人本.json**
17. **word2vec/spearman/network_word2vec_spearman_人本.csv**
18. **word2vec/spearman/network_word2vec_spearman_人本.html**

## File Types
- **CSV**: Similarity data with scores above minimum threshold
- **JSON**: Complete network data including plot structure and metadata
- **HTML**: Self-contained interactive visualizations (no internet required)

## Network Methods
- **Cosine**: Measures angle between word vectors
- **Euclidean**: Measures straight-line distance between word vectors  
- **Manhattan**: Measures sum of absolute differences
