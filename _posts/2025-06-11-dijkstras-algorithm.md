---
title: "Dijkstra's Algorithm"
date: 2025-06-11 08:00:00 +0800
categories: [DAA, Dijkstra's Algorithm]
tags: [Shortest Path, Greedy, Graph]
---

# Dijkstra's Algorithm
## 🎯 Kelompok 10  

## 📌 Deskripsi Singkat  
**Dijkstra’s Algorithm** adalah algoritma greedy yang digunakan untuk mencari **jalur terpendek** dari satu titik ke semua titik lainnya dalam graf berbobot non-negatif. Dengan kata lain, algoritma ini membantu kita menemukan jarak minimum dari satu simpul ke seluruh simpul lain dalam graf berbobot.

## 🧠 Konsep Utama  
- Termasuk dalam kategori **algoritma greedy**
- Bekerja pada **graf berarah atau tidak berarah** dengan bobot sisi **tidak negatif**
- Menggunakan **priority queue** untuk memilih simpul dengan jarak terkecil tiap langkah
- Menjamin jalur terpendek dalam graf dengan bobot positif

## 🧑‍💻 Langkah-Langkah Penyelesaian  
1. Inisialisasi semua jarak ke nilai tak hingga, kecuali jarak dari simpul awal yang bernilai 0.
2. Gunakan priority queue untuk menyimpan pasangan (jarak, simpul).
3. Ekstraksi simpul dengan jarak terkecil.
4. Perbarui jarak semua tetangga dari simpul tersebut.
5. Ulangi hingga semua simpul telah diproses.

## 📥 Input  
- Graf berbobot (dengan bobot sisi ≥ 0)
- Simpul awal (source node)

## 📤 Output  
- Jalur terpendek dari simpul awal ke semua simpul lain  
- Total jarak terpendek ke setiap simpul

## 🧮 Contoh Soal  
**Input:**  
Graf:
A --1-- B --2-- F
| | |
1 3 2
| | |
C --2-- D --2-- E

**Output:**  
Jalur terpendek dari A ke F:  
- Jalur: A → B → F  
- Jarak total: 1 + 2 = 3

## 💻 Contoh Kode (C++)  

```cpp
#include <iostream>
#include <vector>
#include <queue>
using namespace std;

typedef pair<int, int> pii;

void dijkstra(int start, vector<vector<pii>>& adj, int n) {
    vector<int> dist(n, INT_MAX);
    priority_queue<pii, vector<pii>, greater<pii>> pq;

    dist[start] = 0;
    pq.push({0, start});

    while (!pq.empty()) {
        int u = pq.top().second;
        pq.pop();

        for (auto edge : adj[u]) {
            int v = edge.first;
            int weight = edge.second;

            if (dist[v] > dist[u] + weight) {
                dist[v] = dist[u] + weight;
                pq.push({dist[v], v});
            }
        }
    }

    cout << "Jarak Terpendek dari simpul awal:" << endl;
    for (int i = 0; i < n; ++i)
        cout << "Ke simpul " << i << ": " << dist[i] << endl;
}

int main() {
    int n = 6;
    vector<vector<pii>> adj(n);

    // Format: {tujuan, bobot}
    adj[0].push_back({1, 1});  // A -> B
    adj[0].push_back({2, 1});  // A -> C
    adj[1].push_back({2, 2});  // B -> C
    adj[1].push_back({3, 3});  // B -> D
    adj[1].push_back({4, 2});  // B -> E
    adj[3].push_back({5, 2});  // D -> F
    adj[4].push_back({5, 2});  // E -> F

    dijkstra(0, adj, n);
    return 0;
}
```

## 📚 Analisis Kompleksitas
Waktu : O(E log V), dengan struktur data priority queue
Ruang : O(V + E)

## 🌟 Aplikasi Dunia Nyata
1. Sistem navigasi (Google Maps, Waze)
2. Jaringan komputer (routing protokol)
3. Logistik dan distribusi barang
4. Sistem rekomendasi lintasan minimal

## 💪 Kekuatan dan Keterbatasan
Kekuatan :
- Menjamin jalur terpendek
- Efisien untuk graf besar jika menggunakan heap/priority queue
- Bisa digunakan untuk banyak tujuan sekaligus

Keterbatasan :
- Tidak bekerja pada graf dengan bobot negatif
- Tidak optimal jika hanya mencari jalur ke satu tujuan

## 🏁 Kesimpulan
Dijkstra’s Algorithm adalah salah satu algoritma pencarian jalur terpendek paling populer. Bekerja dengan efisien pada graf berbobot non-negatif, dan sering digunakan dalam sistem navigasi, jaringan, dan pipeline data. Meskipun tidak cocok untuk graf dengan bobot negatif, algoritma ini sangat kuat untuk kasus umum dan mudah diimplementasikan dengan struktur data modern seperti priority queue.
