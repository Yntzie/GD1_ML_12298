# Klasifikasi Iris — Perceptron & Adaline (GD & SGD)

Notebook latihan ini membangun dan memvisualisasikan model **Perceptron** serta **Adaline** (Gradient Descent & Stochastic Gradient Descent) pada subset dataset **Iris** (Setosa vs Versicolor; 2 fitur: *sepal length* & *petal length*) agar mudah divisualisasikan dalam grafik 2D.

## Ringkasan Materi di Notebook
1. **Persiapan & impor pustaka**  
2. **Memuat data** (CSV dari UCI) & cek isi  
3. **Pra‑proses & visualisasi data**  
4. **Model 1: Perceptron** + grafik error + **decision boundary**  
5. **Model 2: AdalineGD (Batch GD)** + efek learning rate + **standardisasi** + grafik loss  
6. **Model 3: AdalineSGD (SGD)** + decision boundary + grafik loss + *partial fit*  
7. **Prediksi data baru** (Perceptron vs AdalineGD vs AdalineSGD)

> Catatan: Notebook hanya memakai 2 fitur (sepal length & petal length) untuk mempermudah visualisasi 2D.

---

## Prasyarat
- **Python** 3.9+ (disarankan 3.10/3.11)
- **pip** terbaru
- Salah satu: **Jupyter Notebook**, **JupyterLab**, atau **VS Code** + *Python extension*

## Dependensi (minimal)
- `numpy`
- `pandas`
- `matplotlib`
- (opsional) `scikit-learn` – bila ingin memakai utilitas split/standardisasi siap pakai

---

## Cara Clone & Instalasi

### 1) Clone repository

```bash
git clone git@github.com:Yntzie/GD1_ML_12298.git
cd iris-perceptron-adaline
```

Jika proyek Anda belum ada di GitHub, buat folder lokal lalu salin notebook ke dalamnya:
```bash
mkdir iris-perceptron-adaline
cd iris-perceptron-adaline
```

### 2) Buat virtual environment (disarankan)
**Windows (PowerShell):**
```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

**macOS/Linux (bash/zsh):**
```bash
python3 -m venv .venv
source .venv/bin/activate
```

Jika belum punya `requirements.txt`, instal paket minimal berikut:
```bash
pip install --upgrade pip
pip install numpy pandas matplotlib
# opsional (jika ingin pakai utilitas sklearn):
pip install scikit-learn
```

---

## Menjalankan Notebook
Pilih salah satu cara:

**Jupyter Notebook/Lab**
```bash
jupyter notebook
# atau
jupyter lab
```
Buka file notebook Anda (mis. `iris_perceptron_adaline.ipynb`).

**VS Code**
1. Buka folder proyek di VS Code.
2. Buka file `.ipynb`.
3. Pilih kernel dari venv `.venv` bila diminta.

---
