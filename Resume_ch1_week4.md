# SISTEM OPERASI
Tugas mata kuliah Sistem Operasi pertemuan keempat yang disusun oleh Nabillatun Nafista dengan NRP. 3124521027 dari kelas 1 Teknik Informatika-A

## TUGAS RESUME CHAPTER 1 SISTEM OPERASI
halaman 1.30 sampai halaman 1.40

### Transisi dari Mode Pengguna ke Mode Kernel
- Timer digunakan untuk mencegah perulangan tak terbatas atau proses yang menghabiskan sumber daya.
- Timer bekerja dengan menghitung mundur dari nilai yang ditentukan dan menghasilkan interupsi ketika mencapai nol.
- Sistem operasi mengatur penghitung timer dengan instruksi istimewa.
- Timer penting untuk penjadwalan proses, memungkinkan sistem operasi untuk mendapatkan kembali kendali.

### Manajemen Proses
- Sebuah proses adalah sebuah program yang sedang dieksekusi. Ia adalah sebuah unit kerja di dalam sistem.
- Program adalah entitas pasif, proses adalah entitas aktif.
- Proses memerlukan sumber daya seperti CPU, memori, I/O, dan file.
- Proses single-threaded memiliki satu program counter, sedangkan multi-threaded memiliki beberapa.
- Sistem operasi mengelola proses secara konkuren.

#### Aktivitas Manajemen Proses
Sistem operasi bertanggung jawab atas aktivitas berikut yang berhubungan dengan manajemen proses:
- Membuat dan menghapus proses pengguna dan sistem.
- Menangguhkan dan melanjutkan proses.
- Menyediakan mekanisme untuk sinkronisasi proses.
- Menyediakan mekanisme untuk komunikasi proses.
- Menyediakan mekanisme untuk penanganan kebuntuan.

### Manajemen Memori
#### Kebutuhan Memori
- Untuk menjalankan sebuah program, instruksi (semua atau sebagian) harus berada di memori.
- Data yang dibutuhkan oleh program (semua atau sebagian) juga harus berada di memori.
- Tujuannya adalah untuk mengoptimalkan pemanfaatan CPU dan respons komputer.

#### Aktivitas Manajemen Memori
- Melacak bagian memori yang digunakan.
- Memutuskan proses mana yang dipindahkan masuk dan keluar dari memori.
- Mengalokasikan dan mendealokasikan ruang memori.

### Manajemen Sistem Berkas
#### Fungsi
- Sistem operasi menyediakan tampilan logis yang seragam dari penyimpanan informasi.
- File diatur ke dalam direktori.
- Mengatur hak akses.

#### Aktivitas Manajemen Sistem Berkas
- Pembuatan dan penghapusan file dan direktori.
- Manipulasi file dan direktori.
- Pemetaan file ke penyimpanan sekunder.
- Backup data.

### Manajemen Penyimpanan Massal
- Disk digunakan untuk data yang tidak muat di memori utama atau data jangka panjang.
- Manajemen yang tepat sangat penting untuk kecepatan komputer.

#### Aktivitas OS meliputi:
- Mounting dan unmounting.
- Manajemen ruang kosong.
- Alokasi penyimpanan.
- Penjadwalan disk.
- Partisi.
- Perlindungan.
- Penyimpanan tersier (optik, pita magnetik) juga perlu dikelola.

### Caching
- Prinsip penting, dilakukan pada banyak tingkatan dalam komputer (di perangkat keras, sistem operasi, perangkat lunak).
- Informasi yang digunakan disalin dari penyimpanan yang lebih lambat ke penyimpanan yang lebih cepat untuk sementara.
- Penyimpanan yang lebih cepat (cache) diperiksa terlebih dahulu untuk menentukan apakah informasi ada di sana.
- Jika ada, informasi digunakan langsung dari cache (cepat).
- Jika tidak, data disalin ke cache dan digunakan di sana.
- Cache lebih kecil dari penyimpanan yang di-cache.
- Manajemen cache adalah masalah desain yang penting, termasuk ukuran cache dan kebijakan penggantian.

---

[Nabillatun Nafista 3124521027 ]
