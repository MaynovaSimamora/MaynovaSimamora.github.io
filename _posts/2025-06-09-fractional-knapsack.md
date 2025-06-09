---
title: "Fractional Knapsack Problem"
date: 2025-06-09 08:00:00 +0800
categories: [DAA, Fractional Knapsack]
tags: [Knapsack, Greedy, C++]
---

# Fractional Knapsack Problem
## 🎯 Kelompok 2  

## 📌 Deskripsi Singkat  
Fractional Knapsack adalah variasi dari masalah knapsack di mana kita diperbolehkan mengambil sebagian dari item untuk memaksimalkan nilai total tanpa melebihi kapasitas tas.

## 🧠 Konsep Utama  
- Boleh mengambil fraksi dari item  
- Diselesaikan menggunakan **Greedy Algorithm**  
- Hitung rasio nilai/berat, urutkan secara menurun  
- Ambil sebanyak mungkin dari item dengan rasio tertinggi

## 🧑‍💻 Algoritma Greedy  
1. Hitung rasio nilai/berat tiap item  
2. Urutkan item berdasarkan rasio tersebut  
3. Ambil item hingga kapasitas penuh

## 📥 Input  
- Array berat dan nilai dari tiap item  
- Kapasitas tas

## 📤 Output  
- Total nilai maksimum yang bisa dimasukkan ke dalam tas

## 🧮 Contoh Soal  
Item:  
- Berat: [2, 3, 5, 7, 1, 4]  
- Nilai: [10, 5, 15, 7, 6, 18]  
Kapasitas: 15 kg

**Langkah Solusi**  
1. Hitung rasio nilai/berat  
2. Urutkan item  
3. Ambil item satu per satu hingga kapasitas habis

## 💻 Contoh Kode (C++)  

```cpp
#include <bits/stdc++.h>
using namespace std;

struct Item {
    int weight, value;
};

bool cmp(Item a, Item b) {
    double r1 = (double)a.value / a.weight;
    double r2 = (double)b.value / b.weight;
    return r1 > r2;
}

double fractionalKnapsack(int capacity, vector<Item>& items) {
    sort(items.begin(), items.end(), cmp);
    double totalValue = 0.0;

    for (auto item : items) {
        if (item.weight <= capacity) {
            capacity -= item.weight;
            totalValue += item.value;
        } else {
            totalValue += item.value * ((double)capacity / item.weight);
            break;
        }
    }
    return totalValue;
}

int main() {
    int capacity = 15;
    vector<Item> items = \{\{2, 10\}, \{3, 5\}, \{5, 15\}, \{7, 7\}, \{1, 6\}, \{4, 18\}\};
    cout << "Nilai Maksimum: " << fractionalKnapsack(capacity, items) << endl;
    return 0;
}
```

## 📚 Analisis Kompleksitas
Waktu : O(n log n) – karena pengurutan
Ruang : O(n)

## 🌟 Aplikasi Dunia Nyata
- Pengalokasian sumber daya terbatas
- Investasi dana
- Optimisasi bandwidth
- Penjadwalan tugas

## 💪 Kekuatan dan Keterbatasan
Kekuatan :
- Efisien
- Mudah diimplementasikan
- Menghasilkan solusi optimal

Keterbatasan :
- Tidak cocok untuk 0/1 Knapsack
- Tidak menjamin hasil optimal untuk semua jenis masalah

## 🏁 Kesimpulan
Diselesaikan dengan algoritma greedy yang menghitung rasio nilai/berat, menghasilkan solusi optimal dalam O(n log n). Sangat berguna dalam optimisasi sumber daya.

