# DH Mahua Literary Journal Dataset

## Overview

This dataset contains JSON and CSV files derived from the Mahua (Malayan Chinese) literary journal corpus, organized primarily by year. Most data files are structured on a yearly basis, with the exception of `1959_04_1_jf78` and `1959_05_1_jf79`, which are issued-based.

## Project Aim

The project seeks to move beyond traditional frameworks—Malayan (national assimilation) and Chinese (diasporic or linguistic)—in analyzing the Mahua literary journal. Instead, it explores possible connections to Third World humanism, engaging with broader global debates such as French decolonization.

A key research challenge is how to tokenize and analyze the concept of "humanism," which appears in various Chinese translations (e.g., renwen zhuyi, rendao zhuyi, renben zhuyi). In the journal Chao Foon, writers may use alternative terms containing "ren" (human/person). To address this, the project leverages BERT and other word embedding models to better capture contextual meanings and semantic nuances.

## Dataset Structure

- **Yearly Folders:** Contain embedding visualizations and model data for each year.
- **Corpus Folder:** Contains the original text files for each issue.
- **Special Issues:** `1959_04_1_jf78` and `1959_05_1_jf79` are organized by issue rather than year.

### Folder Structure


### Yearly-based Structure Example (e.g., 1955, 1956, ...)

#### Example: 1955 Yearly Folder

```
1955/
	1955_embedding Visualization_2D_3D/
		2D/
		3D/
	1955_model_data_word2vec_fasttext_bert/
		1955_model_data_bert.json
		1955_model_data_fasttext.json
		1955_model_data_word2vec_fasttext_bert.json
		1955_model_data_word2vec.json
```

#### Example: 1956 Yearly Folder with Networking and Similarity Analysis

```
1956/
	1956_embedding Visualization_2D_3D/
		2D/
		3D/
	1956_model_data_word2vec_fasttext_bert/
		1956_model_data_bert.json
		1956_model_data_fasttext.json
		1956_model_data_word2vec_fasttext_bert.json
		1956_model_data_word2vec.json
	1956_similarity_results_all methods/
		1956_similarity_results_人_all_methods/
		1956_similarity_results_人文_all_methods/
		1956_similarity_results_人文主義_all_methods/
		1956_similarity_results_人本_all_methods/
		1956_similarity_results_人本主義_all_methods/
		1956_similarity_results_人道_all_methods/
		1956_similarity_results_人道主義_all_methods/
	1956_similarity_results_all networks/
		1956_similarity_results_人_all_networks/
		1956_similarity_results_人文_all_networks/
		1956_similarity_results_人文主義_all_networks/
		1956_similarity_results_人本_all_networks/
		1956_similarity_results_人本主義_all_networks/
		1956_similarity_results_人道_all_networks/
		1956_similarity_results_人道主義_all_networks/
```

*Note: Only the 1956 folder contains networking and similarity analysis results for 7 keywords: 人, 人文, 人文主義, 人本, 人本主義, 人道, 人道主義.*

### Issue-based Structure Example (e.g., 1959_04_1_jf78, 1959_05_1_jf79)

```
1959_04_1_jf78/
	1959_04_1_jf78_embedding Visualization_2D_3D/
		2D/
			pca/
				1959_04_1_jf78_2D_pca_multi_model_visualization.csv
				1959_04_1_jf78_2D_pca_multi_model_visualization.json
				1959_04_1_jf78_2D_pca_model_specified/
			tsne/
				1959_04_1_jf78_2D_tsne_multi_model_visualization.csv
				1959_04_1_jf78_2D_tsne_multi_model_visualization.json
				1959_04_1_jf78_2D_tsne_model_specified/
			umap/
				1959_04_1_jf78_2D_umap_multi_model_visualization.csv
				1959_04_1_jf78_2D_umap_multi_model_visualization.json
				1959_04_1_jf78_2D_umap_model_specified/
		3D/
			pca/
				1959_04_1_jf78_3D_pca_multi_model_visualization.csv
				1959_04_1_jf78_3D_pca_multi_model_visualization.json
				1959_04_1_jf78_3D_pca_model_specified/
			tsne/
				1959_04_1_jf78_3D_tsne_multi_model_visualization.csv
				1959_04_1_jf78_3D_tsne_multi_model_visualization.json
				1959_04_1_jf78_3D_tsne_model_specified/
			umap/
				1959_04_1_jf78_3D_umap_multi_model_visualization.csv
				1959_04_1_jf78_3D_umap_multi_model_visualization.json
				1959_04_1_jf78_3D_umap_model_specified/
	1959_04_1_jf78_model_data_word2vec_fasttext_bert/
		1959_04_1_jf78_model_data_bert.json
		1959_04_1_jf78_model_data_fasttext.json
		1959_04_1_jf78_model_data_word2vec_fasttext_bert.json
		1959_04_1_jf78_model_data_word2vec.json

1959_05_1_jf79/
	1959_05_1_jf79_embedding Visualization_2D_3D/
		2D/
			pca/
				1959_05_1_jf79_2D_pca_multi_model_visualization.csv
				1959_05_1_jf79_2D_pca_multi_model_visualization.json
				1959_05_1_jf79_2D_pca_model_specified/
			tsne/
				1959_05_1_jf79_2D_tsne_multi_model_visualization.csv
				1959_05_1_jf79_2D_tsne_multi_model_visualization.json
				1959_05_1_jf79_2D_tsne_model_specified/
			umap/
				...
		3D/
			pca/
				...
			tsne/
				...
			umap/
				...
	1959_05_1_jf79_model_data_word2vec_fasttext_bert/
		1959_05_1_jf79_model_data_bert.json
		1959_05_1_jf79_model_data_fasttext.json
		1959_05_1_jf79_model_data_word2vec_fasttext_bert.json
		1959_05_1_jf79_model_data_word2vec.json
```

The `corpus/` folder contains the original text files for each issue, named by year, month, and issue (e.g., `1955_11_1_jf1.txt`).

## Data Formats

- **JSON/CSV:** Processed data, embeddings, and model outputs.
- **TXT:** Original literary journal texts.

## Data Columns (for CSV/JSON)

- `year`: Year of publication
- `issue`: Issue number or identifier
- `title`: Title of the work
- `author`: Author name(s)
- `text`: Original text content
- `embedding`: Vector representation (if applicable)
- `model`: Embedding/model type (e.g., BERT, word2vec, fastText)

*Note: Not all columns may be present in every file. See individual files for details.*

## Example Usage

Researchers can use this dataset to:

- Analyze the semantic context of humanism-related terms in Mahua literature
- Visualize word embeddings and explore semantic shifts over time
- Apply NLP models (e.g., BERT) to study contextual meanings in literary texts

## License

This dataset is provided for academic and research purposes only. Please contact the author for permissions regarding redistribution or commercial use.

## Citation

If you use this dataset, please cite the project or contact the author for more information.
