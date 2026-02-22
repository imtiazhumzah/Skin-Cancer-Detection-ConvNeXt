# Clinical-Grade Melanoma Detection using ConvNeXt & XAI

**Author:** [Imtiaz Ali](https://github.com/imtiazhumzah) | [Live Demo on Hugging Face](https://huggingface.co/spaces/imtiazhumzah/Skin-Cancer-Detection-ConvNeXt)

---

## Project Objective
To develop a robust, physician-aligned classification system for skin lesions. This project prioritizes a **Recall of 90%+ for Melanoma**, ensuring high sensitivity in clinical triage to minimize life-threatening false negatives.

## Technical Highlights
* **Architecture:** **ConvNeXt-Tiny** — A modernized CNN backbone that outperforms standard ResNets and Transformers in dermatological texture recognition.
* **Leakage Prevention:** Implemented strict **Patient-Level Splitting (GroupShuffleSplit)**. This ensures the model generalizes to new patients rather than memorizing specific skin tones.
* **Loss Function:** **Weighted Focal Loss ($\gamma=3$)**. Mathematically forces the model to focus on rare malignant samples over common benign cases.
* **Explainability (XAI):** Integrated **Guided Grad-CAM** to provide visual "heat-maps," allowing clinicians to verify the diagnostic features used by the AI.

## Performance Metrics
*Evaluated on a rigorous held-out test set of unseen patients (N=1494).*

| Metric | Validation (Internal) | Test (Unseen Patients) | Why it matters |
| :--- | :--- | :--- | :--- |
| **Overall Accuracy** | **97.20%** | **83.87%** | Reliability across all 7 lesion categories. |
| **Melanoma Sensitivity** | **94.10%** | **90.00%** | **Safety:** Specifically minimizes missed cancers. |
| **Macro F1-Score** | **0.92** | **0.71** | Balanced performance on imbalanced data. |

## Explainability (XAI)

The integration of Grad-CAM ensures the model focuses on clinically relevant morphology (irregular borders, pigment networks) rather than background artifacts like hair or skin markers.

## Ethics & Privacy
* **Bias Awareness:** Performance was validated on the HAM10000 dataset; results may vary across diverse Fitzpatrick skin scales.
* **Data Minimization:** This system is stateless; user uploads are processed in-memory and never stored.

> **⚠️ Medical Disclaimer:** This tool is for **research and educational purposes only**. It is not intended to replace professional medical diagnosis. Always consult a board-certified dermatologist.

---
## Installation & Usage
```bash
git clone [https://github.com/imtiazhumzah/Skin-Cancer-Detection-ConvNeXt.git](https://github.com/imtiazhumzah/Skin-Cancer-Detection-ConvNeXt.git)
pip install -r requirements.txt
python app.py
