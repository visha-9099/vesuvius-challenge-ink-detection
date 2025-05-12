🧠 Vesuvius Challenge – Ancient Ink Detection from Scrolls
The vesuvius-challenge-ink-detection project focuses on solving one of the most fascinating challenges in modern digital humanities and computer vision: detecting hidden ink in ancient Herculaneum scrolls carbonized during the eruption of Mount Vesuvius in 79 AD. 
This project is part of the Vesuvius Challenge, which aims to virtually unroll and read these ancient texts without physically opening them, preserving fragile historical artifacts.

🏛️ Background
The Herculaneum papyri are a library of scrolls buried under volcanic ash, preserved but carbonized and unreadable to the naked eye. 
Traditional unrolling methods risk destroying the scrolls. Recent advances in X-ray phase-contrast tomography (XPCT) and machine learning allow researchers to "virtually unroll" the scrolls and detect ink hidden within their layers.

🎯 Project Objective
The primary objective of this project is to build a robust deep learning model that can identify the presence of ink in volumetric 3D scans of scroll fragments, even when the ink is nearly invisible to human perception.

📁 Dataset Description
The dataset consists of:

3D volumetric scans of scroll fragments as stacked 2D grayscale image slices.

Ground truth labels indicating areas where ink is known to be present.

Multiple samples representing different scroll fragments or regions with varying resolution and noise.

🧪 Methodology
1. Preprocessing
Loaded and stacked grayscale image slices into 3D tensors.

Applied histogram equalization, denoising, and normalization.

Extracted patches (cubic volumes) to feed into models for efficient training.

2. Model Architecture
Used advanced deep learning architectures for volumetric segmentation:

3D U-Net: Adapted for 3D spatial context and pixel-level predictions.

2.5D CNNs: Leveraged axial-slice context when memory was constrained.

Data augmentations: Random flips, shifts, elastic deformations, brightness/contrast variation.

3. Training Strategy
Loss Function: Dice loss + BCE (Binary Cross-Entropy)

Optimizer: Adam with Cosine Annealing or OneCycleLR

Validation using IOU/Dice coefficient

📈 Evaluation Metrics
Dice Coefficient – Main metric for evaluating the overlap between predicted ink mask and ground truth.

Precision/Recall – For identifying false positives and negatives.

Visual Inspection – Key step due to subtlety of ink in scan data.

🔬 Challenges Faced
Extremely low contrast between ink and background material.

High variability in scan quality and scroll preservation.

Need for computational efficiency with large 3D volumes.

🚀 Key Results
Successfully trained models that can detect subtle ink patterns on 3D scanned papyri with high accuracy.

Demonstrated generalization to unseen fragments using ensemble techniques and pseudo-labeling.

📦 Repository Structure
bash
Copy
Edit
vesuvius-challenge-ink-detection/
├── data/                      # Scroll volume data and labels
├── notebooks/                 # EDA and model development notebooks
├── src/
│   ├── dataset.py             # Data loaders and transforms
│   ├── model.py               # Model definitions (U-Net etc.)
│   └── train.py               # Training loop
├── outputs/                   # Sample predictions and metrics
├── README.md                  # Project overview
└── requirements.txt           # Dependencies
🛠️ Technologies Used
Python 3.x

PyTorch

OpenCV, NumPy, SciPy

Monai or Kornia (for medical imaging and transformations)

FastAI (optional for training loops)
