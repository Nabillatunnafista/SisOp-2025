# SISTEM OPERASI 
## Tugas Tambahan Mencari kasus yang sama dengan tugas sebelumnya dipractice exercise S10-Ch05

Nama  : Nabillatun Nafista 

NRP   : 3124521027

Kelas : Teknik Informatika - A
 
---

### Shortest Job First (SJF)
Konsep dasar dan contoh non-preemptif SJF dibahas di Bagian 5.3.2, halaman 207.
contoh dengan proses P1 ,P2 ,P3 ,P4 dan waktu burst masing-masing 6, 8, 7, 3 milidetik, beserta Gantt chart dan perhitungan waktu tunggu rata-rata.  

### Shortest Remaining Time First (SRTF)
yang merupakan preemptive SJF, juga dijelaskan di Bagian 5.3.2, halaman 209. Contoh dengan proses P1 ,P 2 ,P3 ,P4 dengan waktu kedatangan dan waktu burst yang berbeda
diberikan, juga dengan Gantt chart dan perhitungan waktu tunggu rata-rata. 

### Round Robin (RR)
Konsep dan implementasi RR dijelaskan di Bagian 5.3.3, halaman 209-210.
Contoh spesifik untuk RR dengan waktu kuantum 4 milidetik diberikan di Bagian 5.3.3, halaman 210. Proses P1 ,P2 ,P3 dengan waktu burst 24, 3, 3 milidetik digunakan untuk ilustrasi, 
termasuk Gantt chart dan perhitungan waktu tunggu rata-rata.

---
### Untuk practice exercise yang relevan pada algoritma ini berada di latihan 5.4
## 1. SJF without arrival time (non-preemptive)
![Image Alt]()

### Analisa:
SJF optimal dalam meminimalkan waktu tunggu rata-rata dan waktu penyelesaian rata-rata untuk sekumpulan proses yang diberikan. Namun, SJF dapat mengalami kelaparan (starvation) jika ada aliran proses pendek yang terus-menerus. Karena semua proses tiba pada waktu 0, tidak ada pertimbangan waktu kedatangan untuk penjadwalan awal.

### Logika Alir (Flow Logic):
Dalam algoritma Penjadwalan SJF (Shortest Job First) Tanpa Waktu Kedatangan (Non-Preemptive) ini, CPU dialokasikan ke proses dengan waktu burst terkecil. Setelah sebuah proses mulai dieksekusi, proses tersebut akan berjalan hingga selesai tanpa interupsi. Karena semua proses tiba pada waktu 0, penjadwal cukup mengurutkan semua proses berdasarkan waktu burst-nya secara menaik dan mengeksekusinya secara berurutan.

### Perhitungan:
Pertama, urutkan proses berdasarkan Waktu Burst:

| Proses | Waktu Burst (ms) |
| :------ | :-------------- |
| $P_2$   | 1               |
| $P_1$   | 2               |
| $P_4$   | 4               |
| $P_5$   | 5               |
| $P_3$   | 8               |

**Gantt Chart:**
```
| P2 | P1 | P4 | P5 | P3 |
0    1    3    7    12   20
```

### Perhitungan Metrik:
* **Waktu Selesai (Completion Time - CT):**
    * $P_2$: 1
    * $P_1$: 3
    * $P_4$: 7
    * $P_5$: 12
    * $P_3$: 20
* **Waktu Penyelesaian (Turnaround Time - TAT) = Waktu Selesai - Waktu Kedatangan:**
    * $P_2$: $1 - 0 = 1$
    * $P_1$: $3 - 0 = 3$
    * $P_4$: $7 - 0 = 7$
    * $P_5$: $12 - 0 = 12$
    * $P_3$: $20 - 0 = 20$
    * Waktu Penyelesaian Rata-rata = $(1 + 3 + 7 + 12 + 20) / 5 = 43 / 5 = 8.6$ ms
* **Waktu Tunggu (Waiting Time - WT) = Waktu Penyelesaian - Waktu Burst:**
    * $P_2$: $1 - 1 = 0$
    * $P_1$: $3 - 2 = 1$
    * $P_4$: $7 - 4 = 3$
    * $P_5$: $12 - 5 = 7$
    * $P_3$: $20 - 8 = 12$
    * Waktu Tunggu Rata-rata = $(0 + 1 + 3 + 7 + 12) / 5 = 23 / 5 = 4.6$ ms
      
## 2. SJF without arrival time (non-preemptive)
![Image Alt]()

### Analisa:
Algoritma ini sangat cocok dan realistis untuk skenario yang diberikan karena secara akurat mempertimbangkan baik waktu kedatangan proses (yang berbeda) maupun sifat penjadwalan yang non-preemptive. Pada setiap titik keputusan (yaitu, ketika CPU bebas untuk menjadwalkan proses berikutnya), algoritma akan memilih proses dengan waktu burst paling kecil dari daftar proses yang sudah berada di antrean "siap" (yaitu, sudah tiba).

### Logika Alir (Flow Logic):
Pada algoritma SJF (Shortest Job First) dengan Waktu Kedatangan (Non-Preemptive) ini, CPU dialokasikan ke proses yang memiliki waktu burst terpendek di antara proses-proses yang sudah tiba dan siap dieksekusi. Sifat "non-preemptive" berarti bahwa begitu sebuah proses mulai dieksekusi, proses tersebut akan berjalan hingga selesai tanpa dapat dihentikan sementara, meskipun ada proses lain yang tiba dengan waktu burst yang lebih pendek. Penjadwal membuat keputusan saat CPU menjadi bebas dan/atau ketika ada proses baru yang tiba.

### Langkah-langkah Perhitungan SJF (Shortest Job First) dengan Waktu Kedatangan (Non-Preemptive):
1.  **Waktu $T=0.0$:**
    * $P_1$ tiba (Burst: 8).
    * $P_1$ mulai dieksekusi karena tidak ada proses lain yang tiba.
    * Sisa waktu $P_1$: 8.
2.  **Waktu $T=0.4$:**
    * $P_2$ tiba (Burst: 4).
    * $P_1$ sedang berjalan (telah berjalan 0.4 ms).
    * **Tidak ada preemption** karena penjadwalan non-preemptive. $P_1$ tetap berjalan.
    * Sisa waktu $P_1$: $8 - 0.4 = 7.6$ ms.
3.  **Waktu $T=1.0$:**
    * $P_3$ tiba (Burst: 1).
    * $P_1$ masih berjalan (telah berjalan 1.0 ms).
    * **Tidak ada preemption**. $P_1$ tetap berjalan.
    * Sisa waktu $P_1$: $8 - 1.0 = 7.0$ ms.
4.  **Waktu $T=8.0$:**
    * $P_1$ selesai dieksekusi.
    * CPU bebas.
    * Proses yang sudah tiba dan siap dieksekusi: $P_2$ (Burst: 4) dan $P_3$ (Burst: 1).
    * **Pilih yang terpendek:** $P_3$ (Burst 1) lebih pendek dari $P_2$ (Burst 4).
    * $P_3$ mulai dieksekusi.
5.  **Waktu $T=9.0$:**
    * $P_3$ selesai dieksekusi.
    * CPU bebas.
    * Proses yang tersisa dan siap dieksekusi: $P_2$ (Burst: 4).
    * $P_2$ mulai dieksekusi.
6.  **Waktu $T=13.0$:**
    * $P_2$ selesai dieksekusi.
    * Semua proses telah selesai.

### Gantt Chart:
```
| P1 | P3 | P2 |
0.0  8.0  9.0  13.0
```

### Perhitungan Metrik:
* **Waktu Selesai (Completion Time - CT):**
    * $P_1$: 8.0 (selesai pada 8.0)
    * $P_3$: 9.0 (selesai pada 9.0)
    * $P_2$: 13.0 (selesai pada 13.0)
* **Waktu Penyelesaian (Turnaround Time - TAT) = Waktu Selesai - Waktu Kedatangan:**
    * $P_1$: $8.0 - 0.0 = 8.0$ ms
    * $P_2$: $13.0 - 0.4 = 12.6$ ms
    * $P_3$: $9.0 - 1.0 = 8.0$ ms
    * **Waktu Penyelesaian Rata-rata** = $(8.0 + 12.6 + 8.0) / 3 = 28.6 / 3 \approx 9.53$ ms
* **Waktu Tunggu (Waiting Time - WT) = Waktu Penyelesaian - Waktu Burst:**
    * $P_1$: $8.0 - 8 = 0.0$ ms
    * $P_2$: $12.6 - 4 = 8.6$ ms
    * $P_3$: $8.0 - 1 = 7.0$ ms
    * **Waktu Tunggu Rata-rata** = $(0.0 + 8.6 + 7.0) / 3 = 15.6 / 3 = 5.2$ ms

## 3. SRTF (preemptive)
![Image Alt]()

### Analisa:
Algoritma SRTF dirancang untuk meminimalkan waktu tunggu rata-rata dan waktu penyelesaian rata-rata. Dengan preemptive, algoritma ini dapat merespons dengan cepat terhadap kedatangan proses-proses pendek, yang sangat efisien untuk sistem interaktif. Namun, ada overhead dari konteks switching yang sering terjadi, dan juga bisa terjadi kelaparan (starvation) untuk proses-proses yang panjang jika ada aliran proses pendek yang terus-menerus. Untuk soal ini, SRTF akan mengeksekusi proses berdasarkan sisa waktu burst terkecil, dengan mempertimbangkan kedatangan proses baru untuk preemption.

### Logika Alir (Flow Logic):
Pada algoritma SRTF, CPU selalu dijalankan oleh proses yang memiliki sisa waktu eksekusi (burst time) terpendek di antara semua proses yang saat ini berada di sistem (telah tiba). Jika sebuah proses baru tiba dan waktu burst-nya lebih pendek dari sisa waktu burst proses yang sedang dieksekusi, maka proses yang sedang dieksekusi akan dihentikan sementara (preempted), dan CPU akan diberikan kepada proses yang baru tiba tersebut. Keputusan penjadwalan ini dievaluasi pada setiap perubahan status (misalnya, proses selesai, atau proses baru tiba).

### Langkah-langkah Perhitungan:

1.  **Pada Waktu $T=0$:**
    Hanya $P_1$ yang tiba (Burst: 8).
    $P_1$ mulai dieksekusi. Sisa $P_1$: 8.
2.  **Pada Waktu $T=1$:**
    $P_2$ tiba (Burst: 4).
    $P_1$ telah berjalan 1 unit waktu. Sisa $P_1$: $8 - 1 = 7$.
    Bandingkan sisa $P_1$ (7) dengan burst $P_2$ (4). $P_2$ lebih pendek.
    $P_1$ di-preempt. $P_2$ mulai dieksekusi. Sisa $P_2$: 4.
3.  **Pada Waktu $T=2$:**
    $P_3$ tiba (Burst: 9).
    $P_2$ telah berjalan $2 - 1 = 1$ unit waktu. Sisa $P_2$: $4 - 1 = 3$.
    Bandingkan sisa $P_2$ (3) dengan burst $P_3$ (9). $P_2$ masih lebih pendek.
    $P_2$ terus dieksekusi.
4.  **Pada Waktu $T=3$:**
    $P_4$ tiba (Burst: 5).
    $P_2$ telah berjalan $3 - 1 = 2$ unit waktu. Sisa $P_2$: $4 - 2 = 2$.
    Bandingkan sisa $P_2$ (2) dengan burst $P_3$ (9) dan burst $P_4$ (5). $P_2$ (sisa 2) masih yang terpendek.
    $P_2$ terus dieksekusi.
5.  **Pada Waktu $T=5$:**
    $P_2$ selesai dieksekusi ($P_2$ berjalan dari $T=1$ hingga $T=5$, total 4 unit waktu).
    Proses yang tersisa: $P_1$ (sisa 7), $P_3$ (burst 9), $P_4$ (burst 5).
    Bandingkan sisa waktu: $P_1$ (7), $P_3$ (9), $P_4$ (5). $P_4$ memiliki sisa waktu terpendek.
    $P_4$ mulai dieksekusi. Sisa $P_4$: 5.
6.  **Pada Waktu $T=10$:**
    $P_4$ selesai dieksekusi ($P_4$ berjalan dari $T=5$ hingga $T=10$, total 5 unit waktu).
    Proses yang tersisa: $P_1$ (sisa 7), $P_3$ (burst 9).
    Bandingkan sisa waktu: $P_1$ (7) dan $P_3$ (9). $P_1$ memiliki sisa waktu terpendek.
    $P_1$ melanjutkan eksekusi. Sisa $P_1$: 7.
7.  **Pada Waktu $T=17$:**
    $P_1$ selesai dieksekusi ($P_1$ berjalan dari $T=0$ hingga $T=1$ (1 unit), kemudian dari $T=10$ hingga $T=17$ (7 unit), total $1+7=8$ unit waktu).
    Proses yang tersisa: $P_3$ (burst 9).
    $P_3$ mulai dieksekusi. Sisa $P_3$: 9.
8.  **Pada Waktu $T=26$:**
    $P_3$ selesai dieksekusi ($P_3$ berjalan dari $T=17$ hingga $T=26$, total 9 unit waktu).
    Semua proses telah selesai.

### Gantt Chart:
```
| P1 | P2 | P3 | P2 | P1 | P4 | P1 | P3 |
0    0.4  1.0  2.0  5.4  10.0 17.0 26.0
```
### Perhitungan Metrik:
* **Waktu Selesai (Completion Time - CT):**
    * $P_2$: 5
    * $P_4$: 10
    * $P_1$: 17
    * $P_3$: 26
* **Waktu Penyelesaian (Turnaround Time - TAT) = Waktu Selesai - Waktu Kedatangan:**
    * $P_1$: $17 - 0 = 17$ ms
    * $P_2$: $5 - 1 = 4$ ms
    * $P_3$: $26 - 2 = 24$ ms
    * $P_4$: $10 - 3 = 7$ ms
    * **Waktu Penyelesaian Rata-rata** = $(17 + 4 + 24 + 7) / 4 = 52 / 4 = 13.0$ ms
* **Waktu Tunggu (Waiting Time - WT) = Waktu Penyelesaian - Waktu Burst:**
    * $P_1$: $17 - 8 = 9$ ms
    * $P_2$: $4 - 4 = 0$ ms
    * $P_3$: $24 - 9 = 15$ ms
    * $P_4$: $7 - 5 = 2$ ms
    * **Waktu Tunggu Rata-rata** = $(9 + 0 + 15 + 2) / 4 = 26 / 4 = 6.5$ ms

---

[Nabillatun Nafista 3124521027 ]
