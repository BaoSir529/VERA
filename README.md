
<h1 align="center">
VERA: Visual Evidence Reliability-Aware model for Multimodal Aspect-Based Sentiment Analysis
</h1>

<p align="center">
  <a href="#-Updates">✨ Updates</a> •
  <a href="#-Abstract">💡 Abstract</a> •
  <a href="#-Dataset">📦 Datasets</a> •
  <a href="#-Results">📜 Results</a> •
  <a href="#-Codes">🔗 Codes</a> •
  <a href="#-License">🔑 License</a> •
  <a href="#-Acknowledgements">💗Acknowledgements</a>
</p>

**Code and dataset for paper**: VERA: Visual Evidence Reliability-Aware model for Multimodal Aspect-Based Sentiment Analysis

## ✨ Updates
- 2026/3/10 Revise the paper and update the git.
- 2026/1/26 Revise certain expressions in the paper.
- 2025/7/27 Anonymize Git repository.
- 2025/4/13 upload the dataset.
- 2025/4/11 create the git and add the README.

## 💡 Abstract

Multimodal Aspect-Based Sentiment Analysis (MABSA) aims to perform fine-grained sentiment inference from social media posts containing both text and images. In social media scenarios, images mainly reflect the overall topic of a post, but may provide limited or unreliable evidence for aspect-level sentiment. This challenge is further complicated by the fact that visual and textual modalities express sentiment in different ways, making multimodal features harder to exploit effectively at the aspect level. To address these combined challenges, we propose the Visual Evidence Reliability-Aware model (VERA), which improves multimodal sentiment reasoning through explicit visual evidence construction and reliability-aware visual regulation. Specifically, VERA first leverages multimodal large language models to convert visual inputs into explicit textual evidence, making visual cues more accessible for downstream sentiment inference. It then adaptively regulates the visual contribution according to the reliability of the generated evidence for the target aspect. In this way, VERA reduces interference from images that are only weakly associated with the target or provide unreliable sentiment cues. Experimental results on benchmark datasets show that our model outperforms strong baselines, while visualizations confirm its ability to establish reliable and interpretable semantic anchors.

## 📦 Dataset

We evaluate VERA on two widely used Multimodal Aspect-Based Sentiment Analysis (MABSA) benchmarks: **Twitter2015** and **Twitter2017**. Following prior work, we report results on two subtasks:

- **JMASA**: Joint Multimodal Aspect-based Sentiment Analysis
- **MASC**: Multimodal Aspect Sentiment Classification

We use the standard train/dev/test splits of the two datasets. The sentiment label distributions are shown below.

### 📚 Data Statistics

| Split | Twitter2017 POS | Twitter2017 NEU | Twitter2017 NEG | Twitter2015 POS | Twitter2015 NEU | Twitter2015 NEG |
| :---: | :-------------: | :-------------: | :-------------: | :-------------: | :-------------: | :-------------: |
| Train | 1508 | 1638 | 416 | 928 | 1883 | 368 |
| Dev   | 515  | 517  | 144 | 303 | 670  | 149 |
| Test  | 493  | 573  | 168 | 317 | 607  | 113 |
| All   | 2516 | 2728 | 728 | 1548 | 3160 | 630 |

## 📜 Results

We report results on both **JMASA** and **MASC**. For JMASA, we use **Precision (P)**, **Recall (R)**, and **F1** as evaluation metrics. For MASC, we report **Accuracy (Acc.)** and **Macro-F1 (F1)**.  
The best results are in **bold**, and the second-best results are <u>underlined</u>. Marker `*` indicates statistically significant improvement over **AoM** on F1 scores across 5 runs (`p < 0.05`).

### 1. Main Results on JMASA

| Models | Twitter2017 P | Twitter2017 R | Twitter2017 F1 | Twitter2015 P | Twitter2015 R | Twitter2015 F1 |
| :----- | :-----------: | :-----------: | :------------: | :-----------: | :-----------: | :------------: |
| **Text-only models** |||||||
| SPAN<sup>§</sup> (2019) | 59.6 | 61.7 | 60.6 | 53.7 | 53.9 | 53.8 |
| D-GCN<sup>§</sup> (2020) | 64.2 | 64.1 | 64.1 | 58.3 | 58.8 | 59.4 |
| BART<sup>§</sup> (2021) | 65.2 | 65.6 | 65.4 | 62.9 | 65.0 | 63.9 |
| **Multimodal models** |||||||
| JML<sup>§</sup> (2021) | 66.5 | 65.5 | 66.0 | 65.0 | 63.2 | 64.1 |
| VLP<sup>§</sup> (2022) | 66.9 | 69.2 | 68.0 | 65.1 | 68.3 | 66.6 |
| CMMT<sup>§</sup> (2022) | 67.6 | 69.4 | 68.5 | 64.6 | 68.7 | 66.5 |
| AoM<sup>§</sup> (2023) | 68.4 | 71.0 | 69.7 | 67.9 | 69.3 | 68.6 |
| MOCOLNet (2024) | 67.3 | 68.7 | 68.0 | 66.3 | 67.9 | 67.1 |
| Atlantis (2024) | 68.6 | 70.3 | 69.4 | 65.6 | 69.2 | 67.3 |
| TMFN (2024) | 70.6 | 71.2 | 70.9 | 68.4 | 69.6 | 69.0 |
| TCMT (2025) | 70.2 | 71.5 | 70.8 | 69.3 | 70.4 | 69.8 |
| CORSA (2025) | 70.1 | 71.0 | 70.6 | 69.0 | 70.8 | 69.9 |
| DEQA (2025) | 71.4 | 72.4 | 71.9 | <u>71.4</u> | 73.9 | <u>72.7</u> |
| DaNet (2025) | 71.3 | 72.9 | 72.1 | 70.8 | 71.5 | 71.2 |
| AETS (2025) | **72.6** | **73.7** | **73.1** | 69.7 | **74.7** | 72.1 |
| **VERA (Ours)** | <u>72.0</u> | <u>73.5</u> | <u>72.7*</u> | **75.2** | <u>74.5</u> | **74.8*** |

> <sup>§</sup> denotes results reported in prior work. Unmarked results are from public or original implementations.

### 2. Comparison with LLMs on JMASA

| LLMs | Twitter2017 P | Twitter2017 R | Twitter2017 F1 | Twitter2015 P | Twitter2015 R | Twitter2015 F1 |
| :--- | :-----------: | :-----------: | :------------: | :-----------: | :-----------: | :------------: |
| **LLMs with text-only input** |||||||
| LLaVA (34B)<sup>†</sup> | 9.6 | 15.9 | 11.9 | 7.0 | 15.2 | 9.6 |
| DeepSeek-V3 (70B)<sup>†</sup> | 27.9 | 33.1 | 30.3 | 26.7 | 41.5 | 32.5 |
| **LLMs with multimodal input** |||||||
| Llama-3.2-Vision<sup>†</sup> | 21.4 | 23.5 | 22.4 | 11.9 | 15.3 | 13.4 |
| Gemini-2.5-Pro<sup>‡</sup> | 30.6 | 18.8 | 23.3 | 28.3 | 24.1 | 26.0 |
| GPT-4o-mini<sup>‡</sup> | 34.8 | 37.3 | 36.0 | 31.2 | 42.4 | 35.9 |
| GPT-5<sup>‡</sup> | 29.9 | 42.2 | 35.0 | 25.0 | 45.8 | 32.3 |
| **VERA (Ours)** | **72.0** | **73.5** | **72.7** | **75.2** | **74.5** | **74.8** |

> <sup>†</sup> indicates locally deployed results.  
> <sup>‡</sup> indicates results from official APIs.

### 3. Main Results on MASC

| Models | Twitter2017 Acc. | Twitter2017 F1 | Twitter2015 Acc. | Twitter2015 F1 |
| :----- | :--------------: | :------------: | :--------------: | :------------: |
| JML (2021) | 72.7 | - | 78.7 | - |
| CMMT (2022) | 73.8 | - | 77.9 | - |
| VLP-MABSA (2022) | 73.8 | 71.8 | 78.6 | 73.8 |
| AoM (2023) | 76.4 | 75.0 | 80.2 | 75.9 |
| Atlantis (2024) | 74.2 | - | 79.3 | - |
| Image2Text (2024) | 74.5 | 73.1 | 79.5 | 75.1 |
| CORSA (2025) | 76.6 | 74.5 | 81.1 | 77.1 |
| DEQA (2025) | 75.8 | 75.1 | <u>82.1</u> | 77.6 |
| DaNet (2025) | **79.0** | <u>76.4</u> | 81.3 | 78.5 |
| AETS (2025) | 76.6 | 75.2 | 79.5 | <u>80.8</u> |
| **VERA (Ours)** | <u>78.1</u> | **76.8*** | **82.3** | **81.2*** |

### 4. Comparison with LLMs on MASC

| LLMs | Twitter2017 Acc. | Twitter2017 F1 | Twitter2015 Acc. | Twitter2015 F1 |
| :--- | :--------------: | :------------: | :--------------: | :------------: |
| **LLMs with text-only input** |||||
| LLaVA (34B)<sup>†</sup> | 18.7 | 15.8 | 13.9 | 12.6 |
| DeepSeek-V3 (70B)<sup>†</sup> | 62.7 | 53.8 | 67.3 | 53.1 |
| DeepSeek (32B)<sup>†</sup> | 62.4 | 61.3 | 71.6 | 62.4 |
| Gemma3 (27B)<sup>†</sup> | 65.1 | 65.1 | 69.4 | 64.3 |
| GPT-4o-mini<sup>‡</sup> | 71.6 | 64.4 | 61.9 | 60.6 |
| Gemini-2.0-Flash<sup>‡</sup> | 71.6 | 62.4 | 64.8 | 63.5 |
| Gemini-2.5-Pro<sup>‡</sup> | 72.1 | 63.8 | 65.2 | 61.7 |
| **LLMs with multimodal input** |||||
| Llama-3.2-Vision<sup>†</sup> | 50.0 | 43.5 | 38.7 | 36.2 |
| Gemma3 (27B)<sup>†</sup> | 63.8 | 64.2 | 59.9 | 59.4 |
| GPT-4o-mini<sup>‡</sup> | 61.1 | 61.1 | 59.5 | 59.1 |
| Gemini-2.0-Flash<sup>‡</sup> | 66.0 | 67.0 | 64.0 | 62.5 |
| Gemini-2.5-Pro<sup>‡</sup> | 66.9 | 67.4 | 66.6 | 63.8 |
| **VERA (Ours)** | **78.1** | **76.8** | **82.3** | **81.2** |

> <sup>†</sup> indicates locally deployed results.  
> <sup>‡</sup> indicates results from official APIs.

### Summary

VERA achieves consistently strong performance across both subtasks and datasets. On **JMASA**, it obtains the **best F1 on Twitter2015 (74.8)** and highly competitive results on **Twitter2017 (72.7)**. On **MASC**, VERA achieves the **best F1 on both Twitter2017 (76.8)** and **Twitter2015 (81.2)**, while also substantially outperforming general-purpose LLMs under both text-only and multimodal settings.

## 🔗 Codes

- **Status**: Under review.

During the paper review stage, we have released the dataset and the core model code. The remaining components are currently under inspection and will be updated as soon as the paper is published.

## 🔑 License

Distributed under the MIT License. See [MIT LICENSE](https://opensource.org/license/MIT) for more information.

## 💗 Acknowledgements

Our code depends on project [MABSA-VLP](https://github.com/NUSTM/VLP-MABSA), many thanks!
