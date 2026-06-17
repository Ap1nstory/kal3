# Studi Kasus UTS - Analisis Determinan, Adjoin, dan Invers Matriks Orde 5x5

Pada bab ini, kita akan membahas secara komprehensif penyelesaian matematis dan implementasi komputasi untuk mencari nilai determinan, matriks adjoin, serta invers dari matriks berorde $5 \times 5$. Studi kasus ini memadukan dua pendekatan utama: metode analitis kofaktor untuk matriks simbolik dan metode numerik Eliminasi Gauss-Jordan untuk matriks terstruktur.

---

## 1. Fondasi Teoretis Matriks Orde 5x5

### A. Representasi Matriks Simbolik

Misalkan kita memiliki sebuah matriks persegi $A$ berdimensi $5 \times 5$ dengan elemen-elemen variabel sebagai berikut:

$$A = \begin{bmatrix} a & b & c & d & e \\ f & g & h & i & j \\ k & l & m & n & o \\ p & q & r & s & t \\ u & v & w & x & y \end{bmatrix}$$

### B. Rumus Determinan Ekspansi Kofaktor

Untuk menghitung determinan matriks di atas secara analitis, kita dapat menerapkan metode **Ekspansi Kofaktor** sepanjang baris pertama:

$$\det(A) = aC_{11} - bC_{12} + cC_{13} - dC_{14} + eC_{15}$$

Di mana nilai kofaktor $C_{ij}$ didefinisikan berdasarkan tanda minornya:
$$C_{ij} = (-1)^{i+j} \cdot M_{ij}$$

_Catatan: $M_{ij}$ merupakan determinan sub-matriks berukuran $4 \times 4$ yang diperoleh dengan cara menghapus baris ke-$i$ dan kolom ke-$j$ pada matriks utama.\_

### C. Matriks Adjoin ($\text{adj}(A)$)

Matriks adjoin diperoleh dengan melakukan operasi transpos (_transpose_) terhadap matriks kofaktor yang dihasilkan dari seluruh elemen matriks $A$:

$$\text{adj}(A) = \begin{bmatrix} C_{11} & C_{21} & C_{31} & C_{41} & C_{51} \\ C_{12} & C_{22} & C_{32} & C_{42} & C_{52} \\ C_{13} & C_{23} & C_{33} & C_{43} & C_{53} \\ C_{14} & C_{24} & C_{34} & C_{44} & C_{54} \\ C_{15} & C_{25} & C_{35} & C_{45} & C_{55} \end{bmatrix}$$

### D. Formulasi Invers Matriks & Syarat Eksistensi

Hubungan antara nilai determinan, matriks adjoin, dan invers matriks dirumuskan melalui persamaan:

$$A^{-1} = \frac{1}{\det(A)} \cdot \text{adj}(A)$$

**Syarat Mutlak Eksistensi Invers:**

- Jika $\det(A) \neq 0$, maka matriks $A$ disebut sebagai **Matriks Non-Singular** dan dipastikan memiliki invers.
- Jika $\det(A) = 0$, maka matriks $A$ disebut sebagai **Matriks Singular** dan tidak memiliki invers karena pembagian dengan angka nol tidak terdefinisi.

---

## 2. Studi Kasus Numerik Matriks Segitiga Bawah

Mari kita uji teori di atas menggunakan sebuah contoh kasus matriks segitiga bawah (_lower triangular matrix_) terstruktur berikut:

$$A = \begin{bmatrix} 1 & 0 & 0 & 0 & 0 \\ 2 & 1 & 0 & 0 & 0 \\ 0 & 3 & 1 & 0 & 0 \\ 0 & 0 & 4 & 1 & 0 \\ 0 & 0 & 0 & 5 & 1 \end{bmatrix}$$

### A. Perhitungan Nilai Determinan Eksplisit

Berdasarkan teorema aljabar linear, nilai determinan dari sebuah matriks yang berbentuk segitiga bawah (atau segitiga atas) cukup dihitung dengan melakukan **operasi perkalian seluruh elemen pada diagonal utamanya**:

$$\det(A) = a_{11} \cdot a_{22} \cdot a_{33} \cdot a_{44} \cdot a_{55}$$
$$\det(A) = 1 \cdot 1 \cdot 1 \cdot 1 \cdot 1 = 1$$

---

## 3. Ekstraksi Invers Menggunakan Eliminasi Gauss-Jordan

Untuk mencari matriks invers secara numerik, kita menggabungkan matriks $A$ dengan matriks identitas $I$ berorde $5 \times 5$ ke dalam struktur matriks augmentasi $[A \mid I]$:

$$\left[ \begin{array}{ccccc|ccccc} 1 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\ 2 & 1 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\ 0 & 3 & 1 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\ 0 & 0 & 4 & 1 & 0 & 0 & 0 & 0 & 1 & 0 \\ 0 & 0 & 0 & 5 & 1 & 0 & 0 & 0 & 0 & 1 \end{array} \right]$$

Berikut adalah visualisasi langkah demi langkah Operasi Baris Elementer (OBE) untuk mengubah sisi kiri menjadi matriks identitas:

### Langkah 1: Reduksi Elemen di Bawah Pivot Kolom 1

Gunakan operasi baris $R_2 \leftarrow R_2 - 2R_1$:
$$\left[ \begin{array}{ccccc|ccccc} 1 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 & 0 & -2 & 1 & 0 & 0 & 0 \\ 0 & 3 & 1 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\ 0 & 0 & 4 & 1 & 0 & 0 & 0 & 0 & 1 & 0 \\ 0 & 0 & 0 & 5 & 1 & 0 & 0 & 0 & 0 & 1 \end{array} \right]$$

### Langkah 2: Reduksi Elemen di Bawah Pivot Kolom 2

Gunakan operasi baris $R_3 \leftarrow R_3 - 3R_2$:
$$\left[ \begin{array}{ccccc|ccccc} 1 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 & 0 & -2 & 1 & 0 & 0 & 0 \\ 0 & 0 & 1 & 0 & 0 & 6 & -3 & 1 & 0 & 0 \\ 0 & 0 & 4 & 1 & 0 & 0 & 0 & 0 & 1 & 0 \\ 0 & 0 & 0 & 5 & 1 & 0 & 0 & 0 & 0 & 1 \end{array} \right]$$

### Langkah 3: Reduksi Elemen di Bawah Pivot Kolom 3

Gunakan operasi baris $R_4 \leftarrow R_4 - 4R_3$:
$$\left[ \begin{array}{ccccc|ccccc} 1 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 & 0 & -2 & 1 & 0 & 0 & 0 \\ 0 & 0 & 1 & 0 & 0 & 6 & -3 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1 & 0 & -24 & 12 & -4 & 1 & 0 \\ 0 & 0 & 0 & 5 & 1 & 0 & 0 & 0 & 0 & 1 \end{array} \right]$$

### Langkah 4: Reduksi Elemen di Bawah Pivot Kolom 4

Gunakan operasi baris $R_5 \leftarrow R_5 - 5R_4$:
$$\left[ \begin{array}{ccccc|ccccc} 1 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 & 0 & -2 & 1 & 0 & 0 & 0 \\ 0 & 0 & 1 & 0 & 0 & 6 & -3 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1 & 0 & -24 & 12 & -4 & 1 & 0 \\ 0 & 0 & 0 & 0 & 1 & 120 & -60 & 20 & -5 & 1 \end{array} \right]$$

---

## 4. Kesimpulan Hasil Akhir Perhitungan

Karena sisi kiri matriks augmentasi telah berhasil diubah menjadi bentuk matriks identitas sempurna ($I$), maka sisi sebelah kanan secara otomatis bertindak sebagai komponen matriks invers ($A^{-1}$):

### A. Matriks Invers ($A^{-1}$)

$$A^{-1} = \begin{bmatrix} 1 & 0 & 0 & 0 & 0 \\ -2 & 1 & 0 & 0 & 0 \\ 6 & -3 & 1 & 0 & 0 \\ -24 & 12 & -4 & 1 & 0 \\ 120 & -60 & 20 & -5 & 1 \end{bmatrix}$$

### B. Matriks Adjoin ($\text{adj}(A)$)

Memanfaatkan hubungan dasar aljabar $\text{adj}(A) = \det(A) \cdot A^{-1}$, dan berhubung nilai konstatanta $\det(A) = 1$, maka susunan matriks adjoin berharga sama persis dengan matriks inversnya:
$$\text{adj}(A) = A^{-1} = \begin{bmatrix} 1 & 0 & 0 & 0 & 0 \\ -2 & 1 & 0 & 0 & 0 \\ 6 & -3 & 1 & 0 & 0 \\ -24 & 12 & -4 & 1 & 0 \\ 120 & -60 & 20 & -5 & 1 \end{bmatrix}$$

---

## 5. Kode Program Python (Verifikasi Komputasi)

Di bawah ini adalah kode pemrograman Python menggunakan pustaka NumPy untuk membuktikan keakuratan hitungan manual di atas secara digital:

```python
import numpy as np

# 1. Definisi Matriks Segitiga Bawah sesuai soal UTS
A = np.array([
    [1, 0, 0, 0, 0],
    [2, 1, 0, 0, 0],
    [0, 3, 1, 0, 0],
    [0, 0, 4, 1, 0],
    [0, 0, 0, 5, 1]
], dtype=float)

print("="*60)
# Perhitungan nilai determinan sistem
det_A = np.linalg.det(A)

# Perhitungan invers matriks
inv_A = np.linalg.inv(A)

# Perhitungan matriks adjoin
adj_A = det_A * inv_A

# Tampilkan hasil running program
print("VERIFIKASI OUTPUT NUMERIK PROGRAM UTS:")
print("="*60)
print(f"1. Nilai Determinan Matriks : {det_A:.1f}\n")
print(f"2. Matriks Invers (A^-1) :\n{np.round(inv_A, 1)}\n")
print(f"3. Matriks Adjoin (adj A) :\n{np.round(adj_A, 1)}")
print("="*60)
```