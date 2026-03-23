# 🐆 Jaguar Individual Re-Identification using EVA-02

> Fine-tuning EVA-02 (a state-of-the-art Vision Transformer) for wildlife conservation — identifying individual jaguars from camera-trap imagery using their unique spot patterns.

---

## 📌 Overview

Individual animal identification is a cornerstone of wildlife conservation, enabling population monitoring, territory tracking, and behavioral research — without invasive tagging. This project applies **EVA-02**, a powerful ViT-based vision foundation model, to the task of **jaguar re-identification (Re-ID)**: given a query image of a jaguar, retrieve or match its identity from a gallery of known individuals.

The model leverages the **Jaguar Re-Identification Kaggle Challenge** dataset, which contains camera-trap images of jaguars from Brazil's Pantanal region, annotated with individual identities.

---

## 🧠 Model Architecture

| Component | Details |
|---|---|
| **Backbone** | EVA-02 (ViT-L/14 or ViT-B/16) — pretrained on merged vision datasets |
| **Task** | Metric learning / Re-Identification |
| **Loss** | ArcFace / Triplet Loss (fine-tuned) |
| **Input** | Camera-trap images (jaguar crops) |
| **Output** | 512-d / 1024-d embedding vectors for similarity matching |

**Why EVA-02?**
EVA-02 is a next-generation vision transformer that incorporates masked image modeling pretraining, achieving state-of-the-art performance on representation learning tasks. Its rich semantic embeddings make it well-suited for fine-grained re-identification, where subtle differences in fur patterns must be captured.

---

## 📂 Repository Structure

```
Jaguar-identification-EVA02/
│
├── jaguar-reid-eva02.ipynb     # Main training & evaluation notebook
└── README.md
```

---

## 🗂️ Dataset

**Jaguar Re-Identification Challenge** — [Kaggle Competition](https://www.kaggle.com/competitions/jaguar-re-id)

- Camera-trap images of wild jaguars from Brazil's Pantanal
- Annotated with individual jaguar identities
- Covers significant pose, lighting, and occlusion variation
- Objective: Match query images to the correct individual in a gallery set

To use the dataset:
```bash
kaggle competitions download -c jaguar-re-id
```

---

## 🚀 Getting Started

### Prerequisites

```bash
pip install torch torchvision timm opencv-python pandas numpy matplotlib kaggle
```

### Run the Notebook

1. Clone the repo:
```bash
git clone https://github.com/Sarthak-404/Jaguar-identification-EVA02.git
cd Jaguar-identification-EVA02
```

2. Download the dataset from Kaggle and place it in the working directory.

3. Open and run the notebook:
```bash
jupyter notebook jaguar-reid-eva02.ipynb
```

---

## ⚙️ Pipeline

```
Camera-Trap Images
        │
        ▼
  Preprocessing & Augmentation
  (resize, normalize, random flip/crop)
        │
        ▼
  EVA-02 Backbone (frozen / partially frozen)
        │
        ▼
  Embedding Head (Linear / ArcFace)
        │
        ▼
  Metric Learning Training
  (ArcFace / Triplet Loss)
        │
        ▼
  Gallery Embedding Index
        │
        ▼
  Query → Cosine Similarity → Top-K Match
```

## 🌿 Conservation Impact

Jaguar populations have declined significantly due to habitat loss and poaching. Automated individual identification from camera traps allows researchers to:

- Accurately estimate population size using mark-recapture methods
- Track individual territory and movement patterns
- Monitor high-risk individuals without physical intervention
- Scale monitoring across large, remote ecosystems

---

## 🔗 References

- [EVA-02: A Visual Representation Powerhouse](https://arxiv.org/abs/2303.11331)
- [Jaguar Re-ID Kaggle Challenge](https://www.kaggle.com/competitions/jaguar-re-id)
- [WildlifeDatasets Toolkit](https://arxiv.org/abs/2311.09118)
- [ArcFace: Additive Angular Margin Loss](https://arxiv.org/abs/1801.07698)

---

## 👤 Author

**Sarthak Sachan**
- GitHub: [@Sarthak-404](https://github.com/Sarthak-404)
- LinkedIn: [sarthak-sachan-99b836291](https://linkedin.com/in/sarthak-sachan-99b836291)

---

## 📄 License

This project is open-sourced under the MIT License.
