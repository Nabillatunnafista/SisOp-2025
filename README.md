## NABILLATUN NAFISTA (3124521027) SISTEM OPERASI

## SISTEM BILANGAN
## 1. a. Bilangan biner adalah bilangan yang berbasis (**dua**).

## 2. Konversi Bilangan Desimal ke Biner
**Soal:**
Konversikan bilangan desimal di bawah ini ke dalam bilangan biner:
a. **1234₁₀**

**Jawab:**
```
1234  : 2 = 617  sisa 0
617   : 2 = 308  sisa 1
308   : 2 = 154  sisa 0
154   : 2 = 77   sisa 0
77    : 2 = 38   sisa 1
38    : 2 = 19   sisa 0
19    : 2 = 9    sisa 1
9     : 2 = 4    sisa 1
4     : 2 = 2    sisa 0
2     : 2 = 1    sisa 0
1     : 2 = 0    sisa 1
```
### Membaca hasil dari bawah ke atas:
### **1234₁₀ = 10011010010₂**
---
## 3. Konversi Bilangan Biner ke Desimal

### Soal:
Konversikan bilangan biner di bawah ini ke dalam bilangan desimal:

a. **10101010**

### Jawaban:
| Bit | Pangkat| Perhitungan | Hasil |
|-----|--------|-------------|-------|
| 0   | 2⁰     | 0 × 1       | 0     |
| 1   | 2¹     | 1 × 2       | 2     |
| 0   | 2²     | 0 × 4       | 0     |
| 1   | 2³     | 1 × 8       | 8     |
| 0   | 2⁴     | 0 × 16      | 0     |
| 1   | 2⁵     | 1 × 32      | 32    |
| 0   | 2⁶     | 0 × 64      | 0     |
| 1   | 2⁷     | 1 × 128     | 128   |

### Hasil:
**10101010₂ = 170₁₀**

### 4. Konversi Bilangan Biner ke Oktal
#### Soal:
Konversikan bilangan biner di bawah ini ke dalam bilangan oktal:

a. **101011111001₂**

#### Jawaban:
Pisahkan tiap 3 bit dari kanan:
```
101 | 011 | 111 | 001
```
Lalu konversi setiap kelompok ke oktal:
```
101₂ = 5₈
011₂ = 3₈
111₂ = 7₈
001₂ = 1₈
```
Jadi, **101011111001₂ = 5371₈**

---

### 5. Konversi Bilangan Oktal ke Biner
#### Soal:
Konversikan bilangan oktal di bawah ini ke dalam bilangan biner:

a. **2170₈**

#### Jawaban:
Setiap digit oktal dikonversi ke 3 bit biner:
```
2 = 010
1 = 001
7 = 111
0 = 000
```
Jadi, **2170₈ = 010001111000₂**

---

### 6. Konversi Bilangan Desimal ke Heksadesimal
#### Soal:
Konversikan bilangan desimal di bawah ini ke dalam bilangan heksadesimal:

a. **1780₁₀**

#### Jawaban:
Pembagian berturut-turut dengan 16:
```
1780 ÷ 16 = 111, sisa 4 (4)
111 ÷ 16 = 6, sisa 15 (F)
6 ÷ 16 = 0, sisa 6 (6)
```
Jadi, **1780₁₀ = 06F4₁₆**

---

### 7. Konversi Bilangan Heksadesimal ke Desimal
#### Soal:
Konversikan bilangan heksadesimal di bawah ini ke dalam bilangan desimal:

a. **ABCD₁₆**

#### Jawaban:
```
A × 16³ = 10 × 4096 = 40960
B × 16² = 11 × 256 = 2816
C × 16¹ = 12 × 16 = 192
D × 16⁰ = 13 × 1 = 13
```
Jumlahkan hasilnya:
```
40960 + 2816 + 192 + 13 = 43981
```
Jadi, **ABCD₁₆ = 43981₁₀**

---

### 8. Konversi Bilangan Pecahan Desimal ke Biner
#### Soal:
Konversikan bilangan pecahan desimal di bawah ini ke dalam bilangan biner:

a. **0,3125₁₀**

#### Jawaban:
Mengalikan pecahan dengan 2 secara berturut-turut:
```
0.3125 × 2 = 0, sisa 0.625
0.625 × 2 = 1, sisa 0.25
0.25 × 2 = 0, sisa 0.5
0.5 × 2 = 1, sisa 0
```
Baca hasil dari atas ke bawah:
```
0.3125₁₀ = 0.0101₂
```

---

### 9. Konversi Bilangan Desimal ke Biner
#### Soal:
Konversikan bilangan desimal di bawah ini ke dalam bilangan biner:

a. **11,625₁₀**

#### Jawaban:
Konversi bagian bilangan bulat:
```
11 ÷ 2 = 5, sisa 1
5 ÷ 2 = 2, sisa 1
2 ÷ 2 = 1, sisa 0
1 ÷ 2 = 0, sisa 1
```
Konversi bagian pecahan:
```
0.625 × 2 = 1, sisa 0.25
0.25 × 2 = 0, sisa 0.5
0.5 × 2 = 1, sisa 0
```
Gabungkan hasilnya:
```
11,625₁₀ = 1011.101₂
```

---

### 10. Konversi Bilangan Desimal ke Heksadesimal
#### Soal:
Konversikan bilangan desimal di bawah ini ke dalam bilangan heksadesimal:

a. **348,654₁₀**

#### Jawaban:
Konversi bagian bilangan bulat:
```
348 ÷ 16 = 21, sisa 12 (C)
21 ÷ 16 = 1, sisa 5 (5)
1 ÷ 16 = 0, sisa 1 (1)
```
Konversi bagian pecahan:
```
0.654 × 16 = 10, sisa 0.464 (A)
0.464 × 16 = 7, sisa 0.424 (7)
0.424 × 16 = 6, sisa 0.784 (6) ( dibulatkan 8)
```
Gabungkan hasilnya:
```
348,654₁₀ = 15C.A78₁₆
```
### 11. Konversi Bilangan Biner ke Desimal
#### Soal:
Konversikan bilangan di bawah ini ke dalam bilangan desimal:

a. **010100011,001111101₂**

#### Jawaban:
Bilangan bulat:
```
010100011₂ = 163₁₀
```
Bilangan pecahan:
```
001111101₂ = 0.244140625₁₀
```
Jadi,
```
010100011,001111101₂ = 163.244140625₁₀
```

---

### 12. Konversi Bilangan Biner ke BCD
#### Soal:
Konversikan bilangan biner di bawah ini ke dalam bentuk BCD:

a. **1010011000011₂**

#### Jawaban:
Pisahkan tiap 4 digit dari kanan, tambah 0 di depan:
```
0010 | 1001 | 1000 | 0111
```
Dikonversi ke desimal:
```
2 | 9 | 8 | 7
```
Jadi,
```
1010011000011₂ = 2987 (BCD)
```

---

### 13. Konversi BCD ke Biner
#### Soal:
Konversikan bentuk BCD di bawah ini ke dalam bilangan biner:

a. **1987 (BCD)**

#### Jawaban:
Setiap digit BCD dikonversi ke biner:
```
1 = 0001
9 = 1001
8 = 1000
7 = 0111
```
Jadi, 1987 (BCD) = 1 1001 1000 0111₂
```
```
### 14. Konversi Bilangan Biner ke BCO
**Soal:**
11111101001₂

**Jawab:**
Pisahkan setiap 3 digit dari kanan, tambahkan 0 dua di depan:
```
011 = 3
111 = 7
101 = 5
001 = 1
```
Jadi, hasilnya **3751**

---

### 15. Konversi Bilangan Biner ke BCH
**Soal:**
1101111100101110₂

**Jawab:**
Pisahkan setiap 4 digit dari kanan:
```
1101 = D
1111 = F
0010 = 2
1110 = E
```
Jadi, hasilnya **CF2E** dalam sistem heksadesimal.

---

### 16. Konversi BCH ke Bilangan Heksadesimal
**Soal:**
F0DE

**Jawab:**
Ubah ke bentuk biner:
```
F = 1111
0 = 0000
D = 1101
E = 1110
```
Jadi, **1111 0000 1101 1110** dalam biner adalah **F0DE** dalam heksadesimal.

---

### 17. Menentukan Bilangan Positif atau Negatif dari Biner
**Soal:**
01111111

**Jawab:**
- MSB (Most Significant Bit) adalah **0**.
- Ini adalah bilangan **positif**.
- Nilai desimalnya adalah **127**.

Jadi, **bilangan biner 01111111 adalah Positif (127).**

---

### 18. Konversi Bilangan Biner Negatif ke Desimal
**Soal:**
10001000

**Jawab:**
- Invers bit: `01110111`
- Tambahkan 1: `01111000`
- Konversi ke desimal:
```
01111000₂ = (0 * 2⁷) + (1 * 2⁶) + (1 * 2⁵) + (1 * 2⁴) + (1 * 2³) + (0 * 2²) + (0 * 2¹) + (0 * 2⁰)
           = 0 + 64 + 32 + 16 + 8 + 0 + 0 + 0
           = 120
```
Karena bilangan awal negatif, maka hasilnya adalah **-120**.
---

### 19. Konversi ASCII Code ke Karakter
**Soal:**
41₁₆

**Jawab:**
```
41₁₆ = A
```
Jadi, hasilnya **A**

---

### 20. Konversi Karakter ke ASCII Code
**Soal:**
a

**Jawab:**
```
a = 61₁₆
```
Jadi, hasilnya **61₁₆**

---

### 21. Menampilkan Keluaran ASCII di Keyboard
**Soal:**
Perintah PRINT X

**Jawab:**
Karakter (8-bit biner):
```
P  : 1010000₂  
R  : 1010010₂  
I  : 1001001₂  
N  : 1001110₂  
T  : 1010100₂  
(spasi) : 0100000₂  
X  : 1011000₂  
```
