# SISTEM OPERASI # 
Nama  : Nabillatun Nafista (3124521027)

Kelas : 1 Teknik Informatika - A

Tugas pertemuan ke-7  

---
## 1. **Penerapan Thread pada Java (`SumTask.java`)**

Program `SumTask.java` merupakan implementasi **paralel menggunakan Fork/Join Framework** di Java. Konsep yang diangkat adalah memecah pekerjaan besar menjadi beberapa tugas kecil yang bisa dijalankan secara paralel oleh beberapa thread.

```java
public class SumTask extends RecursiveTask<Integer>

```

Kelas ini adalah turunan dari `RecursiveTask<Integer>`, yaitu bagian dari Fork/Join yang memungkinkan kita memecah tugas secara rekursif dan menjalankannya paralel.


```java
if (end - begin < THRESHOLD) {   
} else {
}

```

Kalau jumlah data yang diproses lebih kecil dari `THRESHOLD` (yaitu 1000), maka proses penjumlahan dilakukan langsung (disebut **conquer**). Tapi kalau lebih besar, array dibagi dua bagian dan masing-masing dibuat jadi subtask baru (**divide**). Subtask ini dijalankan paralel lewat `fork()`.

```java
leftTask.fork();
rightTask.fork();
return rightTask.join() + leftTask.join();

```

Setelah membagi array, dua subtask (`leftTask` dan `rightTask`) dijalankan paralel. Kemudian, program menunggu masing-masing selesai dengan `join()`, lalu hasilnya dijumlahkan.

```java
ForkJoinPool pool = new ForkJoinPool();
int sum = pool.invoke(task);

```

Di `main()`, program membuat array acak berukuran 10.000 elemen, lalu membuat objek `SumTask` dan menjalankannya dengan `ForkJoinPool`. Pool ini otomatis mengatur thread-thread yang dibutuhkan.


Dengan pendekatan Fork/Join, program ini mampu membagi proses penjumlahan menjadi sub-proses yang berjalan paralel, sehingga lebih efisien dibanding penjumlahan biasa, terutama di sistem multi-core. Program ini cocok jadi contoh penerapan threading modern di Java, yang tidak lagi harus membuat thread satu per satu, tapi cukup fokus pada pembagian tugas, dan sistem yang mengatur paralelismenya.



## 2. **Penerapan Thread di Linux (`thrd-posix.c`)**

Program `thrd-posix.c` adalah contoh penerapan multithreading di Linux menggunakan **POSIX Thread** (pthreads). Dengan API ini, programmer bisa membuat dan mengatur thread secara langsung dalam bahasa C. Konsep dasar di program ini adalah membuat satu thread tambahan untuk menghitung jumlah angka dari 0 sampai angka tertentu.


```c
pthread_t tid;
pthread_create(&tid, NULL, runner, argv[1]);

```

Di sini, `pthread_create()` dipakai untuk membuat thread baru. Parameter `runner` adalah fungsi yang akan dijalankan oleh thread. Argumen `argv[1]` berisi batas akhir dari penjumlahan, yang diambil dari input saat program dijalankan.


```c
void *runner(void *param) {
    int i, upper = atoi(param);
    sum = 0;
    for (i = 1; i <= upper; i++)
        sum += i;

    pthread_exit(0);
}

```

Fungsi `runner` ini akan dijalankan oleh thread yang dibuat tadi. Ia mengonversi parameter ke integer (`upper`), lalu menjumlahkan angka dari 1 sampai `upper`. Hasilnya disimpan di variabel global `sum`.


```c
pthread_join(tid, NULL);

```

Setelah thread dibuat, thread utama tidak langsung dilanjutkan. Dia nunggu thread tambahan selesai dulu dengan `pthread_join()`. Ini penting supaya hasil perhitungan dari thread tambahan gak diakses sebelum waktunya.

Keseluruhannya, penerapan thread di `thrd-posix.c` cukup simpel tapi mencerminkan cara kerja dasar multithreading di Linux.  Ada beberapa keuntungan penggunaanya juga seperti Program bisa jadi lebih responsif, Proses-proses berat bisa dibagi ke thread sendiri dan Bisa disesuaikan untuk lebih banyak thread di realtime case.


## 3. **Penerapan Thread di Windows (`thrd-win32.c`)**

Program `thrd-win32.c` merupakan contoh penggunaan **thread di sistem operasi Microsoft Windows**. Tidak seperti POSIX Thread di Linux, Windows punya API sendiri untuk manajemen thread, salah satunya lewat fungsi `CreateThread()`. Tujuan program ini sama seperti versi POSIX-nya, yaitu menghitung jumlah angka dari 0 sampai angka tertentu (yang dimasukkan lewat command line).

```c
DWORD ThreadId;
HANDLE ThreadHandle;
ThreadHandle = CreateThread(NULL, 0, Summation, argv[1], 0, &ThreadId);

```

Fungsi `CreateThread()` digunakan untuk membuat thread baru. Fungsi yang dijalankan adalah `Summation`, dan argumen yang dikirim adalah `argv[1]`, yaitu batas angka terakhir untuk dijumlahkan. Thread akan berjalan sendiri setelah dipanggil.

```c
DWORD WINAPI Summation(LPVOID Param) {
    int upper = atoi(Param);
    Sum = 0;
    for (int i = 1; i <= upper; i++)
        Sum += i;

    return 0;
}

```

Fungsi `Summation` dijalankan oleh thread yang dibuat. Di dalamnya, program mengonversi argumen ke integer, lalu menjumlahkan angka dari 1 sampai `upper`. Hasil disimpan di variabel global `Sum`.

```c
WaitForSingleObject(ThreadHandle, INFINITE);

```

Agar thread utama tidak mengeksekusi lebih dulu sebelum thread selesai, digunakan `WaitForSingleObject()` untuk menunggu sampai thread selesai bekerja. Tanpa ini, nilai `Sum` bisa diakses sebelum selesai dihitung.


Penerapan thread di Windows melalui `CreateThread()` cukup fleksibel, tapi sedikit lebih verbose dibanding pthread di Linux. Setiap thread diidentifikasi lewat `HANDLE`, dan fungsi yang dijalankan harus mengikuti format khusus (`DWORD WINAPI`).

---

[Nabillatun Nafista 3124521027 ]
