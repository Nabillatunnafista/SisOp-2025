# SISTEM OPERASI (Fork : Parent - Child Process)
Tugas mata kuliah Sistem Operasi pertemuan ke enam yang disusun oleh Nabillatun Nafista dengan NRP. 3124521027 dari kelas 1 TI-A

---
`fork()` adalah mekanisme di sistem operasi Unix-like untuk membuat proses anak yang merupakan duplikat dari proses induk. Sistem operasi menyalin ruang alamat memori, deskriptor file, dan status eksekusi proses induk untuk menciptakan proses anak yang hampir identik. Setelah `fork()` berhasil, kedua proses melanjutkan eksekusi dari titik yang sama.

Implementasi `fork()` melibatkan alokasi ruang alamat baru untuk anak dan penyalinan data dari induk, dengan mekanisme **copy-on-write** untuk efisiensi. Fungsi `fork()` mengembalikan **PID anak** ke induk dan **0** ke anak, memungkinkan keduanya untuk membedakan peran dan menjalankan kode yang berbeda, yang menjadi fondasi untuk pemrograman paralel dan konkurensi.

```
$ ./fork01
```
![fork1](https://github.com/Nabillatunnafista/SisOp-2025/blob/272711753588e343414aaacffcc573b278177def/fork_week6_gambar/SO1.png)
```
                                [PID: [PID Proses Utama], PPID: [PPID Proses Utama]]
                                            [Main process]
                                                    |
                                    +-------------------> Child process created <-------------------+
                                    |                                                               |
                                    |                                                               |
    [PID: [PID Proses Utama], PPID: [PPID Proses Utama]]                      [PID: [PID Proses Anak], PPID: [PID Proses Utama]]
                    [Parent Process]           
```
Penjelasan fork01

fork() menciptakan proses anak yang merupakan duplikat proses induk, dengan salinan memori yang sama. Setelah fork(), induk dan anak berjalan bersamaan dengan PID yang berbeda (anak punya PID baru, PPID anak adalah PID induk), memungkinkan eksekusi kode secara independen.
```
$ ./fork02
```
![fork2](https://github.com/Nabillatunnafista/SisOp-2025/blob/272711753588e343414aaacffcc573b278177def/fork_week6_gambar/SO2.png)
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

Kode fork02.cpp punya loop while (1), yang artinya dia akan terus berjalan tanpa henti diulang-ulang terus setiap 2 detik, dengan nilai x yang terus bertambah. Jadi, kalau kita jalankan kode ini, outputnya akan terus muncul di layar sampai kita menghentikannya secara manual.
```
$ ./fork03
```
![fork3](https://github.com/Nabillatunnafista/SisOp-2025/blob/272711753588e343414aaacffcc573b278177def/fork_week6_gambar/SO3.png)
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

fork() menciptakan induk dan anak yang berjalan paralel. Keduanya melakukan loop 5 kali, mencetak PID dan tidur 2 detik, menghasilkan output bercampur.
```
$ ./fork04
```
![fork4](https://github.com/Nabillatunnafista/SisOp-2025/blob/272711753588e343414aaacffcc573b278177def/fork_week6_gambar/SO4.png)
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

fork() menciptakan proses anak. Anak mencetak info PID/PPID dan pesan "quitting". Induk mencetak info PID/anak PID, lalu menunggu anak selesai (wait()) sebelum mencetak pesan "quitting". Kedua proses mencetak pesan "happy, healthy".
```
$ ./fork05
```
![fork5](https://github.com/Nabillatunnafista/SisOp-2025/blob/272711753588e343414aaacffcc573b278177def/fork_week6_gambar/SO5.png)
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

fork() menciptakan anak. Anak mencetak info PID, lalu mengganti diri dengan perintah ls -l /home menggunakan execl(). Induk mencetak info PID/anak PID, lalu menunggu anak (yang kini adalah proses ls) selesai sebelum mencetak pesan "quitting". Proses "happy, healthy" dicetak oleh induk setelah fork().
```
$ ./fork06
```
![fork6](https://github.com/Nabillatunnafista/SisOp-2025/blob/272711753588e343414aaacffcc573b278177def/fork_week6_gambar/SO6.png)
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

Fungsi execl() mengganti kode yang sedang berjalan dengan kode dari program lain (fork03). Fungsi wait() membuat proses induk menunggu hingga proses anak selesai.

---

[Nabillatun Nafista 3124521027 ]
