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

> Jika Anda sudah memiliki `requirements.txt`, cukup jalankan `pip install -r requirements.txt` (lihat bagian Instalasi).

---

## Cara Clone & Instalasi

### 1) Clone repository
Ganti `<username>` dan nama repo sesuai milik Anda.
```bash
git clone https://github.com/<username>/iris-perceptron-adaline.git
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

### 3) Instal dependensi
Jika Anda punya **requirements.txt** di repo:
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

Jika belum punya `requirements.txt`, instal paket minimal berikut:
```bash
pip install --upgrade pip
pip install numpy pandas matplotlib
# opsional (jika ingin pakai utilitas sklearn):
pip install scikit-learn
```

> **Tips VS Code**: pastikan interpreter menunjuk ke venv (`.venv`). Tekan `Ctrl+Shift+P` → *Python: Select Interpreter* → pilih `.venv`.

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

## Data
- Dataset: **Iris** dari UCI Machine Learning Repository.  
  Link referensi: https://archive.ics.uci.edu/ml/datasets/iris  
- Notebook umumnya akan memuat CSV (mis. `iris.csv`) atau langsung mengambil dari `sklearn.datasets`.  
- Untuk mengikuti visualisasi 2D pada notebook, gunakan subset **Setosa vs Versicolor** dan fitur **sepal length** & **petal length** saja.

Contoh muat data (CSV lokal):
```python
import pandas as pd
df = pd.read_csv("iris.csv")
```

Contoh muat data (dari `sklearn` lalu ubah ke DataFrame):
```python
from sklearn import datasets
import pandas as pd

iris = datasets.load_iris(as_frame=True)
df = iris.frame  # kolom: sepal length, sepal width, petal length, petal width, target
```

---

## Struktur Kode (ringkas)
Di awal notebook biasanya terdapat impor berikut:
```python
import numpy as np
import os
import pandas as pd
import matplotlib.pyplot as plt
```
Bagian berikutnya meliputi:
- **Pra‑proses**: filter kelas (Setosa vs Versicolor), pilih 2 fitur, standardisasi (untuk Adaline).
- **Model**: implementasi Perceptron, AdalineGD, AdalineSGD (kelas custom).
- **Training & Evaluasi**: plot error/loss per epoch, plot **decision boundary**.
- **Prediksi**: uji titik baru dengan 3 model di atas.

---

## Troubleshooting
- **`Import "matplotlib.pyplot" could not be resolved from source`**  
  - Pastikan `matplotlib` terinstal di **venv yang aktif**: `pip show matplotlib`  
  - Jika belum ada: `pip install matplotlib` lalu **restart kernel** Jupyter/VS Code.  
  - Di VS Code, pastikan kernel/Interpreter mengarah ke `.venv`.

- **Paket tidak ditemukan** (`ModuleNotFoundError`)  
  - Cek apakah venv aktif (prompt berawalan `(.venv)`).
  - Jalankan `pip install <nama-paket>` di terminal yang sama dengan kernel.

- **Grafik tidak muncul di Jupyter**  
  - Pastikan sel telah dijalankan berurutan.  
  - Di notebook klasik, Anda bisa menambahkan:  
    ```python
    %matplotlib inline
    ```

---

## Contoh `requirements.txt` (opsional)
Jika Anda ingin file `requirements.txt`, isi minimalnya:
```
numpy
pandas
matplotlib
# opsional:
scikit-learn
```

---

## Lisensi
Pilih lisensi sesuai kebutuhan (mis. MIT).

---

## Kredit
Notebook ini merangkum topik **Perceptron** dan **Adaline (GD & SGD)** pada dataset **Iris** untuk tujuan pembelajaran dan visualisasi 2D.
