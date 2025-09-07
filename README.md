# Ehugbo ASR: Benchmarking Speech Recognition for a Low-Resource Igbo Dialect

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

This repository contains the code and resources for the paper *"When Endangered Voices Speak: Building the First Ehugbo Dialect Audio Dataset Through Grassroots Collaboration"*, presented at the WiML 2025 Workshop @ NeurIPS.

## Abstract

The rapid advancement of speech technologies has created a growing linguistic divide, leaving behind communities whose languages are underrepresented. This is especially true for endangered languages like **Ehugbo**, a dialect of Igbo spoken by approximately 150,000 people in Afikpo, Nigeria. With no prior publicly available audio data, Ehugbo is at high risk of digital extinction. This project details the collaborative, grassroots construction of the first open-source Ehugbo audio dataset—a 42.99-minute corpus of biblical recitations. We benchmark several pre-trained ASR models on this new dataset, establishing baseline performance and highlighting the unique challenges of dialectal, low-resource ASR.

## The Ehugbo ASR Dataset

Our work introduces the first publicly available audio dataset for the Ehugbo dialect.

*   **Language:** Ehugbo (a dialect of Igbo)
*   **Total Duration:** 42.99 minutes
*   **Content Source:** The Ehugbo New Testament (2020 Publication)
*   **Data Collection:** The project was built from the ground up in collaboration with the local community, involving six native speakers for recording and three validators for quality assurance.
*   **Availability:** The dataset is still being curated and to be released publicly soon, however, to reproduce this experiment, feel free to reach out.

## Benchmark Results

We evaluated several existing Igbo ASR models on our dataset to establish a performance baseline. The `CLEAR-Global/w2v-bert-2.0-igbo_naijavoices_250h` model, fine-tuned on a large corpus of diverse Nigerian voices, achieved the best results.

| Model                                            | WER (↓) | CER (↓) | WER (no diacritics) | CER (no diacritics) |
| ------------------------------------------------ | :-----: | :-----: | :-----------------: | :-----------------: |
| **CLEAR-Global/w2v-bert-2.0-igbo\_naijavoices\_250h** | **0.753** | **0.264** |      **0.701**      |      **0.218**      |
| AstralZander/xlsr-finetune-Igbo                    |  0.843  |  0.322  |        0.806        |        0.273        |
| oyemade/w2v-bert-2.0-igbo-CV17.0                   |  0.863  |  0.336  |        0.847        |        0.300        |
| AstralZander/igbo\_ASR                             |  0.866  |  0.320  |        0.852        |        0.281        |

*WER = Word Error Rate, CER = Character Error Rate. Lower is better.*

The results show a significant gap in performance, underscoring the need for dialect-specific training data and models.

## How to Reproduce the Results

### Prerequisites

*   Python 3.8+
*   PyTorch
*   Hugging Face Transformers
*   A local directory containing the Ehugbo audio files (`.wav` format) and a metadata CSV file.

### Installation

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/your-username/your-repo-name.git
    cd your-repo-name
    ```

2.  **Install the required packages:**
    Create a `requirements.txt` file with the content below and run `pip install -r requirements.txt`.
    ```
    transformers
    torch
    pandas
    soundfile
    jiwer<3.0
    rapidfuzz
    unicodedata2
    accelerate
    ```

### Usage

The notebook `Ehugbo_ASR_Evals.ipynb` contains the code used for the evaluation. To run it, you will need to:

1.  **Prepare your data:**
    *   Place all `.wav` audio files in a single directory.
    *   Create a metadata CSV file with at least two columns: one for the audio file names and one for the ground-truth transcriptions.

2.  **Update paths in the notebook:**
    *   Modify the `AUDIO_DIR` and CSV path variables in the notebook to point to your local data directories.

3.  **Run the cells:**
    *   Execute the notebook cells sequentially to load the models, run inference, and calculate the evaluation metrics.

## Citation

If you use this dataset or code in your research, please cite our paper - coming soon.
  url={https://github.com/your-username/your-repo-name}
}
