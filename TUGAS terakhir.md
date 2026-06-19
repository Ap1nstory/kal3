# Pembahasan Soal Determinan Matriks 3x3

Berikut adalah pembahasan lengkap untuk soal-soal determinan matriks $3 \times 3$ menggunakan dua metode: **Metode Sarrus** dan **Metode Ekspansi Baris Pertama (Kofaktor)**. 

---

## Soal 1
Hitung determinan dari matriks berikut:
$$A = \begin{bmatrix} 2 & 1 & 3 \\ 0 & 4 & 5 \\ 1 & 2 & 1 \end{bmatrix}$$

### Cara 1: Metode Sarrus
$$\det(A) = (2 \cdot 4 \cdot 1) + (1 \cdot 5 \cdot 1) + (3 \cdot 0 \cdot 2) - (3 \cdot 4 \cdot 1) - (2 \cdot 5 \cdot 2) - (1 \cdot 0 \cdot 1)$$
$$\det(A) = 8 + 5 + 0 - 12 - 20 - 0$$
$$\det(A) = 13 - 32$$
$$\det(A) = -19$$

### Cara 2: Ekspansi Baris Pertama
$$\det(A) = 2 \cdot \begin{vmatrix} 4 & 5 \\ 2 & 1 \end{vmatrix} - 1 \cdot \begin{vmatrix} 0 & 5 \\ 1 & 1 \end{vmatrix} + 3 \cdot \begin{vmatrix} 0 & 4 \\ 1 & 2 \end{vmatrix}$$
$$\det(A) = 2(4 - 10) - 1(0 - 5) + 3(0 - 4)$$
$$\det(A) = 2(-6) - 1(-5) + 3(-4)$$
$$\det(A) = -12 + 5 - 12$$
$$\det(A) = -19$$

**Jawaban:** Nilai determinan matriks $A$ adalah **$-19$**.

---

## Soal 2
Tentukan nilai determinan matriks:
$$B = \begin{bmatrix} 3 & 2 & 1 \\ 1 & 0 & 4 \\ 2 & 5 & 1 \end{bmatrix}$$

### Cara 1: Metode Sarrus
$$\det(B) = (3 \cdot 0 \cdot 1) + (2 \cdot 4 \cdot 2) + (1 \cdot 1 \cdot 5) - (1 \cdot 0 \cdot 2) - (3 \cdot 4 \cdot 5) - (2 \cdot 1 \cdot 1)$$
$$\det(B) = 0 + 16 + 5 - 0 - 60 - 2$$
$$\det(B) = 21 - 62$$
$$\det(B) = -41$$

### Cara 2: Ekspansi Baris Pertama
$$\det(B) = 3 \cdot \begin{vmatrix} 0 & 4 \\ 5 & 1 \end{vmatrix} - 2 \cdot \begin{vmatrix} 1 & 4 \\ 2 & 1 \end{vmatrix} + 1 \cdot \begin{vmatrix} 1 & 0 \\ 2 & 5 \end{vmatrix}$$
$$\det(B) = 3(0 - 20) - 2(1 - 8) + 1(5 - 0)$$
$$\det(B) = 3(-20) - 2(-7) + 1(5)$$
$$\det(B) = -60 + 14 + 5$$
$$\det(B) = -41$$

**Jawaban:** Nilai determinan matriks $B$ adalah **$-41$**.

---

## Soal 3
Jika
$$C = \begin{bmatrix} 1 & 2 & 3 \\ 2 & 4 & 6 \\ 1 & 1 & 1 \end{bmatrix}$$
tentukan $\det(C)$ dan jelaskan apakah matriks tersebut singular atau tidak.

### Cara 1: Metode Sarrus
$$\det(C) = (1 \cdot 4 \cdot 1) + (2 \cdot 6 \cdot 1) + (3 \cdot 2 \cdot 1) - (3 \cdot 4 \cdot 1) - (1 \cdot 6 \cdot 1) - (2 \cdot 2 \cdot 1)$$
$$\det(C) = 4 + 12 + 6 - 12 - 6 - 4$$
$$\det(C) = 22 - 22$$
$$\det(C) = 0$$

### Cara 2: Ekspansi Baris Pertama
$$\det(C) = 1 \cdot \begin{vmatrix} 4 & 6 \\ 1 & 1 \end{vmatrix} - 2 \cdot \begin{vmatrix} 2 & 6 \\ 1 & 1 \end{vmatrix} + 3 \cdot \begin{vmatrix} 2 & 4 \\ 1 & 1 \end{vmatrix}$$
$$\det(C) = 1(4 - 6) - 2(2 - 6) + 3(2 - 4)$$
$$\det(C) = 1(-2) - 2(-4) + 3(-2)$$
$$\det(C) = -2 + 8 - 6$$
$$\det(C) = 0$$

**Kesimpulan:**
Karena nilai $\det(C) = 0$, maka matriks $C$ adalah **matriks singular** (matriks yang tidak memiliki invers).

## B. Soal Dekomposisi Matriks (LU Decomposition)


## Soal 4
Lakukan dekomposisi LU terhadap matriks:
$$A = \begin{bmatrix} 2 & 4 & 2 \\ 1 & 5 & 2 \\ 1 & 2 & 4 \end{bmatrix}$$

**Langkah 1: Mencari matriks U (Segitiga Atas)**
Kita gunakan operasi baris dasar (Eliminasi Gauss) untuk membuat angka di bawah diagonal utama menjadi nol.

- **Bikin nol di baris 2 kolom 1:** Pengalinya adalah $m_{21} = \frac{1}{2}$.
  $R_2 \leftarrow R_2 - \frac{1}{2}R_1$
  $R_2 = [1, 5, 2] - [1, 2, 1] = [0, 3, 1]$

- **Bikin nol di baris 3 kolom 1:** Pengalinya adalah $m_{31} = \frac{1}{2}$.
  $R_3 \leftarrow R_3 - \frac{1}{2}R_1$
  $R_3 = [1, 2, 4] - [1, 2, 1] = [0, 0, 3]$

Matriks sementaranya jadi:
$$\begin{bmatrix} 2 & 4 & 2 \\ 0 & 3 & 1 \\ 0 & 0 & 3 \end{bmatrix}$$

- **Bikin nol di baris 3 kolom 2:** Karena angkanya sudah nol, pengalinya adalah $m_{32} = 0$.
  $R_3 \leftarrow R_3 - 0 R_2$
  Hasil baris 3 tetap $[0, 0, 3]$.

Jadi, matriks $U$-nya adalah:
$$U = \begin{bmatrix} 2 & 4 & 2 \\ 0 & 3 & 1 \\ 0 & 0 & 3 \end{bmatrix}$$

**Langkah 2: Membentuk matriks L (Segitiga Bawah)**
Matriks $L$ diisi dengan angka pengali ($m$) yang tadi kita pakai, dan diagonal utamanya adalah 1.
$$L = \begin{bmatrix} 1 & 0 & 0 \\ m_{21} & 1 & 0 \\ m_{31} & m_{32} & 1 \end{bmatrix} = \begin{bmatrix} 1 & 0 & 0 \\ \frac{1}{2} & 1 & 0 \\ \frac{1}{2} & 0 & 1 \end{bmatrix}$$

**Jawaban Akhir:**
$$A = LU$$
$$\begin{bmatrix} 2 & 4 & 2 \\ 1 & 5 & 2 \\ 1 & 2 & 4 \end{bmatrix} = \begin{bmatrix} 1 & 0 & 0 \\ \frac{1}{2} & 1 & 0 \\ \frac{1}{2} & 0 & 1 \end{bmatrix} \begin{bmatrix} 2 & 4 & 2 \\ 0 & 3 & 1 \\ 0 & 0 & 3 \end{bmatrix}$$

---

## Soal 5
Tentukan matriks $L$ dan $U$ dari:
$$B = \begin{bmatrix} 1 & 2 & 1 \\ 2 & 5 & 3 \\ 4 & 10 & 8 \end{bmatrix}$$

**Langkah 1: Mencari matriks U dengan Eliminasi Gauss**
- **Bikin nol di baris 2 kolom 1:** Pengalinya $m_{21} = \frac{2}{1} = 2$.
  $R_2 \leftarrow R_2 - 2R_1$
  $R_2 = [2, 5, 3] - [2, 4, 2] = [0, 1, 1]$

- **Bikin nol di baris 3 kolom 1:** Pengalinya $m_{31} = \frac{4}{1} = 4$.
  $R_3 \leftarrow R_3 - 4R_1$
  $R_3 = [4, 10, 8] - [4, 8, 4] = [0, 2, 4]$

Matriks sementaranya jadi:
$$\begin{bmatrix} 1 & 2 & 1 \\ 0 & 1 & 1 \\ 0 & 2 & 4 \end{bmatrix}$$

- **Bikin nol di baris 3 kolom 2:** Pengalinya $m_{32} = \frac{2}{1} = 2$.
  $R_3 \leftarrow R_3 - 2R_2$
  $R_3 = [0, 2, 4] - [0, 2, 2] = [0, 0, 2]$

Jadi, matriks $U$-nya adalah:
$$U = \begin{bmatrix} 1 & 2 & 1 \\ 0 & 1 & 1 \\ 0 & 0 & 2 \end{bmatrix}$$

**Langkah 2: Membentuk matriks L**
Masukkan pengali-pengali tadi ke matriks segitiga bawah:
$$L = \begin{bmatrix} 1 & 0 & 0 \\ m_{21} & 1 & 0 \\ m_{31} & m_{32} & 1 \end{bmatrix} = \begin{bmatrix} 1 & 0 & 0 \\ 2 & 1 & 0 \\ 4 & 2 & 1 \end{bmatrix}$$

**Jawaban Akhir:**
Matriks $L$ dan $U$ dari matriks $B$ adalah:
$$L = \begin{bmatrix} 1 & 0 & 0 \\ 2 & 1 & 0 \\ 4 & 2 & 1 \end{bmatrix}, \quad U = \begin{bmatrix} 1 & 2 & 1 \\ 0 & 1 & 1 \\ 0 & 0 & 2 \end{bmatrix}$$


## C. Soal Invers Matriks 3x3

Metode yang digunakan pada pembahasan ini adalah **Metode Adjoin**, dengan rumus umum:
$$A^{-1} = \frac{1}{\det(A)} \text{Adj}(A)$$
di mana $\text{Adj}(A)$ adalah transpose dari matriks kofaktor.

---

## Soal 7
Tentukan invers dari matriks:
$$A = \begin{bmatrix} 1 & 2 & 1 \\ 0 & 1 & 1 \\ 2 & 3 & 4 \end{bmatrix}$$

**Langkah 1: Cari Determinan**
Ekspansi baris pertama:
$$\det(A) = 1(4 - 3) - 2(0 - 2) + 1(0 - 2)$$
$$\det(A) = 1(1) - 2(-2) + 1(-2)$$
$$\det(A) = 1 + 4 - 2 = 3$$

**Langkah 2: Cari Matriks Kofaktor**
$$C = \begin{bmatrix} +(4-3) & -(0-2) & +(0-2) \\ -(8-3) & +(4-2) & -(3-4) \\ +(2-1) & -(1-0) & +(1-0) \end{bmatrix} = \begin{bmatrix} 1 & 2 & -2 \\ -5 & 2 & 1 \\ 1 & -1 & 1 \end{bmatrix}$$

**Langkah 3: Cari Adjoin (Transpose dari Kofaktor)**
$$\text{Adj}(A) = C^T = \begin{bmatrix} 1 & -5 & 1 \\ 2 & 2 & -1 \\ -2 & 1 & 1 \end{bmatrix}$$

**Langkah 4: Hitung Invers**
$$A^{-1} = \frac{1}{3} \begin{bmatrix} 1 & -5 & 1 \\ 2 & 2 & -1 \\ -2 & 1 & 1 \end{bmatrix} = \begin{bmatrix} \frac{1}{3} & -\frac{5}{3} & \frac{1}{3} \\ \frac{2}{3} & \frac{2}{3} & -\frac{1}{3} \\ -\frac{2}{3} & \frac{1}{3} & \frac{1}{3} \end{bmatrix}$$

---

## Soal 8
Carilah invers matriks:
$$B = \begin{bmatrix} 2 & 1 & 0 \\ 1 & 2 & 1 \\ 0 & 1 & 2 \end{bmatrix}$$

**Langkah 1: Cari Determinan**
Ekspansi baris pertama:
$$\det(B) = 2(4 - 1) - 1(2 - 0) + 0$$
$$\det(B) = 2(3) - 2 = 4$$

**Langkah 2: Cari Matriks Kofaktor**
$$C = \begin{bmatrix} +(4-1) & -(2-0) & +(1-0) \\ -(2-0) & +(4-0) & -(2-0) \\ +(1-0) & -(2-0) & +(4-1) \end{bmatrix} = \begin{bmatrix} 3 & -2 & 1 \\ -2 & 4 & -2 \\ 1 & -2 & 3 \end{bmatrix}$$

**Langkah 3: Cari Adjoin**
$$\text{Adj}(B) = C^T = \begin{bmatrix} 3 & -2 & 1 \\ -2 & 4 & -2 \\ 1 & -2 & 3 \end{bmatrix}$$

**Langkah 4: Hitung Invers**
$$B^{-1} = \frac{1}{4} \begin{bmatrix} 3 & -2 & 1 \\ -2 & 4 & -2 \\ 1 & -2 & 3 \end{bmatrix} = \begin{bmatrix} \frac{3}{4} & -\frac{1}{2} & \frac{1}{4} \\ -\frac{1}{2} & 1 & -\frac{1}{2} \\ \frac{1}{4} & -\frac{1}{2} & \frac{3}{4} \end{bmatrix}$$

---

## Soal 9
Diketahui:
$$C = \begin{bmatrix} 3 & 0 & 2 \\ 2 & 0 & -2 \\ 0 & 1 & 1 \end{bmatrix}$$
Tentukan $C^{-1}$.

**Langkah 1: Cari Determinan**
Biar gampang, pakai ekspansi kolom kedua (karena banyak nolnya):
$$\det(C) = -1 \cdot \begin{vmatrix} 3 & 2 \\ 2 & -2 \end{vmatrix}$$
$$\det(C) = -1(-6 - 4) = -1(-10) = 10$$

**Langkah 2: Cari Matriks Kofaktor**
$$K = \begin{bmatrix} +(0 - (-2)) & -(2 - 0) & +(2 - 0) \\ -(0 - 2) & +(3 - 0) & -(3 - 0) \\ +(0 - 0) & -(-6 - 4) & +(0 - 0) \end{bmatrix} = \begin{bmatrix} 2 & -2 & 2 \\ 2 & 3 & -3 \\ 0 & 10 & 0 \end{bmatrix}$$

**Langkah 3: Cari Adjoin**
$$\text{Adj}(C) = K^T = \begin{bmatrix} 2 & 2 & 0 \\ -2 & 3 & 10 \\ 2 & -3 & 0 \end{bmatrix}$$

**Langkah 4: Hitung Invers**
$$C^{-1} = \frac{1}{10} \begin{bmatrix} 2 & 2 & 0 \\ -2 & 3 & 10 \\ 2 & -3 & 0 \end{bmatrix} = \begin{bmatrix} \frac{1}{5} & \frac{1}{5} & 0 \\ -\frac{1}{5} & \frac{3}{10} & 1 \\ \frac{1}{5} & -\frac{3}{10} & 0 \end{bmatrix}$$