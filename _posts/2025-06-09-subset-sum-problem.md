---
title: "Subset Sum Problem"
date: 2025-06-09 08:00:00 +0800
categories: [DAA, Subset Sum Problem]
tags: [Subset Sum, Dynamic Programming, C++]
---

# Subset Sum Problem
## 🎯 Kelompok 5  

## 📌 Deskripsi Singkat  
**Subset Sum Problem** adalah masalah optimasi di mana kita diberikan sebuah himpunan bilangan bulat dan sebuah nilai target. Tujuannya adalah menentukan apakah ada subset dari himpunan tersebut yang jumlah elemennya sama dengan nilai target.

## 🧠 Konsep Utama  
- Termasuk dalam kategori **NP-Complete**
- Variasi:
  - **Bounded Subset Sum Problem**: Setiap elemen hanya dapat digunakan sekali.
  - **Partition Problem**: Membagi himpunan menjadi dua subset dengan jumlah total yang sama.
  - **Exact k Elements Subset Sum**: Mencari subset dengan tepat `k` elemen yang jumlahnya sama dengan target.
  - **Unbounded Subset Sum Problem**: Elemen dapat digunakan berulang kali.
  - **Multi-target Subset Sum Problem**: Memenuhi lebih dari satu kriteria (misalnya, jumlah total dan batas berat).
  - **Approximate Subset Sum**: Mencari subset terbaik yang mendekati target jika tidak ada solusi tepat.

## 🧑‍💻 Pendekatan Penyelesaian  
1. **Pendekatan Rekursif**:  
   - Cek semua subset secara eksplisit.  
   - Kompleksitas waktu: O(2ⁿ)  
   - Tidak efisien untuk input besar.

2. **Dynamic Programming Approach**:  
   - Menggunakan tabel DP untuk menyimpan hasil submasalah.  
   - Kompleksitas waktu: O(n × sum)  
   - Kompleksitas ruang: O(sum)  

## 📥 Input  
- Himpunan bilangan bulat  
- Nilai target

## 📤 Output  
- Boolean: Apakah ada subset yang jumlahnya sama dengan target?

## 🧮 Contoh Soal  
**Input:**  
Set = {3, 34, 4, 12, 5, 2}, Target = 9  

**Output:**  
Ya. Subset {4, 5} menghasilkan total 9.

## 💻 Implementasi (C++)  

```cpp
#include <bits/stdc++.h>
using namespace std;

bool isSubsetSum(vector<int>& arr, int n, int sum) {
    bool dp[n + 1][sum + 1];
    memset(dp, false, sizeof(dp));

    // Base cases
    for (int i = 0; i <= n; i++) dp[i][0] = true;
    for (int j = 1; j <= sum; j++) dp[0][j] = false;

    // Fill the DP table in bottom up manner
    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= sum; j++) {
            if (arr[i - 1] <= j)
                dp[i][j] = dp[i - 1][j] || dp[i - 1][j - arr[i - 1]];
            else
                dp[i][j] = dp[i - 1][j];
        }
    }

    return dp[n][sum];
}

int main() {
    vector<int> arr = {3, 34, 4, 12, 5, 2};
    int sum = 9;
    int n = arr.size();
    if (isSubsetSum(arr, n, sum))
        cout << "Subset with given sum exists";
    else
        cout << "No subset with given sum";
    return 0;
}
```

## 📚 Analisis Kompleksitas
Waktu : O(n × sum)
Ruang : O(sum)

## 🌟 Aplikasi Dunia Nyata
- Kriptografi
- Alokasi sumber daya
- Genetika dan bioinformatika
- Keuangan dan investasi
- Perancangan permainan dan teka-teki

## 💪 Kekuatan dan Keterbatasan
Kekuatan :
- Menjamin solusi optimal
- Efisien untuk dataset besar
- Keterbatasan :
- Membutuhkan memori tambahan untuk tabel DP

## 🏁 Kesimpulan
Subset Sum Problem adalah masalah optimasi yang penting dalam ilmu komputer. Meskipun termasuk dalam kategori NP-Complete, pendekatan dynamic programming memberikan solusi yang efisien untuk banyak kasus praktis.