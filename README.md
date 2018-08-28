# Temporal Dependency Tree (TDT) Corpus

Temporal Dependency Tree Corpus is a collection of Chinese news reports and fairy tale stories annotated with time expressions, events, and temporal relations. Temporal relations in this corpus are represented as a dependency tree structure for each article. Detailed descriptions about Temporal Dependency Tree structures can be found in [our paper](https://arxiv.org/pdf/1808.07599.pdf).

## Corpus Statistics


|  | # Articles | # Sentences | # Time Expressions | # Events |
| :---: | :---: | :---: | :---: | :---: |
| **News Reports** | 115 | 2,841 | 1,167 | 4,807 |
| **Fairy Tale Stories** | 120 | 3,662 | 131 | 10,976 | 

All 120 fairy tale stories are from Chinese [Grimm Fairy Tales](https://www.grimmstories.com/zh/grimm-tonghua). 52 news reports are from [Chinese Treebank](https://catalog.ldc.upenn.edu/LDC2016T13), and 63 news reports are from Chinese [Wikinews](https://zh.wikinews.org). The train/dev/test data split in this repository is the split we used in [our paper](https://arxiv.org/pdf/1808.07599.pdf).


## Corpus Format

Chinese Treebank and Wikinews data are in ```news_data/```, Grimm data are in ```grimm_data/```. 

```*.txt``` files are texts of the articles. Each article is preceded with a line ```filename:<fileID>``` (e.g. ```filename:wikinews_ZH_15```), and followed by a blank line. Please note:

- In Wikinews data, there are blank lines inside the article text. The annotations are performed on these articles including the blank lines, so please don't remove the blank lines.
- Chinese Treebank `*.txt` files are not included here.

```*.tdt``` files are the **t**emporal **d**ependency **t**rees for the articles. Each line in a ```*.tdt``` file represents one child-parent pair. Each line has 9 fields, separated by tabs:

```
filename    cSnt    cStart  cEnd    cLabel  pSnt    pStart  pEnd    trLabel
```
- filename: the file ID
- cSnt: the sentence ID of the child
- cStart: the start word ID of the child
- cEnd: the end word ID of the child
- cLabel: the *time expression* or *event* label of the child
- pSnt: the sentence ID of the parent
- pStart: the start word ID of the parent
- pEnd: the end word ID of the parent
- trLabel: the temporal relation label between this child-parent pair

Please note: We use `-1 -1  -1` in the place of `pSnt   pStart  pEnd`, when the parent is the *ROOT* of the dependency tree.

### To use this corpus, please cite:

- Yuchen Zhang and Nianwen Xue. 2018. [Structured Interpretation of Temporal Relations](https://arxiv.org/pdf/1808.07599.pdf). In Proceedings of the 11th Language Resources and Evaluation Conference (LREC-2018), Miyazaki, Japan.

```
@inproceedings{zhang2018lrec,
    title={Structured Interpretation of Temporal Relations},
    author={Zhang, Yuchen and Xue, Nianwen},
    booktitle={Proceedings of the 11th Language Resources and Evaluation Conference (LREC-2018)},
    year={2018},
    address={Miyazaki, Japan}
}
```
