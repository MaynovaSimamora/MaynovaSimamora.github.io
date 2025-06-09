---
title: "N-Queens Problem"
date: 2025-06-09 08:00:00 +0800
categories: [DAA, N-Queens]
tags: [Backtracking, C++, Chess]
---

# N-Queens Problem
## 🎯 Kelompok 4  
 
## 📌 Deskripsi Singkat  
Penempatan N buah ratu di papan NxN sehingga tidak ada dua ratu saling menyerang (baris, kolom, diagonal).

## 🧠 Konsep Utama  
- Termasuk Constraint Satisfaction Problem  
- Diselesaikan dengan **Backtracking**

## 🧑‍💻 Algoritma Backtracking  
1. Tempatkan ratu di baris pertama  
2. Periksa apakah posisi aman  
3. Lanjut ke baris berikutnya  
4. Jika tidak ada posisi aman, mundur (backtrack)

## 📥 Input  
- Ukuran papan (N)  

## 📤 Output  
- Semua konfigurasi valid ratu  
- Jumlah total solusi

## 🧮 Contoh Masalah  
Untuk N=4, salah satu solusi:  
- Ratu di posisi (0,1), (1,3), (2,0), (3,2)

## 💻 Contoh Kode (C++)  

```cpp
#include <iostream>
#include <vector>
using namespace std;

bool isSafe(vector<vector<int>>& board, int row, int col, int N) {
    // Implementasi pengecekan aman
}

void solveNQueens(vector<vector<int>>& board, int row, int N, vector<vector<vector<int>>>& solutions) {
    // Rekursi dan backtracking
}
``` 

## 📚 Analisis Kompleksitas
Waktu : O(N!) – eksponensial
Ruang : O(N²)

## 🌟 Aplikasi Dunia Nyata
- Penjadwalan tugas
- Penempatan modul elektronik
- Alokasi sumber daya

## 💪 Kekuatan dan Keterbatasan
Kekuatan :
- Menyelesaikan CSP
- Pelatihan logika pemrograman

Keterbatasan :
- Kompleksitas sangat tinggi
- Tidak efisien untuk N besar

## 🏁 Kesimpulan
Masalah N-Queens adalah contoh klasik constraint satisfaction problem. Diselesaikan dengan backtracking dan digunakan untuk latihan algoritma pencarian.