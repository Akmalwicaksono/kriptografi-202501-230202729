# Laporan Praktikum Kriptografi
Minggu ke-: 2
Topik: cryptosystem
Nama: Akmal Wicaksono
NIM: 230202729 
Kelas: 5IKRA

---

## 1. Tujuan
Setelah mengikuti praktikum ini, mahasiswa diharapkan mampu:  
1. Mengidentifikasi komponen dasar kriptosistem (plaintext, ciphertext, kunci, algoritma).  
2. Menggambarkan proses enkripsi dan dekripsi sederhana.  
3. Mengklasifikasikan jenis kriptosistem (simetris dan asimetris).

---

## 2. Dasar Teori
Kriptografi adalah ilmu dan seni untuk mengamankan informasi dengan cara mengubah data asli (plaintext) menjadi bentuk tidak terbaca (ciphertext) menggunakan suatu algoritma dan kunci tertentu. Tujuannya adalah menjaga kerahasiaan, keaslian, serta integritas data dari pihak yang tidak berwenang. Dalam sejarahnya, kriptografi telah digunakan sejak zaman kuno untuk komunikasi rahasia, terutama dalam bidang militer dan diplomasi.

Cipher klasik merupakan bentuk awal dari sistem kriptografi yang menggunakan operasi sederhana seperti substitusi (penggantian huruf) dan transposisi (penyusunan ulang huruf). Contoh cipher klasik yang terkenal antara lain Caesar Cipher, yang mengenkripsi teks dengan menggeser setiap huruf sejauh beberapa posisi dalam alfabet, serta Vigenère Cipher, yang menggunakan kunci berupa kata untuk menentukan pola pergeseran yang berbeda pada setiap huruf.

Dalam kriptografi klasik, proses enkripsi dan dekripsi biasanya menggunakan aritmetika modular, yaitu operasi matematika yang dilakukan dengan sisa pembagian terhadap suatu bilangan modulus. Misalnya, pada Caesar Cipher digunakan operasi (x + k) mod 26 untuk mengenkripsi huruf, di mana x adalah nilai huruf dan k adalah kunci. Konsep modular ini penting karena memastikan hasil pergeseran tetap berada dalam rentang alfabet A–Z

---

## 3. Alat dan Bahan
(- Python 3.x  
- Visual Studio Code / editor lain  
- Git dan akun GitHub  
- Library tambahan (misalnya pycryptodome, jika diperlukan)  )

---

## 4. Langkah Percobaan
1. Membuka folder proyek praktikum di direktori praktikum/week2-cryptosystem/src/.

2. Membuat file baru dengan nama simple_crypto.py sebagai tempat menyimpan program enkripsi dan dekripsi.

3. Menyalin kode program dari panduan praktikum yang berisi fungsi encrypt() dan decrypt() untuk mengimplementasikan algoritma Caesar Cipher.

4. Menambahkan logika perulangan pada fungsi encrypt() dan decrypt() untuk memproses setiap karakter pada teks. Jika karakter berupa huruf, maka akan digeser        sesuai nilai kunci; jika bukan huruf, karakter dibiarkan tetap.

5. Menyimpan file simple_crypto.py dan menjalankan program menggunakan perintah:

    python simple_crypto.py

6. Memasukkan teks plaintext dan kunci (key) sesuai instruksi praktikum, kemudian mengamati hasil proses enkripsi (ciphertext) dan dekripsi (plaintext hasil balik).

7. Mencatat hasil keluaran program untuk membandingkan kesesuaian antara teks asli dan hasil dekripsi.

---

## 5. Source Code
(Salin kode program utama yang dibuat atau dimodifikasi.  
Gunakan blok kode:

```python
# file: praktikum/week2-cryptosystem/src/simple_crypto.py

def encrypt(plaintext, key):
    result = ""
    for char in plaintext:
        if char.isalpha():
            shift = 65 if char.isupper() else 97
            result += chr((ord(char) - shift + key) % 26 + shift)
        else:
            result += char
    return result

def decrypt(ciphertext, key):
    result = ""
    for char in ciphertext:
        if char.isalpha():
            shift = 65 if char.isupper() else 97
            result += chr((ord(char) - shift - key) % 26 + shift)
        else:
            result += char
    return result

if __name__ == "__main__":
    message = "Cryptosystem Test"
    key = 5

    enc = encrypt(message, key)
    dec = decrypt(enc, key)

    print("Plaintext :", message)
    print("Ciphertext:", enc)
    print("Decrypted :", dec)

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

- Pertanyaan 1:
Komponen utama dalam kriptosistem terdiri atas:

    - Plaintext – pesan asli yang ingin dilindungi.

    - Ciphertext – hasil dari proses enkripsi yang tidak dapat dibaca tanpa kunci.

    - Algoritma enkripsi – prosedur matematis yang mengubah plaintext menjadi ciphertext.

    - Algoritma dekripsi – prosedur untuk mengembalikan ciphertext menjadi plaintext.

    - Kunci (key) – nilai rahasia yang digunakan dalam proses enkripsi dan dekripsi agar hanya pihak tertentu yang dapat membaca pesan.
      
- Pertanyaan 2:
Kelebihan sistem simetris:
Proses enkripsi dan dekripsi lebih cepat karena algoritmanya sederhana.
Membutuhkan sumber daya komputasi yang lebih kecil.

Kelemahan sistem simetris:
Menggunakan satu kunci yang sama untuk enkripsi dan dekripsi, sehingga jika kunci bocor maka keamanan pesan hilang.
Distribusi kunci sulit dilakukan secara aman, terutama jika digunakan antara banyak pihak.

- Pertanyaan 3:

Distribusi kunci menjadi masalah utama karena pengirim dan penerima harus memiliki kunci yang sama sebelum komunikasi aman dapat dilakukan. Pengiriman kunci melalui saluran tidak aman berisiko disadap atau dicuri oleh pihak ketiga. Jika kunci berhasil diambil oleh pihak yang tidak berwenang, maka seluruh sistem keamanan akan gagal, karena kunci tersebut dapat digunakan untuk membuka semua pesan terenkripsi.
)
---

## 8. Kesimpulan
Dari percobaan yang dilakukan, dapat disimpulkan bahwa proses enkripsi dan dekripsi pada kriptografi klasik seperti Caesar Cipher menggunakan prinsip pergeseran huruf berdasarkan kunci tertentu. Sistem ini mampu menyembunyikan isi pesan sederhana, namun masih memiliki kelemahan dalam keamanan karena mudah dipecahkan dengan teknik brute force atau analisis frekuensi.

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
commit update laporan md - week2
Author: akmal Wicaksono akmalwicaksono2704@gmail.com
Date:   2025-10-21

    week2-cryptosystem: implementasi Caesar Cipher dan laporan )
```
