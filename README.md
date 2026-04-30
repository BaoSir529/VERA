<h1 align="center">
Multimodal Aspect-Based Sentiment Analysis via Evidence-Guided Region Calibration
</h1>

<p align="center">
  <a href="#-updates">✨ Updates</a> •
  <a href="#-abstract">💡 Abstract</a> •
  <a href="#-datasets">📦 Datasets</a> •
  <a href="#-results">📜 Results</a> •
  <a href="#-code">🔗 Code</a> •
  <a href="#-license">🔑 License</a> •
  <a href="#-acknowledgements">💗 Acknowledgements</a>
</p>

Code and dataset for the paper:

**Multimodal Aspect-Based Sentiment Analysis via Evidence-Guided Region Calibration**

## ✨ Updates

- 2026/03/10 Release dataset and core model code.
- 2026/03/10 Update README according to the latest version of the paper.
- 2025/07/27 Anonymize Git repository.
- 2025/04/13 Upload dataset.
- 2025/04/11 Create repository.

## 💡 Abstract

Multimodal Aspect-Based Sentiment Analysis (MABSA) aims to identify aspect-level sentiment from image-text social media posts. Although visual information can provide useful context, it is not uniformly beneficial for aspect-level prediction. Some visual regions provide content support, some offer context-relevant cues for sentiment reasoning, while others are weakly related or even misleading.

To address this issue, we propose **VEGA**, an evidence-guided region calibration framework for MABSA. VEGA first uses a multimodal large language model to construct two types of visual evidence from each image-text pair: **content-aware visual evidence** and **context-aware sentiment evidence**. The former describes observable visual content, while the latter identifies post-conditioned visual cues related to entities, events, or aspect-like targets without directly predicting sentiment labels. These evidence streams are then used to guide region-level visual calibration through a dual-support cross-attention mechanism. The calibrated visual features are finally integrated with the original text in a unified encoder-decoder architecture for both **MASC** and **JMASA**.

Experiments on Twitter2015 and Twitter2017 show that VEGA outperforms strong task-specific MABSA baselines. Further analyses validate the effectiveness of visual evidence construction and evidence-guided region calibration.

## 📦 Datasets

We evaluate VEGA on two widely used MABSA benchmarks:

- **Twitter2015**
- **Twitter2017**

Following prior work, we report results on two subtasks:

- **MASC**: Multimodal Aspect Sentiment Classification
- **JMASA**: Joint Multimodal Aspect-Sentiment Analysis

We use the standard train/dev/test splits of the two datasets.

### Data Statistics

| Split | Twitter2015 POS | Twitter2015 NEU | Twitter2015 NEG | Twitter2017 POS | Twitter2017 NEU | Twitter2017 NEG |
| :---: | :-------------: | :-------------: | :-------------: | :-------------: | :-------------: | :-------------: |
| Train | 928 | 1883 | 368 | 1508 | 1638 | 416 |
| Dev   | 303 | 670  | 149 | 515  | 517  | 144 |
| Test  | 317 | 607  | 113 | 493  | 573  | 168 |
| All   | 1548 | 3160 | 630 | 2516 | 2728 | 728 |

## 📜 Results

For **JMASA**, we report Precision, Recall, and F1.  
For **MASC**, we report Accuracy and Macro-F1.

### Main Results on JMASA

| Models | Twitter2015 P | Twitter2015 R | Twitter2015 F1 | Twitter2017 P | Twitter2017 R | Twitter2017 F1 |
| :----- | :-----------: | :-----------: | :------------: | :-----------: | :-----------: | :------------: |
| SPAN | 53.7 | 53.9 | 53.8 | 59.6 | 61.7 | 60.6 |
| D-GCN | 58.3 | 58.8 | 59.4 | 64.2 | 64.1 | 64.1 |
| BART | 62.9 | 65.0 | 63.9 | 65.2 | 65.6 | 65.4 |
| JML | 65.0 | 63.2 | 64.1 | 66.5 | 65.5 | 66.0 |
| VLP | 65.1 | 68.3 | 66.6 | 66.9 | 69.2 | 68.0 |
| CMMT | 64.6 | 68.7 | 66.5 | 67.6 | 69.4 | 68.5 |
| AoM | 67.9 | 69.3 | 68.6 | 68.4 | 71.0 | 69.7 |
| MOCOLNet | 66.3 | 67.9 | 67.1 | 67.3 | 68.7 | 68.0 |
| Atlantis | 65.6 | 69.2 | 67.3 | 68.6 | 70.3 | 69.4 |
| TMFN | 68.4 | 69.6 | 69.0 | 70.6 | 71.2 | 70.9 |
| TCMT | 69.3 | 70.4 | 69.8 | 70.2 | 71.5 | 70.8 |
| CORSA | 69.0 | 70.8 | 69.9 | 70.1 | 71.0 | 70.6 |
| DEQA | 71.4 | 73.9 | 72.7 | 71.4 | 72.4 | 71.9 |
| DaNet | 70.8 | 71.5 | 71.2 | 71.3 | 72.9 | 72.1 |
| DPHA | 69.9 | 71.8 | 70.8 | 70.3 | 71.7 | 71.0 |
| EaNet | 70.6 | 71.7 | 71.1 | 71.5 | 72.6 | 72.0 |
| **VEGA** | **75.2** | **74.5** | **74.8** | **73.1** | **74.8** | **73.9** |

### Main Results on MASC

| Models | Twitter2015 Acc. | Twitter2015 F1 | Twitter2017 Acc. | Twitter2017 F1 |
| :----- | :--------------: | :------------: | :--------------: | :------------: |
| JML | 78.7 | - | 72.7 | - |
| CMMT | 77.9 | - | 73.8 | - |
| VLP | 78.6 | 73.8 | 73.8 | 71.8 |
| AoM | 80.2 | 75.9 | 76.4 | 75.0 |
| Atlantis | 79.3 | - | 74.2 | - |
| Image2Text | 79.5 | 75.1 | 74.5 | 73.1 |
| CORSA | 81.1 | 77.1 | 76.6 | 74.5 |
| DEQA | 82.1 | 77.6 | 75.8 | 75.1 |
| DaNet | 81.3 | 78.5 | 79.0 | 76.4 |
| DPHA | 81.5 | 76.9 | 79.2 | 76.2 |
| EaNet | 81.6 | 78.4 | 78.1 | 75.5 |
| **VEGA** | **82.3** | **81.2** | **80.1** | **77.8** |

### Reference Comparison with MLLMs

The following results are provided as reference comparisons under a fixed zero-shot prompting protocol. They are not used as the primary evidence for VEGA's effectiveness.

| Models | Twitter2015 MASC | Twitter2015 JMASA | Twitter2017 MASC | Twitter2017 JMASA |
| :----- | :--------------: | :---------------: | :--------------: | :---------------: |
| Llama-3.2-Vision | 36.2 | 13.4 | 43.5 | 22.4 |
| Gemini-2.5-Pro | 63.8 | 26.0 | 67.4 | 23.3 |
| GPT-4o | 59.1 | 35.9 | 61.1 | 36.0 |
| **VEGA** | **81.2** | **74.8** | **77.8** | **73.9** |

## 🔗 Code

- **Status**: Released for review.

During the review stage, we release the dataset and core implementation of VEGA, including:

- data preprocessing scripts;
- visual evidence construction interface;
- evidence-guided region calibration module;
- training and evaluation scripts for MASC and JMASA.

Some auxiliary scripts may be further cleaned and updated after publication.

## 🔑 License

Distributed under the MIT License. See [MIT License](https://opensource.org/license/MIT) for more information.

## 💗 Acknowledgements

Our implementation is built upon prior MABSA codebases, especially [MABSA-VLP](https://github.com/NUSTM/VLP-MABSA). We sincerely thank the authors for their contributions.
