# MURI: Multilingual Instruction Tuning Dataset for 200 Languages via Reverse Instructions

We introduce the MURI-IT dataset and MURI-101 model for multilingual instruction tuning. By applying multilingual reverse instructions (MURI), we generate high-quality instruction-tuning data from raw corpora for **200 languages**. This method ensures cultural and linguistic nuances are preserved, avoiding translation artifacts commonly found in prior approaches like Okapi and Aya, which relied heavily on direct translations.

[Paper](PLACEHOLDER)  
[🤗 The MURI-IT Dataset](https://huggingface.co/datasets/akoksal/muri-it/)  
[🤗 The MURI-101 Model](https://huggingface.co/akoksal/muri-101)  


![MURI](https://live.staticflickr.com/65535/54004934709_9ccccbf85a_o.png)

Key Steps:
1. Extract high-quality human-written raw text from CulturaX and Wikipedia.
2. Translate the raw text into English.
3. Apply reverse instructions to generate instructions for the raw text via LLMs.
4. Translate the generated instructions back into the source language.

This ensures the model output is culturally relevant and free from translation artifacts.

## Dataset
Our dataset, **MURI-IT**, is publicly available on HuggingFace 🤗. It contains over 2.2 million instruction-output pairs across 200 languages, including some code examples. Unlike previous research, which relied on translated instructions, our method keeps the output from the native source language, ensuring linguistic authenticity.

[🤗 MURI-IT](https://huggingface.co/datasets/akoksal/muri-it/)

If you would like to use the dataset structured based on language-level subsets, check out this:

[🤗 MURI-IT Language Split](https://huggingface.co/datasets/akoksal/muri-it-language-split)

| **Source**                             | **# Languages** | **# Examples**   |
|--------------------------------------- |:---------------:|-----------------:|
| **Multilingual Reverse Instructions**  |      194        |       1,718,449  |
| - Wikipedia                            |      187        |       1,031,726  |
| - CulturaX                             |      123        |         686,723  |
| **WikiHow**                            |       18        |          54,578  |
| **NLP Tasks**                          |       74        |        455,472   |
| - SupNatInst-v2                        |       55        |        161,986   |
| - xP3                                  |       44        |        184,000   |
| - OpenAssistant                        |       10        |          9,486   |
| - FLAN v2.0                            |        1        |        100,000   |
|--------------------------------------- |-----------------|----------------- |
| **Total**                              |   **200**       |   **2,228,499**  |


For more details on dataset distribution, please refer to [the paper](soon) and [the Hugging Face datasets](https://huggingface.co/datasets/akoksal/muri-it/) link.

## Model
We fine-tuned the mT5-XXL model using a subset of the MURI-IT dataset and released the MURI-101 model on HuggingFace, supporting 101 languages. Thanks to [Google's TRC program](https://sites.research.google/trc/about/) for supporting the training of this model.

[🤗 MURI-101](https://huggingface.co/akoksal/muri-101)

## Results
We compare **MURI-101** against state-of-the-art models for multilingual instruction following. MURI-101 outperforms most multilingual models, except for Aya, across both NLU and NLG datasets.

|                   | Okapi | mT0 | mT0x | Aya-101 | MURI-101 |
|-------------------|----------------|--------------|---------------|------------------|---------------------------|
| arb      | 27.7           | 31.5         | 31.6          | 38.2             | 36.5                      |
| ben      | 26.8           | 31.6         | 30.2          | 35.8             | 33.0                      |
| cat      | 30.5           | 32.8         | 32.6          | 39.6             | 38.8                      |
| dan      | 31.8           | 33.0         | 32.0          | 39.7             | 38.4                      |
| deu      | 31.7           | 32.7         | 32.5          | 39.7             | 38.9                      |
...
| vie      | 27.5           | 30.9         | 31.1          | 34.8             | 36.8                      |
| zho      | 28.2           | 32.5         | 31.6          | 38.3             | 36.9                      |
| Avg.     | 28.8           | 31.5         | 30.8          | 37.3             | 36.0                      |

Additionally, our model complements Aya effectively, especially in low-resource settings.

| Language          | mT5  | Aya_1 | Aya_1 + MURI_1 |
|-------------------|------|-------|----------------|
| aze               | 20.4 | 37.0  | 39.5           |
| bel               | 22.4 | 32.1  | 33.7           |
| bul               | 20.7 | 34.4  | 38.1           |
| cym               | 18.4 | 33.0  | 35.5           |
| gla               | 19.3 | 28.7  | 35.2           |
| kaz               | 19.8 | 44.7  | 46.7           |
| khm               | 16.5 | 30.0  | 31.3           |
| lao               | 21.3 | 32.7  | 33.0           |
| slk               | 19.2 | 38.1  | 39.1           |
| slv               | 18.9 | 40.3  | 39.6           |
| Avg.              | 19.7 | 35.1  | 37.2           |


## Implementation Steps
We will release scripts to replicate the multilingual reverse instructions process soon.

## Limitations
Our dataset quality could be enhanced by removing extraneous elements like headers and footers from documents. MURI's effectiveness in low-resource languages also depends on improving the standardization of input data. Evaluation by native speakers highlighted deficits in dialect and orthographic variation, which we aim to address in future work.

## Citation
[PLACEHOLDER]
