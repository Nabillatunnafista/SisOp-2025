# SISTEM OPERASI
Tugas mata kuliah Sistem Operasi pertemuan ketiga yang disusun oleh Nabillatun Nafista dengan NRP. 3124521027 dari kelas 1 TI-A

## Flowchart Proses Booting Komputer

**Buat flowchart untuk proses dari komputer dinyalakan, bootstrap, hingga komputer bisa digunakan.**

### Flowchart
![Image Alt](https://github.com/Nabillatunnafista/SisOp-2025/blob/6ff271e38f04d457e48047de4956065b81e564c1/flowchart%20SO.drawio.png)

### Penjelasan Tahapan

| No  | Tahapan | Deskripsi |
|-----|---------|-----------|
| 1.  | **Komputer Dinyalakan** | Proses dimulai ketika tombol power komputer ditekan. Jajargenjang digunakan untuk menunjukkan awal atau akhir dari suatu proses. |
| 2.  | **CPU membaca BIOS/UEFI dari ROM di Motherboard** | CPU mengambil instruksi awal dari BIOS (Basic Input/Output System) atau UEFI (Unified Extensible Firmware Interface) yang tersimpan di ROM (Read-Only Memory) pada motherboard. |
| 3.  | **Jalankan BIOS/UEFI & Lakukan POST** (Power-On Self Test) | BIOS/UEFI menjalankan POST untuk memeriksa semua komponen hardware penting (CPU, RAM, dll.). |
| 4.  | **Apakah Hardware Error?** | Jika ya, tampilkan pesan error atau kode beep untuk memberi tahu pengguna tentang masalah tersebut. Jika tidak, lanjutkan ke langkah berikutnya. |
| 5.  | **Boot Device ditemukan?** | BIOS/UEFI mencari perangkat yang berisi sistem operasi. |
| 6.  | **Load Bootloader (MBR/GPT)** | Bootloader dimuat dari perangkat boot. |
| 7.  | **Bootloader Dieksekusi** | Bootloader dijalankan dan mulai memuat sistem operasi. |
| 8.  | **Multi-Boot Menu?** | Jika komputer memiliki lebih dari satu sistem operasi (multi-boot), bootloader akan menampilkan menu yang memungkinkan pengguna memilih sistem operasi yang ingin dijalankan. |
| 9.  | **User pilih OS** | Pengguna memilih sistem operasi yang ingin dijalankan. |
| 10. | **Load Kernel ke RAM** | Bootloader memuat kernel ke dalam RAM (Random Access Memory). |
| 11. | **Kernel inisialisasi: struktur data dan memori** | Kernel mulai menginisialisasi struktur data dan memori yang diperlukan untuk menjalankan sistem operasi. |
| 12. | **Load & Inisialisasi Driver (Hardware Drivers)** | Driver adalah perangkat lunak yang memungkinkan sistem operasi berkomunikasi dengan perangkat keras. |
| 13. | **Mount Root Filesystem** | Sistem file root (direktori utama) dari sistem operasi dipasang, sehingga file-file sistem dapat diakses. |
| 14. | **Spawn Proses init (systemd, init, dsb)** | Proses "init" (seperti systemd atau init) adalah proses pertama yang dijalankan oleh kernel. |
| 15. | **Jalankan Layanan & Daemon** | Layanan dan daemon (proses latar belakang) yang diperlukan oleh sistem operasi dijalankan. |
| 16. | **Tampilkan Login Screen (Display Manager/CLI)** | Layar login ditampilkan, memungkinkan pengguna untuk masuk ke sistem. |
| 17. | **User Login** | Pengguna memasukkan nama pengguna dan kata sandi untuk masuk. |
| 18. | **Muat Lingkungan Pengguna (Desktop/Shell)** | Lingkungan pengguna (desktop grafis atau shell baris perintah) dimuat. |
| 19. | **Sistem Siap digunakan** | Komputer siap digunakan. |

---


[Nabillatun Nafista 3124521027 ]
