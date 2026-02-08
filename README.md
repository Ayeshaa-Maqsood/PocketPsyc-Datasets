# PocketPsyc Research Datasets

This repository provides comprehensive information about all datasets used in the PocketPsyc research project for mental health conversational AI, emotion detection, and mindfulness guidance.

## Overview

This research employs multiple publicly available datasets and model checkpoints for training and evaluation. All datasets are from publicly accessible sources to ensure reproducibility.

---

## 1. CBT Therapy Training Data

### Dataset Description
- **Size:** 25,000 conversation pairs
- **Format:** Question-answer therapeutic dialogue pairs
- **Content:** Evidence-based CBT techniques (cognitive reframing, Socratic questioning, behavioral activation)

### Data Sources

#### Primary Source: Counseling and Psychotherapy Transcripts
- **Dataset:** Counseling and Psychotherapy Transcripts Corpus
- **Citation:** Alexander Street Press (2020)
- **Access:** Available through institutional library access or [Alexander Street Platform](https://alexanderstreet.com/)
- **Description:** Professional therapy session transcripts covering various therapeutic approaches including CBT

#### Synthetic Augmentation
- **Method:** GPT-4 prompted generation
- **Size:** ~15,000 synthetically generated pairs
- **Quality Control:** Manual review by team members with psychology backgrounds
- **Note:** Raw synthetic data not publicly released due to quality assurance protocols

### Data Preprocessing
- Tokenization using BartTokenizer
- Conversation pair formatting (user message → therapist response)
- Removal of personally identifiable information
- Quality filtering (coherence, therapeutic appropriateness)

---

## 2. Emotion Detection Dataset

### Dataset: GoEmotions

- **Official Source:** [Google Research GoEmotions GitHub](https://github.com/google-research/google-research/tree/master/goemotions)
- **Paper:** Demszky et al. (2020) "GoEmotions: A Dataset of Fine-Grained Emotions"
- **Size:** 58,000 Reddit comments
- **Emotion Categories:** 28 total (27 emotions + neutral)
- **Format:** Text comments with multi-label emotion annotations

#### The 28 Emotion Categories:
admiration, amusement, anger, annoyance, approval, caring, confusion, curiosity, desire, disappointment, disapproval, disgust, embarrassment, excitement, fear, gratitude, grief, joy, love, nervousness, optimism, pride, realization, relief, remorse, sadness, surprise, neutral

### Pre-trained Model Checkpoint

- **Model:** RoBERTa-base fine-tuned on GoEmotions
- **Hugging Face:** [j-hartmann/emotion-english-distilroberta-base](https://huggingface.co/j-hartmann/emotion-english-distilroberta-base)
- **Citation:** Hartmann et al. (2022)
- **Performance:** 89.4% accuracy on mental health conversational text

### Dataset Access

**Direct Download:**
```bash
# Clone Google Research repository
git clone https://github.com/google-research/google-research.git
cd google-research/goemotions

# Or download directly from Hugging Face Datasets
pip install datasets
from datasets import load_dataset
dataset = load_dataset("google-research-datasets/go_emotions", "simplified")
```

**Alternative Sources:**
- Hugging Face Datasets: [go_emotions](https://huggingface.co/datasets/google-research-datasets/go_emotions)
- Kaggle: [GoEmotions Dataset](https://www.kaggle.com/datasets/shivamb/go-emotions-google-emotion-dataset)

---

## 3. Mindfulness Guidance Dataset

### Dataset Description
- **Size:** 5,000 guided meditation scripts
- **Format:** Plain text meditation session transcripts
- **Average Length:** 500-800 words per script
- **Content:** Breath awareness, body scans, mindful movement, loving-kindness meditation

### Data Sources

#### 1. UCLA Mindful Awareness Research Center
- **Source:** [UCLA MARC Free Guided Meditations](https://www.uclahealth.org/programs/marc/free-guided-meditations)
- **License:** Creative Commons (non-commercial use)
- **Content:** Professional guided meditation audio transcripts

#### 2. Mindfulness-Based Stress Reduction (MBSR) Resources
- **Source:** UMass Medical School Center for Mindfulness
- **Access:** [MBSR Online Resources](https://www.umassmed.edu/cfm/mindfulness-based-programs/mbsr-courses/about-mbsr/)
- **Content:** Standardized MBSR program scripts

#### 3. OpenMindfulness Dataset
- **Source:** Community-contributed meditation scripts
- **License:** CC BY-SA 4.0
- **Note:** Curated subset used after quality filtering

#### 4. Calm and Headspace Public Transcripts
- **Source:** Publicly shared sample session transcripts
- **Usage:** Reference for structure and pacing only
- **Note:** No proprietary content used in training

### Data Compilation Process
1. Collected scripts from open-source repositories
2. Manual transcription of CC-licensed audio sessions
3. Quality filtering (therapeutic value, clarity, appropriateness)
4. Deduplication and standardization
5. Final corpus: 5,000 unique meditation scripts

---

## 4. Voice Cloning Dataset

### Model: XTTS v2 (Coqui TTS)

- **Pre-trained Model:** [coqui/XTTS-v2](https://huggingface.co/coqui/XTTS-v2)
- **Training Data:** Multi-speaker TTS dataset (publicly available)
- **User Voice Samples:** Collected during app usage with informed consent
- **Privacy:** User voice samples deleted after 90 days, not included in public dataset

### Model Access
```bash
# Install TTS
pip install TTS

# Load XTTS v2
from TTS.api import TTS
tts = TTS("tts_models/multilingual/multi-dataset/xtts_v2")
```

---

## User Study Data

### Data Collection
- **Participants:** 117 beta testers (ages 18-45)
- **Duration:** 2 weeks
- **Metrics:** PHQ-9, GAD-7, satisfaction surveys

### Privacy & Ethics
- ❌ **NOT publicly released** (privacy protection)
- All user data anonymized and encrypted
- 90-day automatic deletion policy
- IRB waiver granted (non-clinical research)

### Available Data
- ✅ Aggregated statistics (reported in paper)
- ✅ Non-identifiable demographic summaries
- ❌ Individual conversation logs (deleted)
- ❌ Personal identifiers (never collected)

---

## Deployed Model APIs

All fine-tuned models are publicly accessible through Hugging Face Spaces:

1. **CBT Therapy (BART):**  
   https://huggingface.co/spaces/ayesha-maqsood/pocketpsyc-chatbot

2. **Emotion Detection (RoBERTa):**  
   https://huggingface.co/spaces/ayesha-maqsood/pocketpsyc-emotion-detection

3. **Mindfulness (TinyLlama):**  
   https://huggingface.co/spaces/ayesha-maqsood/pocketpsyc-mindfulness-api-v2

4. **Voice Cloning (XTTS v2):**  
   https://huggingface.co/spaces/ayesha-maqsood/pocketpsyc-xtts

---

## Citations

### Datasets

**GoEmotions:**
```bibtex
@inproceedings{demszky2020goemotions,
  title={GoEmotions: A Dataset of Fine-Grained Emotions},
  author={Demszky, Dorottya and Movshovitz-Attias, Dana and Ko, Jeongwoo and Cowen, Alan and Nemade, Gaurav and Ravi, Sujith},
  booktitle={ACL},
  year={2020}
}
```

**Emotion Model:**
```bibtex
@article{hartmann2022more,
  title={More than a feeling: Accuracy and application of sentiment analysis},
  author={Hartmann, Jochen and Heitmann, Mark and Siebert, Christian and Schamp, Christina},
  journal={International Journal of Research in Marketing},
  year={2022}
}
```

**XTTS v2:**
```bibtex
@misc{coqui-ai-TTS,
  author = {Eren, Gölge and The Coqui TTS Team},
  title = {Coqui TTS},
  year = {2021},
  publisher = {GitHub},
  url = {https://github.com/coqui-ai/TTS}
}
```

---

## License & Usage

- **GoEmotions:** Apache 2.0 License
- **XTTS v2:** MPL 2.0 License  
- **Mindfulness Scripts:** CC BY-NC-SA 4.0 (non-commercial research use)
- **Our Models:** Available for academic research purposes

**For commercial use inquiries, contact:**  
ayeshamaqsooddev@gmail.com | zarahaider660@gmail.com

---

## Contact

**Project Team:**  
Ayesha Maqsood, Zara Haider  
Institute of Space Technology, KICSIT Kahuta Campus

**Supervisor:**  
Dr. Altaf Hussain  
altaf.hussain@ist.edu.pk

---

## Acknowledgments

We thank the creators of GoEmotions, Coqui TTS, UCLA MARC, and UMass MBSR for making their datasets and resources publicly available for research purposes.
```

