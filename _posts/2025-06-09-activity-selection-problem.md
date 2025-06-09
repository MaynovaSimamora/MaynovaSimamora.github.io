---
title: "Activity Selection Problem"
date: 2025-06-09 08:00:00 +0800
categories: [DAA, Activity Selection Problem]
tags: [Activity Selection, Greedy, C++]
---

# Activity Selection Problem
## 🎯 Kelompok 1    

## 📌 Deskripsi Singkat  
Masalah optimasi untuk memilih aktivitas sebanyak mungkin tanpa tumpang tindih. Diberikan waktu mulai dan selesai dari sekumpulan aktivitas, kita harus memilih subset terbesar dari aktivitas yang kompatibel.

## 🧠 Konsep Utama  
- Termasuk dalam kategori **Greedy Algorithm**
- Strategi: selalu pilih aktivitas yang selesai paling awal
- Cocok untuk masalah penjadwalan

## 🧑‍💻 Algoritma Greedy  
Algoritma greedy bekerja dengan membuat pilihan lokal optimal pada setiap langkah, berharap akan menghasilkan solusi global optimal. Pada kasus ini, pilih aktivitas dengan waktu selesai tercepat.

## 📥 Input  
- Dua array: waktu mulai dan waktu selesai dari setiap aktivitas

## 📤 Output  
- Indeks aktivitas yang dapat dipilih tanpa tumpang tindih

## 🧮 Langkah Penyelesaian  
1. Urutkan aktivitas berdasarkan waktu selesai  
2. Pilih aktivitas pertama  
3. Pilih aktivitas berikutnya hanya jika waktunya tidak bertabrakan

## 🧩 Contoh Soal  
**Aktivitas, Mulai (s), Selesai (f)**  
- A1, 1, 4  
- A2, 3, 5  
- A3, 0, 6  
- A4, 5, 7  
- A5, 8, 9  
- A6, 5, 9  

**Langkah Solusi**  
1. **Urutkan** berdasarkan waktu selesai: [A1, A2, A3, A4, A5, A6]  
2. **Pilih A1**  
3. **Iterasi:**  
   - A2, A3: Tumpang tindih  
   - A4: Kompatibel → {A1, A4}  
   - A5: Kompatibel → {A1, A4, A5}  
   - A6: Tumpang tindih  
**Solusi Optimal:** {A1, A4, A5}

## 💻 Contoh Kode (C++)  

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

struct Activity {
    int start, finish, index;
};

bool compare(Activity a, Activity b) {
    return a.finish < b.finish;
}

void activitySelection(vector<Activity>& activities) {
    sort(activities.begin(), activities.end(), compare);

    cout << "Aktivitas terpilih (index): ";
    int lastFinish = -1;

    for (auto act : activities) {
        if (act.start >= lastFinish) {
            cout << act.index << " ";
            lastFinish = act.finish;
        }
    }
    cout << endl;
}

int main() {
    vector<Activity> activities = {
        {1, 2, 0}, {3, 4, 1}, {0, 6, 2},
        {5, 7, 3}, {8, 9, 4}, {5, 9, 5}
    };

    activitySelection(activities);
    return 0;
}
```

## 📚 Analisis Kompleksitas
Kompleksitas Waktu : O(n log n)
Kompleksitas Ruang : O(n)

## 🌟 Aplikasi Dunia Nyata
- Penjadwalan ruang kelas/meeting/lab
- Sistem operasi (CPU scheduling)
- Logistik (rute kendaraan)
- Telekomunikasi (bandwidth allocation)

## 💪 Kekuatan dan Keterbatasan
Kekuatan :
- Mudah diimplementasikan
- Efisien untuk dataset besar
- Memberikan solusi optimal

Keterbatasan :
- Membutuhkan pengurutan
- Tidak cocok untuk masalah kompleks

## 🏁 Kesimpulan
Diselesaikan dengan algoritma greedy yang mengurutkan aktivitas berdasarkan waktu selesai, menghasilkan solusi optimal dengan efisiensi O(n log n). Cocok untuk aplikasi penjadwalan.

