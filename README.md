# Solving Hidden Picture Puzzle

This project provides a **standalone Google Colab demo** for solving a **Hidden Picture Puzzle**.The recommended way to use this project is to **clone the entire repository inside Colab**, which includes the dataset.

The goal of the project is to automatically identify and solve hidden picture puzzles by analyzing the given images and revealing concealed objects or patterns. The demo allows users to reproduce the core functionality of the proposed approach using the provided dataset with minimal setup.

---

## Repository Structure

```
.
├── dataset/
│   ├── scene/                     # Hidden picture scene images
│   ├── templates/                 # Object templates
│   └── ground-truth/
│       ├── answers.csv            # Ground-truth annotations
│       └── *.png                  # Ground-truth answer images
├── test/
│   └── *.(jpg|jpeg|png)           # Two test scene images
├── result/
│   └── */                         # Per-scene solving results
├── test_result/
│   ├── *.(jpg|jpeg|png)           # Solved test images
│   └── metrics.csv                # Evaluation metrics
└── demo.ipynb                     # Main demo notebook
```

---

## Quick Start (Google Colab – Recommended)

### 1. Open Google Colab
Create a new notebook or open an existing one.

### 2. Clone the Repository

```bash
!git clone https://github.com/USERNAME/Solving-Hidden-Picture-Puzzle.git
%cd REPOSITORY_NAME
```

All required folders, including the dataset, are cloned into the Colab environment.

---

### 3. Install Requirements (if needed)

```bash
!pip install -r requirements.txt
```

> Most dependencies are available in the default Google Colab environment.

---

### 4. Run the Demo

Open `demo.ipynb` and run **all cells**.

The demo uses **relative paths based on the repository root** and does not require Google Drive.

---

## Dataset Overview

* **Scene images (`dataset/scene`)**: Input hidden picture images
* **Templates (`dataset/template`)**: Objects to be detected in scenes
* **Ground truth (`dataset/ground_truth`)**:

  * `answers.csv`: Annotation file
  * Answer images for visualization and evaluation

---

## Test and Evaluation

* `test/` contains two unseen test scene images
* `test_result/` stores:

  * Solved test images
  * `metrics.csv`, which reports accuracy and evaluation metrics computed from the test results

---

## Evaluation Metrics

The performance of the hidden picture solving algorithm is evaluated using both **localization accuracy** and **overlap quality**.

For each detected object, the following metrics are computed:
* **Center Distance**

  * The Euclidean distance between the center of the detected bounding box and the center of the corresponding ground-truth bounding box
  * Measures how accurately the object location is estimated
    
* **Intersection over Union (IoU)**

  * Measures the overlap ratio between the detected bounding box and the ground-truth bounding box
  * Defined as the area of overlap divided by the area of union

All evaluation results are aggregated and saved in `test_result/metrics.csv`.
    
---

## Supported Image Formats

Images may have mixed file extensions. The demo handles image files in a **case-insensitive** manner.

**Supported formats:**

* JPG (jpg) / JPEG (jpeg)
* PNG (png)

---

## Requirements

The following Python packages are required to run the demo:

```
numpy
opencv-python
opencv-contrib-python
scipy
joblib
pandas
```

All listed packages are compatible with the default Google Colab environment.

---

## Notes

* This demo is fully **standalone** and does not require Google Drive mounting.
* Paths are managed internally using relative directory references for reproducibility.
* Results generated during execution are saved locally within the Colab session.
