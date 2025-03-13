# SISTEM OPERASI
Tugas mata kuliah Sistem Operasi pertemuan ketiga yang disusun oleh Nabillatun Nafista dengan NRP. 3124521027 dari kelas 1 TI-A

## Flowchart Proses Booting Komputer

**Buat flowchart untuk proses dari komputer dinyalakan, bootstrap, hingga komputer bisa digunakan.**

### Flowchart
![Image Alt](https://github.com/Nabillatunnafista/SisOp-2025/blob/6a5fa1bf11f5e8a92ef89b791d242c9293c1343c/SO_flowchart_week3.drawio.png)

## **Penjelasan Tahapan**

| No  | Tahapan                                   | Deskripsi |
|----|--------------------------------------|-----------|
| 1.  | **Mulai (Power On)**                  | Proses dimulai ketika tombol power komputer ditekan. |
| 2.  | **Load BIOS/UEFI dari NVRAM**         | Sistem memuat BIOS (Basic Input/Output System) atau UEFI (Unified Extensible Firmware Interface) dari Non-Volatile Random-Access Memory (NVRAM). Ini adalah firmware yang menginisialisasi perangkat keras. |
| 3.  | **Probe untuk Hardware**              | BIOS/UEFI mendeteksi dan menginisialisasi perangkat keras seperti CPU, memori, dan perangkat penyimpanan. |
| 4.  | **Pilih Boot Device**                 | BIOS/UEFI menentukan perangkat mana yang akan digunakan untuk boot (misalnya, hard disk, USB, atau jaringan). |
| 5.  | **Identifikasi EFI System Partition (jika ada)** | Jika sistem menggunakan UEFI, ia mencari partisi sistem EFI (Extensible Firmware Interface). |
| 6.  | **Load Boot Loader**                   | Boot loader (misalnya, GRUB) dimuat dari perangkat boot. Boot loader bertanggung jawab untuk memuat kernel sistem operasi. |
| 7.  | **Tentukan Kernel yang akan di-boot**  | Boot loader menentukan kernel mana yang akan dimuat (jika ada beberapa pilihan). |
| 8.  | **Load Kernel**                        | Kernel sistem operasi dimuat ke memori. |
| 9.  | **Mulai init/systemd sebagai PID 1**   | Kernel memulai proses init atau systemd sebagai proses pertama (PID 1). Ini adalah proses yang mengelola proses lain dalam sistem. |
| 10. | **Jalankan Startup Scripts/Unit Files** | init atau systemd menjalankan skrip startup atau unit files untuk menginisialisasi layanan dan aplikasi sistem. |
| 11. | **Login Prompt (TTY/GUI)**             | Sistem menampilkan antarmuka login (mode teks TTY atau GUI seperti GDM, SDDM, LightDM, dll.). |
| 12. | **(Running System)**                   | Sistem operasi sepenuhnya berjalan dan siap digunakan. |
| 13. | **System Ready**                       | Sistem siap digunakan dan proses booting selesai. |

---

[Nabillatun Nafista 3124521027 ]
