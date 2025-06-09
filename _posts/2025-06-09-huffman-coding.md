---
title: "Huffman Coding"
date: 2025-06-09 08:00:00 +0800
categories: [DAA, Huffman Coding]
tags: [Compression, Tree, Binary]
---

# Huffman Coding
## 🎯 Kelompok 3  

## 📌 Deskripsi Singkat  
Huffman coding adalah algoritma kompresi lossless berbasis frekuensi karakter. Karakter sering muncul → kode lebih pendek.

## 🧠 Konsep Utama  
- Berdasarkan frekuensi karakter  
- Buat pohon biner Huffman  
- Tentukan kode biner: kiri=0, kanan=1

## 🧑‍💻 Langkah-Langkah  
1. Hitung frekuensi tiap karakter  
2. Buat simpul untuk tiap karakter  
3. Gabung dua simpul dengan frekuensi terkecil  
4. Ulangi hingga tersisa satu pohon  
5. Tetapkan kode biner untuk tiap karakter

## 📥 Input  
- String atau data input  
- Frekuensi karakter

## 📤 Output  
- Data terkompresi  
- Tabel kode Huffman

## 🧮 Contoh Kasus  
Input: `"ABBCCCDDDD"`  
Frekuensi:  
- A: 1  
- B: 2  
- C: 3  
- D: 4  

**Hasil Kode**:  
- D = 0  
- C = 10  
- B = 110  
- A = 111  

**Output terkompresi**: `0 10 10 110 110 10 10 0 0 0`  
(Lebih pendek dari representasi asli)

## 💻 Contoh Kode (C++)  

```cpp
// Struktur pohon Huffman
struct Node {
    char ch;
    int freq;
    Node *left, *right;
};
```

## 📚 Analisis Kompleksitas
Waktu : O(n log n)
Ruang : O(n)

## 🌟 Aplikasi Dunia Nyata
1. ZIP
2. JPEG
3. MP3
4. Encoding teks

## 💪 Kekuatan dan Keterbatasan
Kekuatan :
- Lossless
- Efisien untuk distribusi tidak merata

Keterbatasan :
- Butuh tabel kode untuk dekompresi
- Kurang optimal jika frekuensi merata

## 🏁 Kesimpulan
Huffman coding adalah metode kompresi efektif yang menggantikan karakter dengan kode biner berdasarkan frekuensinya. Digunakan luas di sistem kompresi modern.