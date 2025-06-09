---
title: "Rat in a Maze"
date: 2025-06-09 08:00:00 +0800
categories: [DAA, Rat in a Maze]
tags: [Backtracking, Maze, C++]
---

# Rat in a Maze
## 🎯 Kelompok 6  

## 📌 Deskripsi Singkat  
Masalah **Rat in a Maze** adalah tentang mencari jalur dari titik awal ke tujuan di dalam labirin berbentuk matriks. Labirin ini direpresentasikan oleh sel-sel yang bisa dilewati (nilai 1) atau terhalang (nilai 0). Algoritma **backtracking** digunakan untuk menemukan semua kemungkinan jalur tanpa melanggar aturan.

## 🧠 Konsep Utama  
- **Labirin**: Representasi matriks dengan sel-sel yang bisa dilewati atau terhalang.  
- **Tikus**: Dimulai dari posisi awal, mencoba bergerak ke arah kanan, bawah, kiri, atau atas.  
- **Backtracking**: Jika jalur saat ini tidak berhasil, mundur ke posisi sebelumnya dan coba arah lain.

## 🧑‍💻 Langkah-Langkah Penyelesaian  
1. Mulai dari posisi awal tikus.  
2. Coba gerakan ke arah kanan, bawah, kiri, atau atas.  
3. Jika langkah valid (tidak keluar dari labirin dan bukan dinding), lanjutkan ke sel berikutnya.  
4. Jika sampai di tujuan, catat jalur tersebut.  
5. Jika tidak ada jalur yang valid, mundur ke posisi sebelumnya dan coba arah lain.

## 📥 Input  
- Matriks labirin (0 = dinding, 1 = jalan)  
- Posisi awal tikus  
- Posisi tujuan tikus  

## 📤 Output  
- Semua jalur yang valid dari awal ke tujuan  

## 🧮 Contoh Soal  
**Input:**  
Matriks: 
1 0 0 0
1 1 0 1
0 1 0 0
1 1 1 1

Posisi awal: (0, 0)  
Posisi tujuan: (3, 3)  

**Output:**  
Jalur yang valid: DRDDRR  

## 💻 Implementasi (C++)  

```cpp
#include <bits/stdc++.h>
using namespace std;

int N = 4;

bool isSafe(int x, int y, vector<vector<int>>& maze, vector<vector<bool>>& visited) {
    return (x >= 0 && x < N && y >= 0 && y < N && maze[x][y] == 1 && !visited[x][y]);
}

void solveMazeUtil(vector<vector<int>>& maze, vector<vector<bool>>& visited, int x, int y, string path, vector<string>& result) {
    if (x == N - 1 && y == N - 1) {
        result.push_back(path);
        return;
    }

    visited[x][y] = true;

    // Down
    if (isSafe(x + 1, y, maze, visited)) {
        solveMazeUtil(maze, visited, x + 1, y, path + 'D', result);
    }

    // Right
    if (isSafe(x, y + 1, maze, visited)) {
        solveMazeUtil(maze, visited, x, y + 1, path + 'R', result);
    }

    // Up
    if (isSafe(x - 1, y, maze, visited)) {
        solveMazeUtil(maze, visited, x - 1, y, path + 'U', result);
    }

    // Left
    if (isSafe(x, y - 1, maze, visited)) {
        solveMazeUtil(maze, visited, x, y - 1, path + 'L', result);
    }

    visited[x][y] = false;
}

vector<string> solveMaze(vector<vector<int>>& maze) {
    vector<string> result;
    vector<vector<bool>> visited(N, vector<bool>(N, false));
    string path = "";
    solveMazeUtil(maze, visited, 0, 0, path, result);
    return result;
}

int main() {
    vector<vector<int>> maze = {
        {1, 0, 0, 0},
        {1, 1, 0, 1},
        {0, 1, 0, 0},
        {1, 1, 1, 1}
    };
    vector<string> solutions = solveMaze(maze);
    for (const string& sol : solutions) {
        cout << sol << endl;
    }
    return 0;
}
```

## 📚 Analisis Kompleksitas
Waktu : O(4^(N*N)) dalam kasus terburuk (setiap sel memiliki 4 pilihan)
Ruang : O(N*N) untuk rekursi stack dan visited matrix

## 🌟 Aplikasi Dunia Nyata
1. Robot navigasi
2. GPS dan sistem navigasi
3. Simulasi dan permainan

## 💪 Kekuatan dan Keterbatasan
Kekuatan :
- Sederhana dan mudah diimplementasikan
- Menemukan semua solusi

Keterbatasan :
- Tidak efisien untuk labirin besar 
- Risiko stack overflow pada labirin sangat dalam

## 🏁 Kesimpulan
Masalah Rat in a Maze adalah contoh klasik dari algoritma backtracking. Dengan pendekatan ini, kita dapat menemukan semua jalur yang valid dari awal ke tujuan dalam labirin.