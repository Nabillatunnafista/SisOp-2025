# SISTEM OPERASI # 

Nama  : Nabillatun Nafista  (3124521027)

Kelas : 1 Teknik Informatika - A

Tugas pertemuan ke-7  

---
### 4.1 Tiga Contoh Pemrograman di Mana Multithreading Memberikan Kinerja Lebih Baik

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
**Rumus**:

$$
\text{Speedup} = \frac{1}{(1-P) + \frac{P}{N}}
$$


- **P**: Proporsi program yang dapat diparalelkan (0.6)
- **N**: Jumlah inti prosesor

### a. Dua Inti Pemrosesan (N = 2)

$
\text{Speedup}_2 = \frac{1}{(1 - 0.6) + \frac{0.6}{2}} = \frac{1}{0.4 + 0.3} = \frac{1}{0.7} \approx 1.43
$

Jadi, dengan dua inti pemrosesan, aplikasi akan mendapatkan peningkatan kecepatan sekitar **1.43 kali**.

---

### b. Empat Inti Pemrosesan (N = 4)

$
\text{Speedup}_4 = \frac{1}{(1 - 0.6) + \frac{0.6}{4}} = \frac{1}{0.4 + 0.15} = \frac{1}{0.55} \approx 1.82
$

Jadi, dengan empat inti pemrosesan, aplikasi akan mendapatkan peningkatan kecepatan sekitar 1.82 kali.

---

### **4.3 Apakah server web multithread menunjukkan paralelisme tugas atau data?**

**Jawab:**  
Server web multithread menunjukkan **paralelisme tugas (task parallelism)**, bukan paralelisme data. Dalam konteks server web, setiap thread biasanya menangani permintaan (request) dari klien yang berbeda.  

Meskipun kode program yang dijalankan oleh setiap thread bisa sama (misalnya, mengambil halaman HTML atau memproses permintaan API), data yang diproses oleh setiap thread **berbeda** karena berasal dari klien yang berbeda pula.  

Oleh karena itu, multithreading di sini digunakan untuk menyelesaikan berbagai **tugas** secara bersamaan, bukan untuk memecah satu kumpulan data besar menjadi bagian-bagian kecil yang diproses secara paralel.

---

### **4.4 Apa dua perbedaan antara thread tingkat pengguna dan thread tingkat kernel? Dalam keadaan apa salah satu jenis thread lebih baik daripada thread lainnya?**

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

**Jawab:**  
**Ya**, thread real-time **perlu diikat (bound)** ke LWP.

### **Alasan:**
Dalam model **many-to-many**, beberapa thread tingkat pengguna dipetakan ke sejumlah terbatas LWP (Lightweight Process). Tanpa pengikatan, thread pengguna bisa berpindah-pindah antar LWP, yang tidak menjamin **determinisme waktu**—sesuatu yang sangat penting dalam sistem real-time.

### **Dengan Mengikat Thread Real-Time ke LWP:**
- Thread memiliki jalur eksekusi tetap ke kernel.
- Prioritas dan kebijakan penjadwalan real-time tetap berlaku.
- Menjamin **respons waktu yang konsisten dan dapat diprediksi**.

### **Tanpa Pengikatan:**
- Thread real-time bisa terpengaruh oleh thread lain di LWP yang sama.
- Tidak bisa menjamin waktu respons real-time yang diperlukan.

---







