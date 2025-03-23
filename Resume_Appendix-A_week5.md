# SISTEM OPERASI
Tugas mata kuliah Sistem Operasi pertemuan kelima yang disusun oleh Nabillatun Nafista dengan NRP. 3124521027 dari kelas 1 Teknik Informatika-A

## TUGAS RESUME SISTEM OPERASI
## Sistem Operasi Yang Berpengaruh (Influential Operating System)

## A.1 Migrasi Fitur
Fitur yang awalnya hanya tersedia pada sistem besar seperti mainframe, kini telah diadopsi oleh sistem yang lebih kecil, termasuk komputer mini, mikro, dan perangkat genggam. Sebagai contoh utama, sistem operasi MULTICS yang dikembangkan antara 1965 hingga 1970 di MIT untuk komputer mainframe GE-645, menjadi dasar bagi pengembangan UNIX oleh Bell Laboratories pada tahun 1970 untuk komputer mini PDP-11. 
Pada 1980-an, fitur dari UNIX diadopsi oleh sistem operasi untuk komputer mikro, termasuk Microsoft Windows, Windows XP, dan macOS. Linux, yang juga mengadopsi banyak fitur serupa, kini dapat ditemukan di berbagai perangkat, termasuk PDA.

## A.2 Sistem Awal
Sejarah komputer modern dimulai pada abad ke-20 dengan pengembangan konsep komputer program tersimpan oleh Alan Turing dan John von Neumann. Pada 1949, Manchester Mark 1 menjadi komputer program tersimpan pertama yang berfungsi, diikuti oleh Ferranti Mark 1 pada 1951 sebagai komputer komersial pertama. Komputer awal berukuran besar, dioperasikan manual dengan sakelar, pita kertas, atau kartu berlubang, dan debugging dilakukan langsung dari konsol. Output dicetak atau disimpan untuk pemrosesan lebih lanjut.
### A.2.1 Perkembangan Perangkat Keras dan Perangkat Lunak
Perkembangan perangkat keras dan perangkat lunak mengarah pada penggunaan perangkat I/O seperti pembaca kartu, printer, dan pita magnetik. Pemrograman dipermudah dengan alat seperti perakit, loader, dan kompiler (FORTRAN, COBOL), tetapi proses kompilasi, perakitan, dan pemuatan ke memori memperlambat eksekusi. Kesalahan dalam proses ini menyebabkan pemborosan waktu dan mengakibatkan CPU menganggur, memaksa pemilik komputer untuk mengoptimalkan penggunaannya.
### A.2.2 Sistem Batch
Untuk meningkatkan efisiensi, pekerjaan dikelompokkan dalam sistem batch untuk mengurangi waktu penyiapan dan pengaturan ulang. Debugging dilakukan dari dump memori dan register. Untuk mencegah CPU menganggur, pengurutan pekerjaan otomatis dengan monitor residen diterapkan, yang mentransfer kontrol antar pekerjaan menggunakan kartu kontrol, penerjemah, loader, dan driver perangkat.
### A.2.3 Overlapped I/O
Pada 1950-an dan 1960-an, solusi I/O menggantikan pembaca kartu dan printer lambat dengan unit pita magnetik, mengurangi beban komputer utama dan meningkatkan kecepatan pemrosesan. Spooling memungkinkan pemrosesan data jarak jauh tanpa intervensi CPU, meningkatkan efisiensi dengan menumpang-tindihkan I/O satu pekerjaan dengan komputasi pekerjaan lain. Teknik ini menjaga CPU dan perangkat I/O tetap aktif, serta menjadi dasar multiprogramming dalam sistem operasi modern.

## A.3 Atlas
Sistem operasi Atlas, yang dikembangkan pada akhir 1950-an dan awal 1960-an, memperkenalkan fitur inovatif seperti manajemen memori dengan drum sebagai memori utama dan penggunaan demand paging untuk transfer otomatis data. Algoritma penggantian halaman mengoptimalkan penggunaan memori dengan memprediksi halaman yang akan digunakan. Sistem ini juga mengandalkan spooling untuk pengaturan pekerjaan.
Sistem XDS-940, yang merupakan pengembangan dari XDS-930, mencakup fitur-fitur baru seperti mode monitor pengguna dan instruksi sistem untuk operasi I/O dan kontrol sistem. Sistem ini mendukung pengelolaan sumber daya, pembuatan subproses, serta komunikasi dan sinkronisasi antar proses menggunakan model pohon.

## A.4 XDS-940
Sistem operasi XDS-940, dikembangkan di Universitas California, Berkeley pada 1960-an, adalah sistem time-sharing dengan paging untuk relokasi memori. Memori virtual pengguna 16 KB dan memori fisik 64 KB. Sistem ini mendukung berbagi memori antarproses menggunakan kode reentrant read-only. XDS-940 menambahkan mode monitor pengguna dan instruksi khusus, serta menggunakan panggilan sistem untuk pengelolaan sumber daya. Sistem ini juga memungkinkan pembuatan subproses dalam struktur pohon dan komunikasi antarproses.

## A.5 THE
Sistem operasi THE, dirancang di Belanda pada tahun 1960-an, adalah sistem batch yang terkenal dengan desain berlapis dan penggunaan semaphore. Sistem ini menggunakan penjadwalan CPU prioritas, manajemen memori paging perangkat lunak, dan algoritma bankir untuk penghindaran kebuntuan. Sistem Venus, yang terinspirasi oleh THE, menggunakan struktur berlapis dan semaphore tetapi diimplementasikan dalam mikrokode untuk kecepatan yang lebih tinggi dan mendukung pembagian waktu.

## A.6 RC 4000
Sistem RC 4000, dikembangkan oleh Regnecentralen pada 1960-an, adalah kernel fleksibel dengan struktur berlapis yang mendukung proses bersamaan dan penjadwalan CPU round-robin. Komunikasi antarproses menggunakan sistem pesan berbasis buffer dengan pesan berukuran tetap. Terdapat operasi atomik untuk pengiriman pesan dan sinkronisasi, serta primitif tambahan untuk fleksibilitas. Perangkat I/O diperlakukan sebagai proses dengan driver perangkat menangani interupsi dan register sebagai pesan.

## A.7 CTSS
Compatible Time-Sharing System (CTSS), dikembangkan di MIT pada 1961 untuk IBM 7090, adalah sistem time-sharing eksperimental yang mendukung hingga 32 pengguna interaktif. Dengan memori 32 KB, CTSS menukar citra memori pengguna antara RAM dan drum cepat. Penjadwalan CPU menggunakan antrean umpan balik bertingkat, di mana kuantum waktu program bertambah dua kali lipat setiap kali tidak selesai dalam satu siklus.
CTSS berhasil besar dan digunakan hingga 1972, membuktikan pentingnya sistem time-sharing. Pengembangan CTSS juga berkontribusi pada kemajuan sistem time-sharing lainnya, serta pengembangan MULTICS (Multiplexed Information and Computing Service).

## A.8 MULTICS
MULTICS (1965–1970) dikembangkan oleh MIT, GE, dan Bell Labs sebagai penerus CTSS, dirancang sebagai sistem time-sharing terus-menerus dengan sistem berkas yang luas. Berjalan di GE 645, MULTICS menggunakan memori segmentasi-halaman dengan alamat virtual berbasis segmen 18-bit dan offset 16-bit, serta algoritma penggantian halaman kesempatan kedua.
Sistem berkasnya berbentuk pohon bertingkat, di mana setiap segmen adalah berkas yang dialamatkan berdasarkan nama. Penjadwalan CPU menggunakan antrean umpan balik bertingkat, dengan perlindungan berbasis daftar akses dan cincin perlindungan. Ditulis dalam PL/1 dengan 300.000 baris kode, MULTICS mendukung multiprosesor dan pemeliharaan CPU tanpa menghentikan sistem.

## A.9 IBM OS/360
IBM memiliki sejarah panjang dalam pengembangan sistem operasi, dimulai dengan IBM 709 yang memperkenalkan fitur seperti subrutin I/O dan proteksi memori. IBM/360 bertujuan menyatukan berbagai tipe komputer, namun menghadapi tantangan kompleksitas dan efisiensi. Penambahan memori virtual pada IBM/370 menghasilkan OS/VS1 dan OS/VS2, yang berkembang menjadi MVS, meskipun tetap kompleks. Proyek seperti TSS/360 dan MULTICS gagal, tetapi pembagian waktu berhasil diimplementasikan melalui CMS dan MVS. Seiring berkembangnya komputer pribadi, kebutuhan akan sistem besar berkurang, membawa komputasi lebih dekat ke pengguna akhir.

## A.10 TOPS-20
DEC (Digital Equipment Corporation) memiliki peran penting dalam sejarah sistem operasi, terutama dengan VMS dan TOPS-20. TOPS-20, yang berawal dari proyek penelitian TENEX, menjadi sistem pembagian waktu yang populer karena fitur canggih dan harga terjangkau pada DECSYSTEM-20. Namun, DEC menghentikan pengembangan lini PDP-10 untuk fokus pada sistem VAX dan VMS. Meskipun TOPS-20 sangat berpengaruh, VMS tetap menjadi produk yang relevan hingga saat ini sebagai OpenVMS.

## A.11 CPM/M and MS/DOS
Komputer rumahan awal biasanya dirakit sendiri dan menjalankan satu program sekaligus. CP/M, yang dikembangkan oleh Gary Kindall, menjadi sistem operasi standar untuk komputer 1970-an. Ketika IBM memasuki pasar, mereka memilih MS-DOS, yang dikembangkan oleh Bill Gates. MS-DOS mirip dengan CP/M namun memiliki fitur lebih kaya dan menjadi sistem operasi komputer pribadi yang populer, meskipun terbatas dalam fitur modern seperti memori terlindungi.

## A.12 Sistem Operasi Macintosh dan Windows
Pada 1984, Apple Macintosh memperkenalkan GUI untuk pengguna rumahan, diikuti oleh peluncuran Microsoft Windows pada 1985 yang menggantikan Mac OS dengan lisensi yang lebih luas. Dengan munculnya CPU 32-bit dan fitur seperti memori terlindungi, kegunaan komputer pribadi meningkat. Persaingan antara Apple dan Microsoft berlanjut, dengan masing-masing merilis versi baru. Sementara sistem seperti AmigaOS dan OS/2 gagal, Linux semakin populer, terutama di kalangan pengguna teknis dan dalam proyek One Laptop per Child (OLPC).

## A.13 Mach
Sistem operasi Mach, yang berasal dari sistem Accent di Carnegie Mellon University pada 1980, dirancang untuk mendukung berbagai model memori dan komputasi paralel dengan kernel sederhana. Mach 3 memperkenalkan mikrokernel, memungkinkan eksekusi antarmuka sistem operasi di atasnya. Mach menjadi dasar OSF/1 pada 1989 dan mendukung multiprosesing serta komunikasi berbasis pesan. Kini, Mach digunakan dalam kernel XNU untuk macOS dan iOS, dengan dukungan berkelanjutan dari Apple.

## A.14 Sistem Berbasis Kemampuan-Hydra dan CAP
Bagian ini membahas dua sistem perlindungan berbasis kapabilitas, yang berbeda dalam hal kompleksitas dan kebijakan yang dapat diterapkan. Meskipun tidak ada yang digunakan secara luas, keduanya memberikan dasar yang menarik untuk pembuktian teori perlindungan.

### A.14.1 Hydra
Hydra adalah sistem perlindungan berbasis kapabilitas yang memungkinkan pengelolaan hak akses secara fleksibel, termasuk hak akses khusus seperti baca, tulis, dan eksekusi. Sistem ini mendukung kontrol akses rinci melalui kapabilitas dan amplifikasi hak, di mana prosedur tepercaya dapat bertindak atas nama proses lain dengan hak lebih tinggi, namun terbatas pada objek tertentu.

### A.14.2 Cambridge CAP System
Sistem Perlindungan CAP Cambridge menawarkan pendekatan perlindungan yang lebih sederhana dengan dua jenis kapabilitas: data (hak akses standar) dan perangkat lunak (ditafsirkan oleh prosedur terlindungi). Prosedur dapat memperkuat hak akses menggunakan mekanisme seal dan unseal. Meskipun menghemat sumber daya, CAP mengharuskan pemahaman mendalam tentang prinsip perlindungan karena tidak menyediakan pustaka prosedur siap pakai.

## A.15 Sistem Lainnya
Sistem operasi seperti MCP untuk komputer Burroughs, yang mendukung segmentasi dan beberapa CPU, serta SCOPE untuk CDC 6600, yang unggul dalam koordinasi dan sinkronisasi proses, menunjukkan tren perkembangan sistem operasi yang terus berubah. Sistem yang dirancang untuk tujuan tertentu sering digantikan oleh sistem operasi baru yang lebih canggih, mendukung perangkat keras terbaru, lebih mudah digunakan, dan lebih baik dalam pemasaran. Tren ini diperkirakan akan terus berlanjut.

---

[Nabillatun Nafista 3124521027 ]
