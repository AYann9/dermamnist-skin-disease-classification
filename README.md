# dermamnist-skin-disease-classification
Skin disease classification on DermaMNIST-64 dataset: A comparative study of ResNet18 (CNN) and ViT-Tiny (Vision Transformer) for 7-category dermatological lesion diagnosis, with class imbalance handling, model evaluation and interpretability analysis.

---

# 📂 Dataset Preparation
This project uses **DermaMNIST-64** (64×64 RGB, 7-class skin disease dataset) for model training and evaluation.

## 1. For ResNet18 (Required local dataset file)
The ResNet18 code reads data from a local `.npz` file.
- Please download `dermamnist_64.npz` first
- Place it **in the project root directory** (same level as the `.ipynb` files)
- The code will automatically load the dataset from this local file

## 2. For ViT-Tiny (No local file required)
The ViT-Tiny code uses the official `medmnist` API.
- **No need to download any dataset in advance**
- When you run the code, the dataset will be **automatically downloaded** to the default path
- Just run the notebook directly

---

## Full Standard README (With Clear Data Instructions)
# Skin Disease Classification with ResNet18 & ViT-Tiny
### DermaMNIST 7-Class Skin Lesion Classification | CNN vs Vision Transformer

---

## 🔍 Project Overview
This project implements a **computer-aided diagnosis (CAD) system** for **7-category skin disease classification** on the **DermaMNIST-64** dataset.
We build, train, and comprehensively compare two mainstream deep learning architectures:
- **ResNet18 (CNN)** – as the CNN baseline model
- **ViT-Tiny (Vision Transformer)** – as the Transformer-based model

The project includes full pipelines: data exploration → preprocessing & augmentation → model training → quantitative evaluation → interpretability visualization.

---

## 📂 Dataset Preparation
This project uses **DermaMNIST-64** (64×64 RGB, 7-class skin disease dataset).

### 1. For ResNet18 (Required local dataset file)
The ResNet18 code reads data from a local `.npz` file.
- Please download `dermamnist_64.npz` first
- Place it **in the project root directory** (same level as the `.ipynb` files)
- The code will automatically load the dataset from this local file

### 2. For ViT-Tiny (No local file required)
The ViT-Tiny code uses the official `medmnist` API.
- **No need to download any dataset in advance**
- When you run the code, the dataset will be **automatically downloaded** to the default path
- Just run the notebook directly

---

## 🧰 Environment Setup
```bash
# Install required packages
pip install torch torchvision timm medmnist numpy matplotlib seaborn scikit-learn pytorch-grad-cam
```

---

## 🚀 How to Run
1. Clone this repository
2. Prepare dataset (follow instructions above)
3. Run notebook files:
   - `ResNet18.ipynb` – CNN model training & evaluation & Grad-CAM
   - `ViT_tiny_patch16_224.ipynb` – ViT model training & evaluation & Attention Map

---

## 📁 Project Structure
```
├── ResNet18.ipynb              # CNN baseline implementation
├── ViT_tiny_patch16_224.ipynb  # Vision Transformer implementation
├── results/                    # ROC, confusion matrix, visualization images
└── README.md                   # Project description
```

---

## 📈 Experimental Results
### Test Set Performance (Weighted Average)
| Model | Accuracy | Precision | Recall | F1-score |
|-------|----------|-----------|--------|----------|
| ResNet18 | 72.569% | 68.335% | 72.569% | 69.944% |
| ViT-Tiny | **85.786%** | **85.660%** | **85.786%** | **85.641%** |

### AUC Performance
- ResNet18: 0.85 – 0.93
- ViT-Tiny: 0.93 – 1.00 (Class 6 AUC = 1.00)

### Confusion Matrix Key Observations
- **ResNet18**: Strongly biased toward majority class (Class 5: 92.2%); Classes 0/4 only ~20%
- **ViT-Tiny**: Balanced performance; Classes 3/5/6 > 87%; Classes 0/4 greatly improved

### Interpretability
- ResNet18: Grad-CAM (blurry localization, weak focus on lesions)
- ViT-Tiny: Attention Map (precise focus on skin lesions, better clinical interpretability)

---

## 🧠 Model Comparison
1. **Performance**: ViT-Tiny outperforms ResNet18 by **+13.217%** accuracy
2. **Data Efficiency**: ViT benefits more from strong augmentation & robust to imbalance
3. **Computation**: ResNet18 is lighter; ViT requires higher GPU memory
4. **Interpretability**: ViT attention maps are more reliable for medical images
5. **Generalization**: ViT generalizes much better on minority classes

---

## 💡 Key Conclusions
1. Vision Transformer (ViT-Tiny) is **more suitable** for fine-grained skin disease classification than traditional CNN.
2. Data augmentation & advanced training tricks (label smoothing, mixup) significantly improve ViT performance.
3. Class imbalance severely affects CNN; ViT shows stronger robustness.
4. Transformer’s self-attention provides better interpretability for clinical diagnosis.

---

## 📦 Pre-trained Models
The trained model weights (.pth files) are **not uploaded** due to GitHub file size limits.

### How to get models:
1. **Auto-generate (Recommended)**
   Run the training notebook, the best model will be automatically saved in the corresponding folder.

---

## 🔧 Future Improvements
1. Add class-weighted loss / oversampling to handle imbalance
2. Unify augmentation for fair CNN–ViT comparison
3. Use larger models (EfficientNet, ViT-Base)
4. Build ensemble model for higher stability
5. Optimize inference speed for clinical deployment

---

## 📝 License
This project is for **academic & educational use only**.
