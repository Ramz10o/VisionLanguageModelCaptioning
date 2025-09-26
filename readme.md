# GoPro Street-View Image Captioning

This project generates natural language captions for street-view images captured using a GoPro camera during a journey. Since no ground-truth captions were available, manual annotations were created for evaluation.

---

## Objective
Generate descriptive captions for sequential GoPro images using Vision-Language Models (VLMs) in zero-shot mode.

---

## Dataset
- **Source:** 95 RGB images from a GoPro camera  
- **Characteristics:** Sequential journey frames, varied lighting, occasional motion blur  
- **Storage:** Google Drive (used in Colab)

[Download Dataset](https://dhineumlassignment.s3.us-east-1.amazonaws.com/goPro.zip)

---

##  Preprocessing
- Convert images to RGB
- Resize to 224×224 pixels (BLIP/ViT standard)
- Normalize pixel values to [0,1]
- Saved preprocessed images to a dedicated folder
- Manual captions stored in `manual_captions.csv` ([filename, caption]) for evaluation

---

## Captioning
- **Model:** `Salesforce/blip-image-captioning-base` (Hugging Face)  
- Zero-shot inference on all preprocessed images  
- Captions saved in `captions_baseline.csv`  

---

## Evaluation
Metrics comparing zero-shot captions against manual annotations:

| Metric | Score |
|--------|-------|
| BLEU   | 0.8625 |
| METEOR | 0.9091 |

**Observations:**
- Captions are fluent but sometimes generic (e.g., “a street with buildings”)  
- High BLEU indicates exact overlap, METEOR shows semantic alignment  
- Manual annotations allow quantitative evaluation

---

## Results
- Annotated images saved with captions overlayed (`annotated_gallery/`)  
- Zero-shot BLIP captions are reasonable; partial fine-tuning could improve specificity  
- Pipeline supports frame sampling and journey summarization  

---

## Deliverables
- **Captioning Model:** BLIP zero-shot (`Salesforce/blip-image-captioning-base`)  
- **Sample Predictions:** Annotated images with captions  
- **Evaluation:** BLEU and METEOR scores  
- **Report:** This README documenting approach and results

---

## Usage
1. Preprocess images  
2. Generate captions using BLIP  
3. Evaluate against manual annotations  
4. (Optional) Sample frames and overlay captions for visualization  
5. (Optional) Summarize journey from captions

---

## References
- [BLIP Model on Hugging Face](https://huggingface.co/Salesforce/blip-image-captioning-base)  
- [Hugging Face Transformers](https://huggingface.co/docs/transformers)
