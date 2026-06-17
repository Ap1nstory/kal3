# elemminasi gauss

# C. Studi Kasus Kompleks Eliminasi Gaussian SPL 5x5

Pada materi ini, kita akan menyelesaikan sebuah Sistem Persamaan Linear (SPL) berukuran $5 \times 5$ menggunakan metode Eliminasi Gaussian. Fokus utama dari bab ini adalah memahami bagaimana Operasi Baris Elementer (OBE) bekerja secara bertahap untuk menyederhanakan matriks augmented hingga membentuk matriks identitas agar solusi variabelnya langsung dapat diketahui.

---

## Representasi Sistem Persamaan Linear dan Matriks Augmented

Berikut adalah struktur model matematika dari SPL lima variabel yang menjadi objek kajian kita:

$$x_1 + x_2 + x_3 + x_4 + x_5 = 1$$
$$x_2 + x_3 + x_4 + x_5 = 2$$
$$x_3 + x_4 + x_5 = 3$$
$$x_4 + x_5 = 4$$
$$x_5 = 5$$

Untuk mempermudah proses komputasi, koefisien variabel beserta konstanta di ruas kanan kita formulasikan ke dalam bentuk matriks augmented $[A|B]$ awal sebagai berikut:

$$
\left[ \begin{array}{ccccc|c}
1 & 1 & 1 & 1 & 1 & 1 \\
0 & 1 & 1 & 1 & 1 & 2 \\
0 & 0 & 1 & 1 & 1 & 3 \\
0 & 0 & 0 & 1 & 1 & 4 \\
0 & 0 & 0 & 0 & 1 & 5
\end{array} \right]
$$

---

## Proses Transformasi Operasi Baris Elementer (OBE)

Tujuan dari algoritma ini adalah mentransformasikan matriks di atas menjadi bentuk eselon baris terreduksi. Kita akan mengeksekusi reduksi elemen kolom secara bertahap berdasarkan posisi pivot utama.

### Tahap 1: Analisis Pivot Kolom Pertama

Pada baris pertama kolom pertama, kita sudah mendapatkan nilai pivot bernilai 1. Jika kita perhatikan elemen di bawah baris pertama pada kolom ini, seluruhnya sudah bernilai 0.

- **Evaluasi:** Tidak diperlukan operasi baris tambahan untuk kolom pertama. Matriks tetap dalam kondisi awal dan kita bisa langsung melangkah ke target pivot berikutnya.

### Tahap 2: Eliminasi Elemen Kolom Kelima

Kita jadikan elemen pada baris kelima kolom kelima (angka 1) sebagai basis pivot. Target kita adalah mengeliminasi atau menolkan semua nilai 1 yang berada di atas baris kelima pada kolom tersebut.

- **Operasi OBE:** $$R_1 \leftarrow R_1 - R_5$$
  $$R_2 \leftarrow R_2 - R_5$$
  $$R_3 \leftarrow R_3 - R_5$$
  $$R_4 \leftarrow R_4 - R_5$$

Hasil matriks setelah reduksi kolom kelima:

$$
\left[ \begin{array}{ccccc|c}
1 & 1 & 1 & 1 & 0 & -4 \\
0 & 1 & 1 & 1 & 0 & -3 \\
0 & 0 & 1 & 1 & 0 & -2 \\
0 & 0 & 0 & 1 & 0 & -1 \\
0 & 0 & 0 & 0 & 1 & 5
\end{array} \right]
$$

### Tahap 3: Eliminasi Elemen Kolom Keempat

Selanjutnya, kita bergerak ke pivot baris keempat kolom keempat. Kita bersihkan elemen-elemen bernilai 1 yang berada di atas baris keempat pada kolom ini.

- **Operasi OBE:**
  $$R_1 \leftarrow R_1 - R_4$$
  $$R_2 \leftarrow R_2 - R_4$$
  $$R_3 \leftarrow R_3 - R_4$$

Hasil matriks setelah reduksi kolom keempat:

$$
\left[ \begin{array}{ccccc|c}
1 & 1 & 1 & 0 & 0 & -3 \\
0 & 1 & 1 & 0 & 0 & -2 \\
0 & 0 & 1 & 0 & 0 & -1 \\
0 & 0 & 0 & 1 & 0 & -1 \\
0 & 0 & 0 & 0 & 1 & 5
\end{array} \right]
$$

### Tahap 4: Eliminasi Elemen Kolom Ketiga

Dengan cara yang sama, kita gunakan elemen diagonal pada baris ketiga kolom ketiga sebagai acuan untuk menolkan nilai di atasnya.

- **Operasi OBE:**
  $$R_1 \leftarrow R_1 - R_3$$
  $$R_2 \leftarrow R_2 - R_3$$

Hasil matriks setelah reduksi kolom ketiga:

$$
\left[ \begin{array}{ccccc|c}
1 & 1 & 0 & 0 & 0 & -2 \\
0 & 1 & 0 & 0 & 0 & -1 \\
0 & 0 & 1 & 0 & 0 & -1 \\
0 & 0 & 0 & 1 & 0 & -1 \\
0 & 0 & 0 & 0 & 1 & 5
\end{array} \right]
$$

### Tahap 5: Penyelesaian Akhir Kolom Kedua

Langkah terakhir dari rangkaian OBE ini adalah membersihkan elemen di atas pivot baris kedua kolom kedua. Kita hilangkan angka 1 pada baris pertama menggunakan basis baris kedua.

- **Operasi OBE:**
  $$R_1 \leftarrow R_1 - R_2$$

Hasil transformasi final matriks menjadi matriks identitas sempurna:

$$
\left[ \begin{array}{ccccc|c}
1 & 0 & 0 & 0 & 0 & -1 \\
0 & 1 & 0 & 0 & 0 & -1 \\
0 & 0 & 1 & 0 & 0 & -1 \\
0 & 0 & 0 & 1 & 0 & -1 \\
0 & 0 & 0 & 0 & 1 & 5
\end{array} \right]
$$

---

## Kesimpulan Himpunan Penyelesaian

Karena matriks koefisien di sebelah kiri telah berhasil dikonversi penuh menjadi matriks identitas, kita dapat langsung membaca nilai kebenaran dari masing-masing variabel sistem persamaan linear ini tanpa perlu substitusi balik lagi:

$$x_1 = -1$$
$$x_2 = -1$$
$$x_3 = -1$$
$$x_4 = -1$$
$$x_5 = 5$$

---

## Validasi Logika Menggunakan Kode Python (NumPy)

Untuk membuktikan validitas langkah OBE di atas, skrip Python berikut mengeksekusi pencarian solusi nilai variabel secara otomatis:

```python
import numpy as np

# Menyusun matriks koefisien A sesuai kasus dari dosen
A = np.array([[1, 1, 1, 1, 1],
              [0, 1, 1, 1, 1],
              [0, 0, 1, 1, 1],
              [0, 0, 0, 1, 1],
              [0, 0, 0, 0, 1]])

# Menyusun vektor hasil B
B = np.array([1, 2, 3, 4, 5])

# Menghitung solusi linear dengan numpy
solusi_komputer = np.linalg.solve(A, B)

print("--- VERIFIKASI SELESAI ---")
print("Hasil perhitungan variabel oleh sistem:")
for i, nilai in enumerate(solusi_komputer, 1):
    print(f"Nilai x_{i} = {nilai:.1f}")
```

berikut link collabnya

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1uPb1PyOSqKcS16Ciw7tivTeDDer29JCa?usp=sharing)