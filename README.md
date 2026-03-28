# Fine-tuning DeepSeek-OCR for Vietnamese Handwriting Recognition

## 1. Problem Statement
This project focuses on Vietnamese handwriting recognition (Handwriting OCR), one of the major challenges in Natural Language Processing and Computer Vision due to the diversity of handwriting styles, character angles, and Vietnamese diacritical marks. The objective is to fine-tune the DeepSeek-OCR model to improve the accuracy and efficiency of text extraction from handwritten images.

## 2. Dataset
The dataset used in this project is **UIT-HWDB**, a standard benchmark dataset for evaluating Vietnamese handwriting recognition in unconstrained conditions.  
**Dataset Link:** [UIT-HWDB](https://github.com/nghiangh/UIT-HWDB-dataset)

### Dataset Composition
The dataset is categorized by granularity with the following distribution:
- **Word level:** 30% of samples
- **Line level:** 30% of samples
- **Paragraph level:** 40% of samples

### Data Split
The experimental setup uses the following data split:
| Split | Training (1000 samples) | Training (2000 samples) |
| :--- | :--- | :--- |
| Train | 900 (90%) | 1800 (90%) |
| Validation | 100 (10%) | 200 (10%) |
| Test | 100 | 100 |

## 3. Fine-tuning Model DeepSeek-OCR
The training process is based on the DeepSeek-OCR foundation model using QLoRA (Quantized Low-Rank Adaptation) technique to optimize hardware resources. The [Unsloth](https://unsloth.ai/docs/models/tutorials/deepseek-ocr-how-to-run-and-fine-tune) library is used to accelerate training, saving memory and increasing training speed by 2x.

### Training Configuration
- **LoRA parameters:**
  - Rank (r): 16
  - Alpha: 16
  - Dropout: 0
  - Target modules: q_proj, k_proj, v_proj, o_proj, gate_proj, up_proj, down_proj

- **Training hyperparameters:**
  - Batch size: 1 (with gradient accumulation of 16)
  - Learning rate: 2e-4
  - Epochs: 3
  - Optimizer: AdamW 8bit
  - Image size: 640x640, Base size: 768x768

## 4. Evaluation Metrics
The model performance is assessed using two primary metrics:  
1. Character Error Rate (CER): Measures the percentage of character-level errors in the transcription.  
2. Word Error Rate (WER): Measures the percentage of word-level errors in the transcription.  

### Performance Improvements
| Model | CER | Δ CER | WER | Δ WER |
| :--- | :--- | :--- | :--- | :--- |
| Base Model | 1.4032 | - | 1.1309 | - |
| Finetune (1000 samples) | 0.2943 | ↓ 79.03% | 0.5069 | ↓ 55.17% |
| Finetune (2000 samples) | 0.2844 | ↓ 79.73% | 0.4750 | ↓ 58.00% |

The fine-tuning process demonstrates significant improvements in both CER and WER metrics. With 1000 training samples, **CER improved by 79.03%** and **WER by 55.17%**. With 2000 training samples, the improvements **reached 79.73% in CER** and **58.00% in WER**, indicating increasingly better accuracy in Vietnamese handwriting recognition.

