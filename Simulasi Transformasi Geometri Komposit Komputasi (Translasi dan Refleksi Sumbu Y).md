# Simulasi Transformasi Geometri Komposit Komputasi (Translasi dan Refleksi Sumbu Y)

Bab ini membahas implementasi komputasi transformasi geometri komposit dua dimensi (2D) menggunakan representasi sistem matriks koordinat homogen berorde $3 \times 3$. Melalui studi kasus ini, kita akan melihat bagaimana operasi pergeseran spasial (_translasi_) dan pencerminan (_refleksi_) digabungkan secara linear menjadi satu matriks tunggal untuk membentuk animasi pergerakan objek persegi.

---

## 1. Representasi Objek Awal & Koordinat Homogen

Objek geometri awal yang digunakan dalam simulasi ini berbentuk persegi yang didefinisikan oleh empat titik sudut utama:

- $A(1, 1)$
- $B(3, 1)$
- $C(3, 3)$
- $D(1, 3)$

Untuk melakukan operasi transformasi komposit secara simultan melalui perkalian matriks, koordinat kartesius 2D $(x, y)$ dikonversi menjadi bentuk **Koordinat Homogen 3D** dengan menambahkan komponen berskala 1 pada baris ketiga:

$$P = \begin{bmatrix} x \\ y \\ 1 \end{bmatrix}$$

---

## 2. Tahap 1: Operasi Translasi Horizontal

Langkah pertama pada setiap iterasi program adalah menggeser objek persegi secara horizontal ke arah kanan sejauh **1 satuan**. Secara pemetaan geometris, rumus pergeseran ini ditulis sebagai:

$$T(x,y) = (x + 1, y)$$

Di dalam sistem koordinat homogen, struktur matriks operator translasi $T$ dirumuskan sebagai:

$$T = \begin{bmatrix} 1 & 0 & 1 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}$$

**Hasil Pemetaan Titik Persegi Efek Translasi (Step 1):**

- $A(1,1) \rightarrow A_1(2,1)$
- $B(3,1) \rightarrow B_1(4,1)$
- $C(3,3) \rightarrow C_1(4,3)$
- $D(1,3) \rightarrow D_1(2,3)$

---

## 3. Tahap 2: Operasi Refleksi Terhadap Sumbu Y

Setelah objek berhasil digeser, langkah kedua adalah mencerminkan posisi titik baru tersebut terhadap sumbu $Y$. Operasi pencerminan sumbu $Y$ akan membalikkan tanda nilai koordinat $x$ menjadi negatif, sementara nilai koordinat $y$ tetap konstan:

$$R(x,y) = (-x, y)$$

Representasi matriks homogen untuk operator refleksi sumbu $Y$ adalah:

$$R = \begin{bmatrix} -1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}$$

**Hasil Pemetaan Akhir Pasca Refleksi (Dari Posisi Step 1):**

- $A_1(2,1) \rightarrow A'(-2,1)$
- $B_1(4,1) \rightarrow B'(-4,1)$
- $C_1(4,3) \rightarrow C'(-4,3)$
- $D_1(2,3) \rightarrow D'(-2,3)$

---

## 4. Komposisi Matriks Transformasi Gabungan

[Image of geometric transformation composition matrix multiplication]

Sesuai aturan aljabar linear, urutan operasi transformasi komposit dibaca dari arah kanan ke kiri. Karena objek dikenai operasi translasi ($T$) terlebih dahulu baru kemudian operasi refleksi ($R$), maka persamaan transformasinya ditulis sebagai:

$$P' = R \cdot T \cdot P$$

Kita dapat menyatukan kedua matriks operator $3 \times 3$ tersebut menjadi satu matriks gabungan tunggal melalui operasi perkalian matriks (_dot product_):

$$R \cdot T = \begin{bmatrix} -1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix} \begin{bmatrix} 1 & 0 & 1 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix} = \begin{bmatrix} -1 & 0 & -1 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}$$

Melalui matriks gabungan $R \cdot T$ di atas, rumus pemetaan koordinat akhir untuk sembarang titik dapat langsung diperoleh secara ringkas lewat satu kali operasi:

$$\begin{bmatrix} x' \\ y' \\ 1 \end{bmatrix} = \begin{bmatrix} -1 & 0 & -1 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix} \begin{bmatrix} x \\ y \\ 1 \end{bmatrix} = \begin{bmatrix} -(x + 1) \\ y \\ 1 \end{bmatrix}$$

---

## 5. Proses Iterasi Berulang (Loop Animasi Sistem)

Di dalam program utama, transformasi komposit ini dijalankan secara berulang di dalam struktur _looping_ sebanyak **6 kali langkah**. Pola pergerakan spasial untuk setiap langkah ke-$n$ mematuhi skema formulasi berikut:

$$(x, y) \rightarrow (x + n, y) \rightarrow (-(x + n), y)$$

### Contoh Perkembangan Titik $A(1,1)$ Sepanjang Iterasi:

- **Step 0 (Kondisi Awal):** $A(1,1)$
- **Step 1:** Translasi $\rightarrow (2,1) \quad \rightarrow$ Refleksi $\rightarrow (-2,1)$
- **Step 2:** Translasi $\rightarrow (3,1) \quad \rightarrow$ Refleksi $\rightarrow (-3,1)$
- **Step 3:** Translasi $\rightarrow (4,1) \quad \rightarrow$ Refleksi $\rightarrow (-4,1)$
- _(Dan berlanjut secara konstan hingga menyentuh Step 6)_

---

## 6. Kode Implementasi Python (Simulator Animasi Transformasi)

Berikut adalah kode Python menggunakan pustaka `Matplotlib` dan `NumPy` untuk memvisualisasikan perubahan pergerakan posisi persegi hasil gabungan translasi dan refleksi sumbu Y secara bertahap:

```python
import numpy as np
import matplotlib.pyplot as plt

# 1. Definisi Koordinat Empat Titik Persegi Awal (Homogen: x, y, 1)
P = np.array([
    [1, 3, 3, 1, 1], # Baris X (ditutup kembali ke titik awal agar membentuk kotak)
    [1, 1, 3, 3, 1], # Baris Y
```