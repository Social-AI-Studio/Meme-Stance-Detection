# Meme-Stance-Detection
Repo for Meme Stance Detection
# Usage
This repository comprises the following folders/subfolders:
- `stance_detection_hf/`: contains Colab notebooks for running experiments using selected Hugging Face models;
- `stance_detection_hf/0000_datasets_preparation`: contains Colab notebooks for downloading the datasets required, reshaping the datasets, taking subsets of the data etc.;
- `stance_detection_hf/1000_captioning`: contains Colab notebooks for captioning the images using selected Hugging Face models;
- `stance_detection_hf/2000_grounding`: contains a Colab notebook for using Qwen-VL-Chat to ground the images with bounding boxes;
- `stance_detection_hf/3000_prediction`: contains Colab notebooks for predicting target labels using selected Hugging Face models;
- `stance_detection_gpt/`: contains Colab notebooks for running experiments using gpt-4-vision-preview;
- `results_hf/`: contains result data obtained using selected Hugging Face models;
- `results_gpt/`: contains result data obtained using gpt-4-vision-preview;

Run the notebooks sequentially with respect to folder name, i.e., notebooks in 0000_datasets_preparation, followed by notebooks in 1000_captioning, 2000_grounding, and 3000_prediction.

Run the notebooks sequentially with respect to notebook name, e.g. 0001_ TDEF_preparation, followed by 0002_TDEF_zero_shot_inference and so on.

# Naming conventions
Result data in `results_hf/` are primarily named using one of the two formats:
```
{dataset-name}_grounding[{grounding}]_caption[{caption}]_prompt[{prompt}]_prediction[{prediction}].csv
```
```
{dataset-name}_grounding[{grounding}]_prompt[{prompt}]_prediction[{prediction}].csv
```
- dataset-name: e.g. total_defense_memes;
- grounding: either <em>ABSENT</em> or <em>PRESENT</em>, indicating whether the predictions were made using images grounded with bounding boxes;
- caption: name of the model used for captioning images;
- prompt: either <em>VANILLA</em> (no captions or OCR text used for prediction), <em>OCR</em> (OCR text used, but no captions used for prediction), <em>CAPTION</em> (captions used for prediction), or <em>CAPTION_{target-labels-used}</em> (e.g. CAPTION_POSITIVENEUTRALNEGATIVE);
- prediction: name of the model used for predicting the target labels;

Result data in `results_gpt/` include:
- total_defense_memes_test_zero_shot_inference.csv: zero-shot predictions made using vanilla prompt (no captions or OCR text used for prediction);
- total_defense_memes_test_zero_shot_w_caption_inference.csv: zero-shot predictions made using captions made by gpt-4-vision-preview;
- total_defense_memes_examples.csv: from which one-shot examples are drawn and used to make one-shot predictions;
- total_defense_memes_test_one_shot_inference.csv: one-shot predictions (no captions used, one example per possible target label included) made using examples drawn from total_defense_memes_examples.csv;

# Datasets
We use datasets presented in the following papers:
- Shivam Sharma, Tharun Suresh, Atharva Kulkarni, Himanshi Mathur, Preslav Nakov, Md. Shad Akhtar, and Tanmoy Chakraborty. 2022. Findings of the CONSTRAINT 2022 Shared Task on Detecting the Hero, the Villain, and the Victim in Memes. In <em>Proceedings of the Workshop on Combating Online Hostile Posts in Regional Languages during Emergency Situations</em>, Tanmoy Chakraborty, Md. Shad Akhtar, Kai Shu, H. Russell Bernard, Maria Liakata, Preslav Nakov, and Aseem Srivastava (Eds.). Association for Computational Linguistics, Dublin, Ireland, 1–11. https://doi.org/10.18653/v1/2022.constraint-1.1
- Shivam Sharma, Md Shad Akhtar, Preslav Nakov, and Tanmoy Chakraborty. 2022. DISARM: Detecting the Victims Targeted by Harmful Memes. In <em>Findings of the Association for Computational Linguistics: NAACL 2022</em>, Marine Carpuat, Marie-Catherine de Marneffe, and Ivan Vladimir Meza Ruiz (Eds.). Association for Computational Linguistics, Seattle, United States, 1572–1588. https://doi.org/10.18653/v1/2022.findings-naacl.118
- Shraman Pramanick, Shivam Sharma, Dimitar Dimitrov, Md. Shad Akhtar, Preslav Nakov, and Tanmoy Chakraborty. 2021. MOMENTA: A Multimodal Framework for Detecting Harmful Memes and Their Targets. In <em>Findings of the Association for Computational Linguistics: EMNLP 2021</em>, Marie-Francine Moens, Xuanjing Huang, Lucia Specia, and Scott Wen-tau Yih (Eds.). Association for Computational Linguistics, Punta Cana, Dominican Republic, 4439–4455. https://doi.org/10.18653/v1/2021.findings-emnlp.379
- Nirmalendu Prakash, Ming Shan Hee, and Roy Ka-Wei Lee. 2023. TotalDefMeme: A Multi-Attribute Meme Dataset on Total Defence in Singapore. In <em>Proceedings of the 14th Conference on ACM Multimedia Systems</em> (Vancouver, BC, Canada) (MMSys ’23). Association for Computing Machinery, New York, NY, USA, 369–375. https://doi.org/10.1145/3587819.3592545
