# SISTEM INFORMASI (Fork : Parent - Child Process)
Tugas mata kuliah Sistem Operasi pertemuan ke enam yang disusun oleh Nabillatun Nafista dengan NRP. 3124521027 dari kelas 1 TI-A

---
`fork()` adalah mekanisme di sistem operasi Unix-like untuk membuat proses anak yang merupakan duplikat dari proses induk. Sistem operasi menyalin ruang alamat memori, deskriptor file, dan status eksekusi proses induk untuk menciptakan proses anak yang hampir identik. Setelah `fork()` berhasil, kedua proses melanjutkan eksekusi dari titik yang sama.

Implementasi `fork()` melibatkan alokasi ruang alamat baru untuk anak dan penyalinan data dari induk, dengan mekanisme **copy-on-write** untuk efisiensi. Fungsi `fork()` mengembalikan **PID anak** ke induk dan **0** ke anak, memungkinkan keduanya untuk membedakan peran dan menjalankan kode yang berbeda, yang menjadi fondasi untuk pemrograman paralel dan konkurensi.

```
$ ./fork01
```
![fork1]()
```
pid: [PID Proses Utama], ppid: [PPID Proses Utama]
[Main process]
    |
    +-------------------> Child process created <-------------------
    |                                                           |
    |                                                           |
pid: [PID Proses Utama], ppid: [PPID Proses Utama]      pid: [PID Proses Anak], ppid: [PID Proses Utama]
[Parent Process]                                        [Child Process]
```
Penjelasan fork01

```
$ ./fork02
```
![fork2]()
```
                                  [Proses Utama] (PID: ..., PPID: ...)
                                          |
                                          | fork()
                                          |
                        --------------------------------------
                        |                                    |
            [Proses Induk] (PID: ..., PPID: ...)   [Proses Anak] (PID: ..., PPID: ...)
                        |                                    |
                        | (Loop Tak Terbatas)                | (Loop Tak Terbatas)
                        |                                    |
                        | ... (Terus Berjalan)               | ... (Terus Berjalan)
```
Penjelasan fork02

```
$ ./fork03
```
![fork3]()
```
                                  [Proses Utama (fork03)] (PID: ..., PPID: ...)
                                          |
                                          | fork()
                                          |
                        --------------------------------------
                        |                                    |
            [Proses Induk (fork03)] (PID: ..., PPID: ...)   [Proses Anak (fork03)] (PID: ..., PPID: ...)
                        |                                    |
                        | (Loop 5 kali)                       | (Loop 5 kali)
                        |                                    |
                        | (Selesai)                           | (Selesai)
```
Penjelasan fork03

```
$ ./fork04
```
![fork4]()
```
                                               [Inisiasi Proses Utama]
                                    PID: [PID Proses Utama], PPID: [PPID Proses Utama]
                                        |
                        +-------------------- fork() dijalankan --------------------+
                        |                                                        |
                        |                                                        |
        [Proses Induk]                                                   [Proses Anak]
        PID: [PID Proses Utama], PPID: [PPID Proses Utama]                PID: [PID Proses Anak], PPID: [PID Proses Utama]
        cout << "I am the parent and my pid = ..."                      cout << "I am a child and my pid = ..."
        cout << "My child has pid = ..."                              cout << "My parent is ..."
        cout << "I am a happy, healthy process and my pid = ..."          cout << "I am a happy, healthy process and my pid = ..."
        cout << "I am a parent and I am going to wait ..."             cout << "I am a child and I am quitting work now!"
        |                                                              |
        (Menunggu proses anak selesai - wait())                      (Proses anak selesai/keluar)
        |
        cout << "I am a parent and I am quitting."
```
Penjelasan fork04

```
$ ./fork05
```
![fork5]()
```
                                          [Inisiasi Proses Utama]
                                    PID: [PID Induk], PPID: [PPID Induk]
                                        |
                        +-------------------- fork() dijalankan --------------------+
                        |                                                        |
                        |                                                        |
        [Proses Induk]                                                   [Proses Anak]
        PID: [PID Induk], PPID: [PPID Induk]                PID: [PID Anak], PPID: [PID Induk]
        cout << "I am the parent and my pid = ..."                      cout << "I am a child and my pid = ..."
        cout << "My child has pid = ..."                              execl("/bin/ls", "ls", "-l", "/home", NULL)
        cout << "I am a happy, healthy process and my pid = ..."      (Proses anak mengganti dirinya dengan program 'ls')
        cout << "I am a parent and I am going to wait ..."
        |
        (Menunggu proses anak selesai - wait())
        |
        cout << "I am a parent and I am quitting."
```
Penjelasan fork05

```
$ ./fork06
```
![fork6]()
```
                                  [Proses Utama (fork06)] (PID: ..., PPID: ...)
                                          |
                                          | fork()
                                          |
                        --------------------------------------
                        |                                    |
            [Proses Induk (fork06)] (PID: ..., PPID: ...)   [Proses Anak (fork03)] (PID: ..., PPID: ...)
                        |                                    |
                        | (Menunggu Anak)                     | (Menjalankan fork03)
                        |                                    |
                        | (Selesai setelah Anak selesai)      | (Selesai)
```
Penjelasan fork06
