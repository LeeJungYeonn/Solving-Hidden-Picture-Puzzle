# Solving Hidden Picture Puzzle

This project provides a **standalone Google Colab demo** for solving a **Hidden Picture Puzzle**.The recommended way to use this project is to **clone the entire repository inside Colab**, which includes the dataset.

The goal of the project is to automatically identify and solve hidden picture puzzles by analyzing the given images and revealing concealed objects or patterns. The demo allows users to reproduce the core functionality of the proposed approach using the provided dataset with minimal setup.

---

## Repository Structure

```
.
├── dataset/
│   ├── scenes/                    # Hidden picture scene images
│       └── *.(JPG|jpg|jpeg)  
│   ├── templates/                 # Object templates
│       └── *.(JPG|jpg|jpeg)  
│   └── ground-truth/              # Ground-truth for each category
│       ├── ce-ground-truth.csv    
│       ├── ch-ground-truth.csv
│       ├── ge-ground-truth.csv
│       └── gh-ground-truth.csv  
├── result/
│   ├── <scene_image>/             # One folder per scene image containing solving results
│   ├── ge_batch_summary.csv       # Batch summary for 'ge' category
│   └── gh_batch_summary.csv       # Batch summary for 'gh' category
├── test/
│   └── *.(Jpg|jpg)                # Two test scene images
├── test_result/
│   ├── <scene_image>/             # Solved test images
│   └── batch_summary.csv          # Evaluation metrics to test result
└── demo.ipynb                     # Main demo notebook
```

---

## Quick Start (Google Colab – Recommended)

### 1. Open Google Colab
Create a new notebook or open an existing one.

### 2. Clone the Repository

```bash
!git clone https://github.com/Hidden-Picture-Puzzle/Solving-Hidden-Picture-Puzzle.git
%cd Solving-Hidden-Picture-Puzzle
!ls
```

Please check all required folders, including the dataset, are cloned into the Colab environment.

---

### 3. Install Requirements (if needed)

```bash
!pip install -r requirements.txt
```

> Most dependencies are available in the default Google Colab environment.

---

### 4. Run the Demo

To open and run the demo notebook (demo.ipynb) in Colab, follow these steps:
* Go to File → Open Notebook → GitHub.
* Enter the repository URL:

  ```bash
  https://github.com/Hidden-Picture-Puzzle/Solving-Hidden-Picture-Puzzle.git
  ```
* Select `demo.ipynb` from the list and click Open.
* Run all cells in the notebook.

The demo uses **relative paths based on the repository root** and does not require Google Drive.

---

## Dataset Overview

* **Scene images (`dataset/scenes`)**: Input hidden picture images
* **Templates (`dataset/templates`)**: Objects to be detected in scenes
* **Ground truth (`dataset/ground-truth`)**:

  * ce/ch/ge/gh-ground-truth.csv: Annotation file

---

## Test and Evaluation

* `test/` contains two unseen test scene images
* `test_result/` stores:

  * Solved test images
  * `batch_summary.csv`, which reports accuracy and evaluation metrics computed from the test results

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
