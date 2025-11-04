# Laporan Praktikum Kriptografi
Minggu ke-: 3  
Topik: Modular Math 
Nama: Akmal Wicaksono 
NIM: 230202729
Kelas: 5IKRB

---

## 1. Tujuan
1. Menyelesaikan operasi aritmetika modular.
2. Menentukan bilangan prima dan menghitung GCD (Greatest Common Divisor).
3. Menerapkan logaritma diskrit sederhana dalam simulasi kriptografi

---

## 2. Dasar Teori
Modular aritmetika merupakan sistem operasi perhitungan yang berfokus pada sisa hasil pembagian terhadap suatu bilangan tertentu yang disebut modulus. Dua bilangan dikatakan kongruen apabila keduanya memiliki sisa pembagian yang sama terhadap modulus tertentu, misalnya 
17≡5(mod12). Konsep ini sering diterapkan dalam bidang kriptografi serta berbagai algoritma komputasi.

GCD (Greatest Common Divisor) atau FPB (Faktor Persekutuan Terbesar) adalah bilangan terbesar yang dapat membagi dua bilangan tanpa menyisakan hasil bagi. Nilai GCD biasanya ditentukan menggunakan algoritma Euclid yang bekerja dengan mengulangi proses pembagian hingga diperoleh sisa nol.

Bilangan prima sendiri adalah bilangan yang hanya dapat dibagi oleh 1 dan dirinya sendiri, seperti 2, 3, 5, 7, dan 11. Bilangan ini memiliki peran penting dalam dunia keamanan data karena digunakan dalam berbagai algoritma kriptografi, seperti RSA, berkat sifatnya yang sulit diuraikan menjadi faktor-faktor lain. Sementara itu, logaritma diskrit merupakan kebalikan dari operasi perpangkatan pada sistem modulo, yaitu mencari nilai eksponen 𝑥 yang memenuhi ax ≡b(modp). Proses ini sangat kompleks untuk bilangan besar, sehingga menjadi dasar dari keamanan sistem kriptografi modern seperti Diffie–Hellman dan ElGamal.

Secara keseluruhan, keempat konsep tersebut—modular aritmetika, GCD, bilangan prima, dan logaritma diskrit—merupakan fondasi utama dalam teori bilangan yang banyak dimanfaatkan di bidang komputasi, enkripsi, serta perlindungan informasi digital.

---

## 3. Alat dan Bahan
(- Python 3.x  
- Visual Studio Code / editor lain  
- Git dan akun GitHub  
- Library tambahan (misalnya pycryptodome, jika diperlukan)  )

---

## 4. Langkah Percobaan

1. Perhitungan modular arithmetic & GCD menggunakan Python.
2. Identifikasi bilangan prima dan penerapan algoritma Euclidean.
3. Simulasi sederhana logaritma diskrit.
4. Commit kode perhitungan ke repositori dengan format week3-modmath-gcd.
---

## 5. Source Code
(Salin kode program utama yang dibuat atau dimodifikasi.  
Gunakan blok kode:

def mod_add(a, b, n): return (a + b) % n
def mod_sub(a, b, n): return (a - b) % n
def mod_mul(a, b, n): return (a * b) % n
def mod_exp(base, exp, n): return pow(base, exp, n)  # eksponensiasi modular

print("7 + 5 mod 12 =", mod_add(7, 5, 12))
print("7 * 5 mod 12 =", mod_mul(7, 5, 12))
print("7^128 mod 13 =", mod_exp(7, 128, 13))
def gcd(a, b):
    while b != 0:
        a, b = b, a % b
    return a

print("gcd(54, 24) =", gcd(54, 24))
def egcd(a, b):
    if a == 0:
        return b, 0, 1
    g, x1, y1 = egcd(b % a, a)
    return g, y1 - (b // a) * x1, x1

def modinv(a, n):
    g, x, _ = egcd(a, n)
    if g != 1:
        return None
    return x % n

print("Invers 3 mod 11 =", modinv(3, 11))  # hasil: 4
def discrete_log(a, b, n):
    for x in range(n):
        if pow(a, x, n) == b:
            return x
    return None

print("3^x ≡ 4 (mod 7), x =", discrete_log(3, 4, 7))  # hasil: 4
```
)

---

## 6. Hasil dan Pembahasan
(- Lampirkan screenshot hasil eksekusi program (taruh di folder `screenshots/`).  
- Berikan tabel atau ringkasan hasil uji jika diperlukan.  
- Jelaskan apakah hasil sesuai ekspektasi.  
- Bahas error (jika ada) dan solusinya. 

Hasil eksekusi program Caesar Cipher:

![Hasil Eksekusi](screenshots/output.png)
![Hasil Input](screenshots/input.png)
![Hasil Output](screenshots/output.png)
)

---

## 7. Jawaban Pertanyaan
(Jawab pertanyaan diskusi yang diberikan pada modul.  
- Pertanyaan 1: Apa peran aritmetika modular dalam kriptografi modern?
  Aritmetika modular menjadi dasar bagi hampir semua algoritma kriptografi modern. Operasi seperti penjumlahan, perkalian, dan              perpangkatan dilakukan dalam ruang bilangan yang terbatas (modulus). Hal ini menjaga hasil agar tetap dalam rentang tertentu dan          memungkinkan keamanan algoritma, seperti pada RSA, Diffie-Hellman, dan ECC. Sifat kesulitan membalik operasi modular inilah yang          membuat kriptografi aman.
  
- Pertanyaan 2: Mengapa invers modular penting dalam algoritma kunci publik (misalnya RSA)?
  Invers modular digunakan untuk menemukan kunci privat dari kunci publik. Dalam RSA, jika diketahui eksponen publik 
  𝑒 dan fungsi totient aka kunci privat 𝑑adalah invers modular dari 𝑒 terhadap 𝜑(𝑛)φ(n), yaitu: e×d≡1 (mod φ(n))Tanpa invers modular,      kita tidak bisa membalik proses enkripsi menjadi dekripsi, sehingga komunikasi tidak dapat diamankan.

- Pertanyaan 3: Apa tantangan utama dalam menyelesaikan logaritma diskrit untuk modulus besar?
  Tantangan utamanya adalah kompleksitas komputasi yang sangat tinggi. Tidak ada algoritma efisien yang diketahui untuk menghitung          logaritma diskrit pada modulus besar. Waktu komputasi tumbuh secara eksponensial terhadap ukuran kunci, sehingga hampir mustahil          diselesaikan dalam waktu wajar. Kesulitan inilah yang dimanfaatkan untuk keamanan sistem seperti Diffie-Hellman dan ElGamal.
---

## 8. Kesimpulan
Melalui praktikum ini, mahasiswa memahami penerapan aritmetika modular, bilangan prima, dan perhitungan GCD menggunakan Python, serta penerapan logaritma diskrit sederhana dalam simulasi kriptografi sebagai dasar konsep keamanan data.

---

## 9. Daftar Pustaka
(Cantumkan referensi yang digunakan.  
Contoh:  
- Katz, J., & Lindell, Y. *Introduction to Modern Cryptography*.  
- Stallings, W. *Cryptography and Network Security*.  )

---

## 10. Commit Log
(Tuliskan bukti commit Git yang relevan.  
Contoh:
```
commit update laporan md-week3
Author: Akmal Wicaksono akmalwicaksono2704@gmail.com
Date:   2025-11-04

    week3-modmath: Modular Math  
```
