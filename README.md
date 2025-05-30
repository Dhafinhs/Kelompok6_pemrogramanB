

# Kelompok 3

## Program: Penerapan Metode Brent untuk Menentukan Kecepatan Terminal pada Gerak Jatuh Bebas dengan Hambatan Udara

**Anggota Kelompok:**

- Ahmad Fariz Khairi (2306211370)
- Daffa Bagus Dhiananto (2306250756)
- Dhafin Hamizan Setiawan (2306267145)
- Dimas Ananda Sutiardi (2306250586)
- Rafi Naufal Aryaputra (2306250680)


## Deskripsi

Program ini mengimplementasikan metode Brent dalam bahasa C untuk mencari akar dari fungsi nonlinear \$ f(v) = mg - cv^2 \$, yang merepresentasikan keseimbangan gaya pada gerak jatuh bebas dengan hambatan udara. Akar dari fungsi ini merupakan kecepatan terminal, yaitu kecepatan saat gaya gravitasi dan gaya hambat udara seimbang. Program menerima parameter fisika nyata dan melakukan pencarian akar secara numerik dengan hasil yang cepat dan akurat[^2].

## Fitur

- Implementasi metode Brent untuk pencarian akar fungsi nonlinear
- Studi kasus: gerak jatuh bebas dengan hambatan udara
- Parameter fisika dapat dimodifikasi pada kode sumber


## Cara Menjalankan

1. **Kompilasi Program**

Gunakan compiler C seperti gcc:

```bash
gcc -o kecepatan_terminal TugasPemrogramanB.c -lm
```

2. **Jalankan Program**

```bash
./kecepatan_terminal
```

3. **Output**

Program akan menampilkan nilai kecepatan terminal yang ditemukan secara numerik.

## Struktur File

- `TugasPemrogramanB.c` — File utama program berisi implementasi metode Brent dan fungsi fisika terkait
- `README.md` — Dokumentasi dan petunjuk penggunaan
- `laporan_pemrogramanB.pdf` — Dokumentasi laporan


## Referensi

- [1] S. C. Chapra dan R. P. Canale, Numerical Methods for Engineers, Edisi ke-6, McGraw-Hill, 2010.
- [2] R. Nave, “Fluid Friction,” Gsu.edu, 2019. http://hyperphysics.phy-astr.gsu.edu/hbase/airfri2.html 
- [3]  “One Dimensional Root-Finding — GSL 2.8 documentation,” Gnu.org, 2024. https://www.gnu.org/software/gsl/doc/html/roots.html#brent-method  




---
