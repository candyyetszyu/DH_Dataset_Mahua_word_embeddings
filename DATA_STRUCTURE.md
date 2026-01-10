# DH Mahua Dataset Structure and Coverage

## Directory Overview

- `corpus/`: Canonical text corpus organized by year. Issues from 1955–1958 appear twice per month (first/second circulation), while November 1958 onward the publisher switched to a single monthly issue; filenames retain the `first/second` slot for consistency.
- `rationality-related/`: Focused experiments for the `1959-04-first-issue-078` and `1959-05-first-issue-079` issues (embedding visualizations, similarity networks, etc.).
- `yearly-based-model-data/`: Aggregated embedding/model outputs grouped by publication year (1955–1961).

## Corpus File Naming Convention

```
YYYY-MM-first|second-issue-XXX.txt
```

- `YYYY`: Gregorian publication year.
- `MM`: Two-digit month.
- `first` / `second`: Indicates the first (roughly days 1–15) or second (roughly days 16–end) circulation of the monthly issue. Beginning in November 1958 the publisher adopted a single monthly issue, so only `first` files exist for those years.
- `XXX`: Zero-padded sequential identifier that matches the historical `jf` numbering used in the print archive.

Example: `1957-03-second-issue-035.txt` represents the second half of the March 1957 issue, historically labeled `jf35`.

## Coverage Summary (corpus/)

| Year | Issues | Months Covered | Second Issues Present | Total Characters |
| --- | --- | --- | --- | --- |
| 1955 | 4 | Nov–Dec | Both halves for Nov & Dec | 93,773 |
| 1956 | 24 | Jan–Dec | All months have both halves | 647,956 |
| 1957 | 24 | Jan–Dec | All months have both halves | 669,896 |
| 1958 | 21 | Jan–Dec | Complete coverage; monthly publication from November 1958 onward | 617,044 |
| 1959 | 12 | Jan–Dec | Publisher shifted to single monthly issue (no second release) | 431,252 |
| 1960 | 12 | Jan–Dec | Monthly single issue | 386,075 |
| 1961 | 1 | Jan | Monthly single issue | 32,315 |

Character counts are direct byte-length measurements of the UTF-8 encoded files and give a rough sense of textual volume.

## Corrections and Text Quality

- Source texts were OCRed and manually vetted by the project team (see README credits). Reviewers corrected obvious OCR artifacts such as broken characters, duplicated punctuation, or missing diacritics.
- No large-scale modernization, re-segmentation, or rephrasing was performed; historical orthography, punctuation, and diction are intentionally preserved.
- Encoding is UTF-8. When opening in spreadsheet tools, ensure UTF-8 decoding to avoid mojibake.

## Known Gaps and Anomalies

- **1958 Q4**: Second-half issues for October are missing in the source archive; monthly publication began in November 1958.
- **1959–1960**: Publisher officially moved from bi-monthly (two-half) issues to a single monthly issue, so only `first` files exist.
- **1961**: The monthly format continues, but only the January issue survives in the current collection.
- Any additional anomalies (damaged scans, partially illegible pages) are documented inline within research notebooks, but not embedded in the text files themselves.

## Related Processed Data

- `rationality-related/1959_04_1_jf78/` and `1959_05_1_jf79/` retain their historical directory names to mirror the specialized experiments conducted on those issues.
- `yearly-based-model-data/<year>/` aggregates embedding outputs (BERT, fastText, word2vec). File names remain unchanged to preserve provenance with earlier publications.

Consult the main `README.md` for project motivation, funding context, and usage guidance. This document focuses solely on structural and coverage metadata to assist with reproducibility and reuse.
