# Anemia Detection Model Collection

A downloader and comparison toolkit for four community-built anemia detection models hosted on Hugging Face. Each model screens for anemia from a different body site: fingernails, conjunctiva, general pallor, and a multimodal fusion approach.

## Why this exists

Anemia screening research uses several visual proxies for low hemoglobin: pallor in the nail bed, conjunctiva, and skin. This repo pulls together four independent, openly published models so you can run them side by side and compare approaches.

## Models

### 1. Nail Anemia Detector (`JetX-GT/nail-anemia-detector`)
Extracts handcrafted color features (brightness, redness, pallor ratios) from fingernail images and classifies with an MLP. Trained on 3,406 images from 443 patients in the Ghana fingernail anemia dataset (Asare et al., 2022, Mendeley Data). Reported performance: AUC 0.75, accuracy 73%, recall 90%, specificity 46%. A high-sensitivity mode (threshold 0.255) trades specificity for 100% recall, meant for screening followed by a confirmatory blood test.

### 2. Anemia Palor Detection (`galihkjaya/anemia-palor-detection`)
Image classification model targeting visible pallor as an anemia indicator.

### 3. ViT Anemia Conjunctiva (`thismad/vit-anemia-conjunctiva`)
Vision Transformer model classifying anemia from conjunctiva (inner eyelid) images. The conjunctiva is a common screening site in published anemia research since it stays visible and free of melanin.

### 4. Attention Fusion Anemia Model (`DrateHillary/Attention_Fusion_Anemia_Model`)
Combines multiple input signals through an attention fusion architecture rather than relying on a single image type.

## Setup

```bash
pip install huggingface_hub
```

## Download all models

```bash
python download_anemia_models.py
```

Each model downloads into its own folder:

```
Attention_Fusion_Anemia_Model/
anemia-palor-detection/
vit-anemia-conjunctiva/
nail-anemia-detector/
```

## Project structure

```
.
├── README.md
├── download_anemia_models.py
├── Attention_Fusion_Anemia_Model/
├── anemia-palor-detection/
├── vit-anemia-conjunctiva/
└── nail-anemia-detector/
```

## Limitations

None of these models diagnose anemia. Each is a screening tool built on a limited dataset from a single research group. Treat outputs as a signal to follow up with a real blood test, not a result on its own.

## Credits

All model weights and original documentation belong to their respective authors on Hugging Face: DrateHillary, galihkjaya, thismad, and JetX-GT. This repo only bundles a downloader and a side-by-side summary.
