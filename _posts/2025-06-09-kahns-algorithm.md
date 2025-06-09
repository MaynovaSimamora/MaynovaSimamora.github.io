---
title: "Kahn's Algorithm"
date: 2025-06-09 08:00:00 +0800
categories: [DAA, Kahn's Algorithm]
tags: [Topological Sort, BFS, Graph]
---

# Kahn's Algorithm
## 🎯 Kelompok 9  

## 📌 Deskripsi Singkat  
**Kahn’s Algorithm** adalah algoritma penyusunan topologi (topological sorting) pada graf berarah tanpa siklus (**Directed Acyclic Graph / DAG**). Algoritma ini menggunakan pendekatan **Breadth-First Search (BFS)** untuk menentukan urutan simpul berdasarkan ketergantungan antar simpul.

## 🧠 Konsep Utama  
- Digunakan untuk menyusun urutan simpul dalam **graf berarah tanpa siklus (DAG)**.
- Berguna dalam masalah seperti penjadwalan tugas, build system, dan dependency management.
- Menggunakan konsep **in-degree** (jumlah sisi masuk ke sebuah node).

## 🧑‍💻 Langkah-Langkah Penyelesaian  
1. Hitung in-degree untuk setiap simpul.
2. Masukkan semua simpul dengan in-degree = 0 ke dalam queue.
3. Ambil simpul dari queue, tambahkan ke hasil urutan topologis.
4. Kurangi in-degree dari semua tetangga simpul tersebut.
5. Jika in-degree tetangga menjadi 0, tambahkan ke queue.
6. Ulangi hingga semua simpul diproses atau jika masih ada sisi tersisa → berarti graf memiliki siklus.

## 📥 Input  
- Graf berupa daftar sisi berarah (misalnya A → B)
- Daftar simpul dan hubungan ketergantungan

## 📤 Output  
- Urutan topologis valid  
- Deteksi apakah graf memiliki siklus

## 🧮 Contoh Soal  
**Input:**  
A → C  
B → C  
C → D  

**Output:**  
Urutan topologis valid: A → B → C → D  
Atau: B → A → C → D  

## 💻 Contoh Kode (C++)  

```cpp
#include <iostream>
#include <unordered_map>
#include <vector>
#include <queue>
using namespace std;

void kahnTopologicalSort(unordered_map<char, vector<char>>& graph, unordered_map<char, int>& in_degree) {
    queue<char> q;
    for (auto& entry : in_degree) {
        if (entry.second == 0) q.push(entry.first);
    }

    while (!q.empty()) {
        char u = q.front();
        cout << u << " ";
        q.pop();

        for (char v : graph[u]) {
            in_degree[v]--;
            if (in_degree[v] == 0) q.push(v);
        }
    }
}

int main() {
    unordered_map<char, vector<char>> graph;
    unordered_map<char, int> in_degree;

    // Tambahkan sisi
    graph['A'].push_back('C');
    graph['B'].push_back('C');
    graph['C'].push_back('D');

    // Inisialisasi in-degree
    for (auto& pair : graph) {
        for (char v : pair.second) {
            in_degree[v]++;
        }
    }

    cout << "Urutan Topologis: ";
    kahnTopologicalSort(graph, in_degree);
    cout << endl;

    return 0;
}
```

## 📚 Analisis Kompleksitas
Waktu : O(V + E)
Ruang : O(V)

## 🌟 Aplikasi Dunia Nyata
1. Penjadwalan tugas berbasis dependensi
2. Build system di software development
3. Pengelolaan prasyarat mata kuliah
4. Pipeline processing dalam machine learning/data engineering

## 💪 Kekuatan dan Keterbatasan
Kekuatan :
- Efisien (O(V + E))
- Mendeteksi siklus secara otomatis
- Cocok untuk masalah ketergantungan

Keterbatasan :
- Hanya bekerja pada graf berarah tanpa siklus (DAG)
- Tidak menjamin satu-satunya solusi (banyak kemungkinan urutan)

## 🏁 Kesimpulan
Kahn’s Algorithm adalah metode sistematis dan efisien untuk melakukan penyusunan topologi (topological sort) pada graf berarah tanpa siklus (DAG) . Selain menentukan urutan valid, algoritma ini juga bisa mendeteksi adanya siklus dalam graf. Sangat berguna dalam pengaturan tugas berbasis dependensi.