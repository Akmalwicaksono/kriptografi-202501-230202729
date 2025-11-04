# Laporan Praktikum Kriptografi
Minggu ke-: 4
Topik: Entropy & Unicity Distance 
Nama: Akmal Wicaksono
NIM: 230202729 
Kelas: 5IKRB  

---

## 1. Tujuan
1. Menyelesaikan perhitungan sederhana terkait entropi kunci.
2. Menggunakan teorema Euler pada contoh perhitungan modular & invers.
3. Menghitung unicity distance untuk ciphertext tertentu.
4. Menganalisis kekuatan kunci berdasarkan entropi dan unicity distance.
5. Mengevaluasi potensi serangan brute force pada kriptosistem sederhana.

---

## 2. Dasar Teori
Entropy adalah ukuran tingkat ketidakpastian atau acaknya suatu sistem kriptografi. Semakin tinggi nilai entropi, semakin sulit menebak kunci karena kemungkinan kombinasi kunci semakin banyak. Entropi dinyatakan dalam satuan bit, dan dihitung menggunakan rumus: H=log2​(N)
di mana 𝑁dalah jumlah kemungkinan kunci.

Unicity Distance adalah ukuran jumlah minimal data (ciphertext) yang dibutuhkan agar penyerang dapat menentukan kunci secara unik. Semakin besar unicity distance, semakin aman suatu sistem, karena dibutuhkan lebih banyak ciphertext untuk menemukan kuncinya.

Sementara itu, Brute Force Attack adalah metode untuk memecahkan sandi dengan mencoba semua kemungkinan kunci. Waktu yang dibutuhkan untuk serangan brute force bergantung pada panjang kunci dan nilai entropinya. Oleh karena itu, sistem kriptografi yang baik memiliki entropi tinggi dan unicity distance yang besar untuk mencegah keberhasilan serangan brute force.

---

## 3. Alat dan Bahan
(- Python 3.x  
- Visual Studio Code / editor lain  
- Git dan akun GitHub  
- Library tambahan (misalnya pycryptodome, jika diperlukan)  )

---

## 4. Langkah Percobaan
(Tuliskan langkah yang dilakukan sesuai instruksi.  
Contoh format:
1. Membuat file `caesar_cipher.py` di folder `praktikum/week2-cryptosystem/src/`.
2. Menyalin kode program dari panduan praktikum.
3. Menjalankan program dengan perintah `python caesar_cipher.py`.)

---

## 5. Source Code
(Salin kode program utama yang dibuat atau dimodifikasi.  
Gunakan blok kode:


# contoh potongan kode
import math

def entropy(keyspace_size):
    return math.log2(keyspace_size)

print("Entropy ruang kunci 26 =", entropy(26), "bit")
print("Entropy ruang kunci 2^128 =", entropy(2**128), "bit")

import math

# Fungsi menghitung entropi ruang kunci
def entropy(A):
    return math.log2(A)

# Fungsi menghitung unicity distance
def unicity_distance(HK, R=0.75, A=26):
    return HK / (R * math.log2(A))

# Hitung entropi untuk Caesar Cipher (jumlah kunci = 26)
HK = entropy(26)

print("Entropy ruang kunci =", HK, "bit")
print("Unicity Distance untuk Caesar Cipher =", unicity_distance(HK))

def brute_force_time(keyspace_size, attempts_per_second=1e6):
    seconds = keyspace_size / attempts_per_second
    days = seconds / (3600*24)
    return days

print("Waktu brute force Caesar Cipher (26 kunci) =", brute_force_time(26), "hari")
print("Waktu brute force AES-128 =", brute_force_time(2**128), "hari")
)


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
- Pertanyaan 1: Apa arti dari nilai entropy dalam konteks kekuatan kunci?
  Nilai entropy menunjukkan tingkat keacakan atau ketidakpastian kunci. Semakin tinggi nilai entropi, semakin sulit kunci ditebak karena    kemungkinan kombinasi kunci semakin banyak, sehingga sistem kriptografi menjadi lebih kuat.
  
- Pertanyaan 2: Mengapa unicity distance penting dalam menentukan keamanan suatu cipher?
  Unicity distance menunjukkan jumlah minimal ciphertext yang dibutuhkan untuk menemukan kunci secara unik. Jika nilai ini besar, maka      dibutuhkan lebih banyak data untuk menebak kunci, sehingga cipher tersebut lebih aman dari serangan analisis kriptografi.
  
- Pertanyaan 3: Mengapa brute force masih menjadi ancaman meskipun algoritma sudah kuat?
  Karena brute force mencoba semua kemungkinan kunci tanpa perlu memahami algoritma. Jika kunci yang digunakan terlalu pendek atau sistem   tidak membatasi percobaan, maka penyerang tetap berpeluang menemukan kunci, terutama dengan peningkatan daya komputasi modern.
)
---

## 8. Kesimpulan
Berdasarkan percobaan, nilai entropi dan unicity distance pada Caesar Cipher menunjukkan bahwa algoritma ini memiliki tingkat keamanan yang sangat rendah. Hal ini karena ruang kuncinya kecil dan ciphertext yang sedikit saja sudah cukup untuk menemukan kunci unik. Dengan demikian, Caesar Cipher tidak aman untuk digunakan dalam sistem kriptografi modern.

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
commit update laporan.md-week4
Author: Akmal Wicaksono <email>
Date:   2025-11-05

   week4-entropy-unicity
```
