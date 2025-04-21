# SISTEM OPERASI # 

Nama  : Nabillatun Nafista  (3124521027)

Kelas : 1 Teknik Informatika - A

Tugas pertemuan ke-7  

---
### 4.1 Tiga Contoh Pemrograman di Mana Multithreading Memberikan Kinerja Lebih Baik

*Jawaban:* 
#### 1. Pemrosesan Data Paralel
- **Contoh**: Aplikasi yang memproses data besar seperti analisis log, pemrosesan gambar, atau perhitungan ilmiah.
- **Keuntungan Multithreading**: Data dapat dibagi ke beberapa bagian dan diproses secara paralel, sehingga mempercepat waktu eksekusi dibandingkan dengan pemrosesan sekuensial.

#### 2. Aplikasi Responsif dengan Operasi Blocking
- **Contoh**: Aplikasi GUI atau web yang harus tetap responsif sambil melakukan download file, akses database, dll.
- **Keuntungan Multithreading**: Operasi blocking dapat dijalankan di thread terpisah, sehingga thread utama tetap bisa merespon pengguna.

#### 3. Server dengan Banyak Koneksi Klien
- **Contoh**: Server web, game, atau database.
- **Keuntungan Multithreading**: Setiap koneksi dapat dilayani oleh thread terpisah, memungkinkan server menangani banyak permintaan secara bersamaan.

---

### 4.2 Perhitungan Speedup dengan Hukum Amdahl hitung perolehan kecepatan aplikasi yang memiliki komponen paralel 60 persen untuk (a) dua inti pemrosesan dan (b) empat inti pemrosesan.

*Jawaban:* 

Rumus:

$$
\text{Speedup} = \frac{1}{(1-P) + \frac{P}{N}}
$$


- **P**: Proporsi program yang dapat diparalelkan (0.6)
- **N**: Jumlah inti prosesor

**(a) Dua inti:**

Speedup = 1 / [(1 - 0.6) + (0.6 / 2)] = 1.43


**(b) Empat inti:**  

Speedup = 1 / [(1 - 0.6) + (0.6 / 4)] = 1.82


---


### **4.3 Apakah server web multithread menunjukkan paralelisme tugas atau data?**

*Jawaban:*   
Server web multithread menunjukkan **paralelisme tugas (task parallelism)**, bukan paralelisme data. Dalam konteks server web, setiap thread biasanya menangani permintaan (request) dari klien yang berbeda. Meskipun kode program yang dijalankan oleh setiap thread bisa sama (misalnya, mengambil halaman HTML atau memproses permintaan API), data yang diproses oleh setiap thread **berbeda** karena berasal dari klien yang berbeda pula. Oleh karena itu, multithreading di sini digunakan untuk menyelesaikan berbagai **tugas** secara bersamaan, bukan untuk memecah satu kumpulan data besar menjadi bagian-bagian kecil yang diproses secara paralel.

---

### **4.4 Apa dua perbedaan antara thread tingkat pengguna dan thread tingkat kernel? Dalam keadaan apa salah satu jenis thread lebih baik daripada thread lainnya?**

*Jawaban:* 
| **Fitur** | **Thread Tingkat Pengguna (User-Level Threads)** | **Thread Tingkat Kernel (Kernel-Level Threads)** |
|----------|--------------------------------------------------|--------------------------------------------------|
| **Manajemen** | Dikelola oleh user-level thread library | Dikelola oleh kernel sistem operasi |
| **Visibilitas** | Tidak terlihat oleh kernel | Terlihat dan dikelola oleh kernel |
| **Implementasi** | Lebih cepat untuk dibuat dan di-switch | Lebih lambat untuk dibuat dan di-switch |
| **Blocking System Calls** | Dapat memblokir seluruh proses jika satu thread melakukan blocking | Tidak memblokir seluruh proses jika satu thread diblokir |
| **Penjadwalan** | Dilakukan oleh thread library | Dilakukan oleh kernel |

### **Kapan Salah Satu Jenis Thread Lebih Baik**

#### Thread Tingkat Pengguna Lebih Baik Ketika:
- Aplikasi membutuhkan pembuatan dan switching thread yang sangat cepat.
- Aplikasi tidak terlalu bergantung pada operasi I/O yang sering melakukan blocking.
- Portabilitas antar sistem operasi menjadi prioritas (karena implementasi thread library ada di tingkat pengguna).
- Manajemen thread yang disesuaikan diperlukan.

#### Thread Tingkat Kernel Lebih Baik Ketika:
- Aplikasi melakukan banyak operasi I/O yang dapat menyebabkan blocking.
- Ingin memanfaatkan multiprosesor (paralelisme sejati), karena kernel dapat menjadwalkan beberapa thread pada inti CPU yang berbeda.

---

### **4.5 Menjelaskan tindakan yang diambil oleh kernel untuk beralih konteks antara thread tingkat kernel**

*Jawaban:* 
Ketika terjadi **context switch** antara thread tingkat kernel, sistem operasi melakukan beberapa langkah berikut:

1. **Menyimpan Status Thread yang Sedang Berjalan**  
   Kernel menyimpan semua informasi penting dari thread yang sedang berjalan, seperti register CPU, program counter (PC), stack pointer, dan status lainnya ke dalam **Thread Control Block (TCB)**.

2. **Memilih Thread Baru**  
   Scheduler kernel memilih thread baru untuk dijalankan berdasarkan kebijakan penjadwalan (misalnya: round-robin, priority-based, dll).

3. **Memuat Status Thread Baru**  
   Informasi konteks dari thread baru dimuat ke CPU dari TCB-nya, termasuk nilai register, PC, dan stack pointer.

4. **Melanjutkan Eksekusi Thread Baru**  
   CPU mulai menjalankan thread baru dari titik terakhir eksekusinya.

---

### **4.6 Sumber daya apa yang digunakan saat thread dibuat? Apa perbedaannya dengan sumber daya yang digunakan saat proses dibuat?**

*Jawaban:* 
### **Sumber Daya yang Digunakan Saat Thread Dibuat:**
- Stack pribadi untuk data lokal dan panggilan fungsi.
- Register CPU (PC, SP, dsb.) untuk status eksekusi.
- Metadata seperti Thread ID (TID) dan Thread Control Block (TCB).

### **Thread Berbagi Sumber Daya Dalam Satu Proses:**
- Ruang alamat memori (memory space)
- File descriptor
- Variabel global
- Segmen kode dan data

### **Saat Proses Dibuat, Sistem Harus Menyediakan:**
- Ruang alamat memori baru (sendiri)
- Salinan baru dari semua variabel, kode, dan data
- Process Control Block (PCB)
- File descriptor dan resource sistem lainnya

### **Perbedaan Utama:**
- **Pembuatan proses** lebih mahal dan lambat karena membutuhkan alokasi sumber daya penuh.
- **Pembuatan thread** lebih ringan dan cepat karena sumber daya dibagi dalam satu proses.

---

### **4.7 Apakah perlu mengikat thread real-time ke LWP dalam model many-to-many?**

*Jawaban:*   
**Ya**, thread real-time **perlu diikat (bound)** ke LWP.

### **Alasan:**
Dalam model **many-to-many**, beberapa thread tingkat pengguna dipetakan ke sejumlah terbatas LWP (Lightweight Process). Tanpa pengikatan, thread pengguna bisa berpindah-pindah antar LWP, yang tidak menjamin **determinisme waktu**—sesuatu yang sangat penting dalam sistem real-time.

#### **Dengan Mengikat Thread Real-Time ke LWP:**
- Thread memiliki jalur eksekusi tetap ke kernel.
- Prioritas dan kebijakan penjadwalan real-time tetap berlaku.
- Menjamin **respons waktu yang konsisten dan dapat diprediksi**.

#### **Tanpa Pengikatan:**
- Thread real-time bisa terpengaruh oleh thread lain di LWP yang sama.
- Tidak bisa menjamin waktu respons real-time yang diperlukan.

---

### 4.8 Berikan dua contoh pemrograman di mana multithreading tidak memberikan kinerja yang lebih baik daripada solusi single-threaded.

*Jawaban:*  
1. *Program yang sangat sederhana:* Jika program hanya melakukan satu tugas kecil, overhead pembuatan dan pengelolaan thread dapat melebihi manfaat paralelisme.  
2. *Program I/O-bound dengan sedikit komputasi:* Jika program menghabiskan sebagian besar waktunya menunggu operasi I/O, menambahkan thread tidak akan meningkatkan kinerja secara signifikan karena I/O adalah faktor pembatas.

---

### 4.9 Dalam keadaan apa solusi multithreaded menggunakan beberapa thread kernel memberikan kinerja yang lebih baik daripada solusi single-threaded pada sistem single-processor?

*Jawaban:*  
- *Menangani I/O yang memblokir:* Jika satu thread diblokir menunggu I/O, thread lain dapat terus berjalan, meningkatkan responsivitas keseluruhan.  
- *Menangani peristiwa asinkron:* Multithreading dapat memungkinkan program untuk merespons peristiwa asinkron (misalnya, input pengguna, data jaringan) tanpa mengganggu tugas utama.

---

### 4.10 Komponen status program mana yang dibagikan antar thread dalam proses multithreaded?

- *a. Nilai register*  
- *b. Memori heap*  
- *c. Variabel global*  
- *d. Memori stack*  

*Jawaban:*  
a, b, c dibagikan; d tidak dibagikan.

---

### 4.11 Dapatkah solusi multithreaded menggunakan beberapa thread level pengguna mencapai kinerja yang lebih baik pada sistem multiprosesor daripada pada sistem single-processor? Jelaskan.

*Jawaban:*  
Ya, mungkin saja. Meskipun thread level pengguna dikelola oleh pustaka pengguna dan tidak diketahui oleh kernel, pustaka dapat menjadwalkan thread pada prosesor yang berbeda, memungkinkan paralelisme.

---

### 4.12 Dalam Bab 3, kita membahas browser Chrome Google dan praktiknya membuka setiap tab baru dalam proses terpisah. Apakah manfaat yang sama akan tercapai jika, alih-alih, Chrome dirancang untuk membuka setiap tab baru dalam thread terpisah? Jelaskan.

*Jawaban:*  
Tidak, manfaat yang sama tidak akan tercapai. Proses terpisah memberikan isolasi memori dan perlindungan yang lebih kuat daripada thread terpisah. Jika satu tab mengalami crash dalam proses terpisah, itu tidak akan memengaruhi tab lain. Dengan thread, crash dapat memengaruhi seluruh aplikasi.

---

### 4.13 Apakah mungkin memiliki konkurensi tetapi bukan paralelisme? Jelaskan.

*Jawaban:*  
Ya, mungkin saja. Konkurensi berarti beberapa tugas dapat berjalan bersamaan, tetapi tidak harus secara paralel. Misalnya, penjadwalan round-robin pada single-processor memungkinkan konkurensi tetapi bukan paralelisme sejati.

---

### 4.14 Menggunakan Hukum Amdahl, hitung perolehan kecepatan untuk aplikasi berikut:

- *40% paralel:*  
  - (a) 8 inti: Speedup = 1.43  
  - (b) 16 inti: Speedup = 1.54  

- *67% paralel:*  
  - (a) 2 inti: Speedup = 1.51  
  - (b) 4 inti: Speedup = 2.01  

- *90% paralel:*  
  - (a) 4 inti: Speedup = 2.86  
  - (b) 8 inti: Speedup = 4.71  

---

### 4.15 Tentukan apakah masalah berikut menunjukkan paralelisme tugas atau data:

1. *Menggunakan thread terpisah untuk menghasilkan thumbnail untuk setiap foto dalam koleksi.*  
2. *Mentransposisi matriks secara paralel.*  
3. *Aplikasi jaringan di mana satu thread membaca dari jaringan dan thread lain menulis ke jaringan.*  
4. *Aplikasi penjumlahan array fork-join yang dijelaskan di Bagian 4.5.2.*  
5. *Sistem Grand Central Dispatch.*  

*Jawaban:*  
1. Paralelisme tugas  
2. Paralelisme data  
3. Paralelisme tugas  
4. Paralelisme data  
5. Paralelisme tugas  

---

### 4.16 Sistem dengan dua prosesor dual-core memiliki empat prosesor yang tersedia untuk penjadwalan. Aplikasi intensif CPU berjalan pada sistem ini. Semua input dilakukan saat program dimulai, ketika satu file harus dibuka. Demikian pula, semua output dilakukan tepat sebelum program berakhir, ketika hasil program harus ditulis ke satu file. Antara startup dan pengakhiran, program sepenuhnya terikat CPU. Tugas Anda adalah meningkatkan kinerja aplikasi ini dengan multithreading. Aplikasi berjalan pada sistem yang menggunakan model threading one-to-one (setiap thread pengguna dipetakan ke thread kernel).

*Berapa banyak thread yang akan Anda buat untuk melakukan input dan output? Jelaskan.*
*Berapa banyak thread yang akan Anda buat untuk bagian aplikasi yang intensif CPU? Jelaskan.*


*Jawaban:*  
- *Input/Output:* Satu thread untuk input dan satu thread untuk output.  
- *CPU-intensif:* Empat thread, satu untuk setiap inti prosesor.  

---

### 4.17 Pertimbangkan segmen kode berikut:

c
pid_t pid;

pid = fork();

if (pid == 0) { /* proses anak */
    /* ... */
    exit(0);
}

/* proses induk */
/* ... */
wait(NULL);


*a. Berapa banyak proses unik yang dibuat?* 
a. Jumlah proses unik yang dibuat:* Kode ini membuat dua proses unik: satu proses induk dan satu proses anak yang dibuat oleh panggilan fork().
*b. Berapa banyak thread unik yang dibuat?*  
b. Jumlah thread unik yang dibuat:* Kode ini membuat satu thread unik di setiap proses. Proses induk memiliki thread utamanya, dan proses anak juga memiliki thread utamanya setelah fork(). Panggilan fork() menduplikasi ruang alamat dan thread eksekusi proses induk.



---

### 4.18 Jelaskan perbedaan mendasar antara thread level pengguna dan thread level kernel. Di bawah sistem operasi mana satu jenis thread mungkin lebih disukai daripada yang lain?

*Jawaban:*  
* Perbedaan Mendasar:
* Thread Level Pengguna: Dikelola oleh pustaka thread di ruang pengguna. Kernel tidak menyadari keberadaan thread ini. Peralihan antar thread level pengguna cepat karena tidak melibatkan intervensi kernel. Namun, jika satu thread level pengguna melakukan operasi pemblokiran, seluruh proses juga akan diblokir.
* Thread Level Kernel: Dikelola langsung oleh kernel. Kernel menjadwalkan thread-thread ini. Peralihan antar thread level kernel lebih lambat daripada thread level pengguna karena melibatkan intervensi kernel. Namun, jika satu thread level kernel melakukan operasi pemblokiran, thread lain dalam proses yang sama dapat terus berjalan.

* Sistem Operasi yang Lebih Memilih Satu Jenis:
* Thread Level Pengguna Lebih Disukai: Pada sistem operasi yang tidak mendukung multithreading tingkat kernel secara efisien atau di mana kinerja peralihan thread sangat kritis dan pemblokiran I/O jarang terjadi atau dapat dikelola oleh pengguna (misalnya, menggunakan I/O asinkron).
* Thread Level Kernel Lebih Disukai: Pada sistem operasi modern yang mendukung multithreading tingkat kernel dengan baik, terutama pada sistem multiprosesor di mana paralelisme sejati dapat dicapai. Thread level kernel juga lebih unggul dalam menangani situasi di mana satu thread melakukan operasi pemblokiran tanpa memengaruhi seluruh proses.

---

### 4.19 Program yang ditunjukkan pada Gambar 4.23 menggunakan Pthreads. Apa yang akan menjadi output dari program tersebut?

*Jawaban:* 


---

### 4.20 Pertimbangkan implikasi kinerja dari model many-to-many dan model one-to-one untuk sistem multithreaded. Dalam keadaan apa model many-to-many mungkin memberikan kinerja yang lebih baik daripada jumlah thread pengguna yang lebih besar daripada jumlah inti pemrosesan? Jelaskan implikasi kinerja dari skenario berikut:

*Jawaban:*  
a.	Jumlah thread yang dialokasikan ke proses kurang dari jumlah inti pemrosesan.
Ini dapat menyebabkan kurangnya pemanfaatan sumber daya CPU. Beberapa inti pemrosesan mungkin menganggur meskipun ada thread level pengguna yang siap dijalankan. Kinerja paralel mungkin tidak optimal.
b.	Jumlah thread kernel yang dialokasikan ke proses sama dengan jumlah inti pemrosesan.
Ini berpotensi memberikan kinerja terbaik untuk aplikasi terikat CPU dalam model one-to-one. Setiap thread kernel dapat berjalan secara paralel pada inti yang berbeda, memaksimalkan pemanfaatan CPU.
c.	Jumlah thread kernel yang dialokasikan ke proses lebih besar daripada jumlah thread level pengguna.
* c. Jumlah thread kernel lebih besar daripada jumlah thread level pengguna: Ini dapat menyebabkan overhead penjadwalan kernel yang tidak perlu. Kernel harus mengelola lebih banyak thread daripada yang benar-benar digunakan oleh aplikasi secara bersamaan. Sumber daya kernel mungkin terbuang untuk mengelola thread-thread tambahan ini tanpa memberikan manfaat paralelisme tambahan.

---

### 4.21 Pthreads menyediakan API untuk pembatalan thread Fungsi pthread_setcancelstate() digunakan untuk mengatur status pembatalan thread. Prototipe fungsinya muncul sebagai berikut:

c
int pthread_setcancelstate(int state, int *oldstate);

Dua nilai yang mungkin untuk state adalah PTHREAD_CANCEL_ENABLE dan PTHREAD_CANCEL_DISABLE. Jelaskan mengapa aplikasi mungkin ingin menonaktifkan pembatalan thread untuk bagian kode tertentu. Berikan contoh dua operasi yang mungkin tidak aman untuk dibatalkan.

1.  Memperbarui Struktur Data Bersama: Jika sebuah thread sedang memperbarui struktur data yang diakses oleh thread lain (misalnya, linked list, tabel hash), pembatalan di tengah-tengah operasi ini dapat meninggalkan struktur data dalam keadaan rusak. Thread lain yang mencoba mengakses struktur data ini mungkin mengalami perilaku yang tidak benar atau bahkan crash. Untuk mencegah hal ini, pembatalan thread dapat dinonaktifkan selama bagian kode yang memodifikasi struktur data bersama, dan diaktifkan kembali setelah modifikasi selesai. Mekanisme sinkronisasi seperti mutex atau kunci biasanya digunakan bersamaan dengan penonaktifan pembatalan untuk memastikan akses eksklusif dan penyelesaian operasi kritis.

2.  Operasi I/O Kritis: Beberapa operasi input/output mungkin melibatkan beberapa langkah atau transfer data yang harus diselesaikan secara atomik. Misalnya, menulis blok data ke disk atau mengirim serangkaian paket jaringan. Jika sebuah thread dibatalkan di tengah-tengah operasi I/O seperti itu, data mungkin tertulis sebagian atau koneksi jaringan mungkin tertinggal dalam keadaan tidak stabil. Ini dapat menyebabkan kehilangan data, kerusakan file, atau masalah komunikasi. Menonaktifkan pembatalan selama operasi I/O kritis dan memastikan penyelesaian atau rollback yang tepat dapat mencegah masalah ini.
3.  Dalam kedua contoh ini, menonaktifkan pembatalan thread memberikan jaminan bahwa operasi penting akan diselesaikan tanpa gangguan, menjaga konsistensi dan keandalan program. Setelah bagian kode kritis selesai, aplikasi harus mengaktifkan kembali pembatalan thread untuk memungkinkan thread merespons permintaan pembatalan di lain waktu.

---

## 4.22 Program Multithreaded Menghitung Statistik

**Deskripsi:**
Program ini menerima daftar angka dari argumen baris perintah, lalu menggunakan tiga thread untuk menghitung nilai rata-rata, minimum, dan maksimum.

```c
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>

int average, minimum, maximum;
int *numbers;
int count;

void* calculate_average(void* arg) {
    int sum = 0;
    for (int i = 0; i < count; i++) sum += numbers[i];
    average = sum / count;
    pthread_exit(0);
}

void* calculate_minimum(void* arg) {
    minimum = numbers[0];
    for (int i = 1; i < count; i++)
        if (numbers[i] < minimum) minimum = numbers[i];
    pthread_exit(0);
}

void* calculate_maximum(void* arg) {
    maximum = numbers[0];
    for (int i = 1; i < count; i++)
        if (numbers[i] > maximum) maximum = numbers[i];
    pthread_exit(0);
}

int main(int argc, char *argv[]) {
    if (argc < 2) {
        printf("Gunakan: %s angka1 angka2 ...\n", argv[0]);
        return 1;
    }

    count = argc - 1;
    numbers = (int*) malloc(count * sizeof(int));
    for (int i = 0; i < count; i++) numbers[i] = atoi(argv[i + 1]);

    pthread_t tid1, tid2, tid3;
    pthread_create(&tid1, NULL, calculate_average, NULL);
    pthread_create(&tid2, NULL, calculate_minimum, NULL);
    pthread_create(&tid3, NULL, calculate_maximum, NULL);

    pthread_join(tid1, NULL);
    pthread_join(tid2, NULL);
    pthread_join(tid3, NULL);

    printf("Nilai rata-rata adalah %d\n", average);
    printf("Nilai minimum adalah %d\n", minimum);
    printf("Nilai maksimum adalah %d\n", maximum);

    free(numbers);
    return 0;
}
```
![nomor 22](https://github.com/Nabillatunnafista/SisOp2025/blob/585f070dafc3dc005b94e889104693a93d2d0060/pertemuan%20ke%207/gambar/gambar%20single%20dan%20multi%20thread.png)

---

## 4.23 Program Multithreaded Menentukan Bilangan Prima

**Deskripsi:**
Program menerima angka dari pengguna dan mencetak semua bilangan prima yang kurang dari atau sama dengan angka tersebut dalam thread terpisah.

```c
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>
#include <stdbool.h>

int batas;

bool is_prime(int num) {
    if (num < 2) return false;
    for (int i = 2; i * i <= num; i++)
        if (num % i == 0) return false;
    return true;
}

void* cari_prima(void* arg) {
    printf("Bilangan prima <= %d:\n", batas);
    for (int i = 2; i <= batas; i++)
        if (is_prime(i)) printf("%d ", i);
    printf("\n");
    pthread_exit(0);
}

int main(int argc, char *argv[]) {
    if (argc != 2) {
        printf("Gunakan: %s bilangan\n", argv[0]);
        return 1;
    }

    batas = atoi(argv[1]);
    pthread_t thread;
    pthread_create(&thread, NULL, cari_prima, NULL);
    pthread_join(thread, NULL);

    return 0;
}
```
![nomor 23](https://github.com/Nabillatunnafista/SisOp2025/blob/585f070dafc3dc005b94e889104693a93d2d0060/pertemuan%20ke%207/gambar/gambar%20single%20dan%20multi%20thread.png)

---

## 4.24 Estimasi Nilai Pi dengan Monte Carlo (Multithreaded)

**Deskripsi:**
Program menggunakan metode Monte Carlo untuk memperkirakan nilai Pi dengan thread-thread yang menghasilkan titik acak.

```c
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>
#include <time.h>

int total_poin = 0;
int poin_dalam_lingkaran = 0;
pthread_mutex_t lock;

void* hitung_pi(void* arg) {
    int jumlah_poin = *((int*)arg);
    int hitung_dalam = 0;
    double x, y;

    for (int i = 0; i < jumlah_poin; i++) {
        x = (double)rand() / RAND_MAX * 2.0 - 1.0;
        y = (double)rand() / RAND_MAX * 2.0 - 1.0;
        if (x * x + y * y <= 1.0) hitung_dalam++;
    }

    pthread_mutex_lock(&lock);
    poin_dalam_lingkaran += hitung_dalam;
    pthread_mutex_unlock(&lock);

    pthread_exit(0);
}

int main(int argc, char *argv[]) {
    if (argc != 3) {
        printf("Gunakan: %s <jumlah_poin> <jumlah_thread>\n", argv[0]);
        return 1;
    }

    total_poin = atoi(argv[1]);
    int jumlah_thread = atoi(argv[2]);

    pthread_t threads[jumlah_thread];
    int poin_per_thread = total_poin / jumlah_thread;

    srand(time(NULL));
    pthread_mutex_init(&lock, NULL);

    for (int i = 0; i < jumlah_thread; i++)
        pthread_create(&threads[i], NULL, hitung_pi, &poin_per_thread);

    for (int i = 0; i < jumlah_thread; i++)
        pthread_join(threads[i], NULL);

    double pi = 4.0 * (double)poin_dalam_lingkaran / total_poin;
    printf("Estimasi nilai Pi = %.6f\n", pi);

    pthread_mutex_destroy(&lock);
    return 0;
}
```
![nomor 24](https://github.com/Nabillatunnafista/SisOp2025/blob/585f070dafc3dc005b94e889104693a93d2d0060/pertemuan%20ke%207/gambar/gambar%20single%20dan%20multi%20thread.png)

---

## 4.25 Estimasi Nilai Pi dengan OpenMP

**Deskripsi:**
Versi alternatif dari soal 4.24, tetapi menggunakan OpenMP untuk paralelisasi alih-alih menggunakan thread secara manual.

```c
#include <stdio.h>
#include <stdlib.h>
#include <omp.h>
#include <time.h>

int main(int argc, char *argv[]) {
    if (argc != 3) {
        printf("Gunakan: %s <jumlah_poin> <jumlah_thread>\n", argv[0]);
        return 1;
    }

    int total_poin = atoi(argv[1]);
    int jumlah_thread = atoi(argv[2]);
    int poin_dalam_lingkaran = 0;

    double start_time = omp_get_wtime();

    #pragma omp parallel num_threads(jumlah_thread)
    {
        unsigned int seed = time(NULL) ^ omp_get_thread_num();

        #pragma omp for reduction(+:poin_dalam_lingkaran)
        for (int i = 0; i < total_poin; i++) {
            double x = (double)rand_r(&seed) / RAND_MAX * 2.0 - 1.0;
            double y = (double)rand_r(&seed) / RAND_MAX * 2.0 - 1.0;
            if (x * x + y * y <= 1.0) poin_dalam_lingkaran++;
        }
    }

    double pi = 4.0 * poin_dalam_lingkaran / total_poin;
    double end_time = omp_get_wtime();

    printf("Estimasi nilai Pi     = %.6f\n", pi);
    printf("Titik dalam lingkaran = %d\n", poin_dalam_lingkaran);
    printf("Total titik           = %d\n", total_poin);
    printf("Jumlah thread         = %d\n", jumlah_thread);
    printf("Waktu eksekusi (s)    = %.6f\n", end_time - start_time);

    return 0;
}
```
![nomor 25](https://github.com/Nabillatunnafista/SisOp2025/blob/585f070dafc3dc005b94e889104693a93d2d0060/pertemuan%20ke%207/gambar/gambar%20single%20dan%20multi%20thread.png)

---









