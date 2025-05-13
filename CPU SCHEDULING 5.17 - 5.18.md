# SISTEM OPERASI # 

Nama  : Nabillatun Nafista  

NRP   : 3124521027

Kelas : Teknik Informatika - A
 
---
### 5.17 Consider the following set of processes, with the length of the CPU burst given in milliseconds:

| Process | Burst Time | Priority |
|---------|------------|----------|
| P1      | 5          | 4        |
| P2      | 3          | 1        |
| P3      | 1          | 2        |
| P4      | 7          | 2        |
| P5      | 4          | 3        |

The processes are assumed to have arrived in the order P1, P2, P3, P4, P5 all at time 0.

---

### a. Draw four Gantt charts that illustrate the execution of these processes using the following scheduling algorithms: FCS, SJF, non-preemptive priority, and RR (	q=2).

#### 1. FCFS (First Come First Served)
Urutan: P1, P2, P3, P4, P5  

| Proses | P1 | P2 | P3 | P4 | P5 | -  |
|--------|----|----|----|----|----|----|
| Waktu  | 0  | 5  | 8  | 9  | 16 | 20 |

#### 2. SJF (Shortest Job First)
Urutan berdasarkan burst time: P3 (1), P2 (3), P5 (4), P1 (5), P4 (7)

| Proses | P3 | P2 | P5 | P1 | P4 | -  |
|--------|----|----|----|----|----|----|
| Waktu  | 0  | 1  | 4  | 8  | 13 | 20 |

#### 3. Priority (Non-preemptive)
Urutan prioritas: P1, P5, P3, P4, P2

| Proses | P1 | P5 | P3 | P4 | P2 | -  |
|--------|----|----|----|----|----|----|
| Waktu  | 0  | 5  | 9  | 10 | 17 | 20 |

#### 4. Round Robin (Quantum = 2)

Urutan putaran berdasarkan antrian FIFO dengan quantum = 2.  
Proses: P1(5), P2(3), P3(1), P4(7), P5(4)

| Proses | P1 | P2 | P3 | P4 | P5 | P1 | P2 | P4 | P5 | P1 | P4 | P4 |
|--------|----|----|----|----|----|----|----|----|----|----|----|----|
| Waktu  | 0  | 2  | 4  | 5  | 7  | 9  | 11 | 12 | 14 | 16 | 17 | 19 | 21 |

---

### b. What is the turnaround time of each process for each of the scheduling algorithms in part a?

Turnaround Time = Waktu selesai - Waktu kedatangan

| Proses | FCFS | SJF | Priority | RR |
|--------|------|-----|----------|----|
| P1     | 5    | 13  | 5        | 20 |
| P2     | 8    | 20  | 20       | 21 |
| P3     | 9    | 1   | 10       | 7  |
| P4     | 16   | 20  | 17       | 19 |
| P5     | 20   | 8   | 13       | 16 |

---

### c. What is the waiting time of each process of these scheduling algorithms?

Waiting Time = Turnaround Time - Burst Time

| Proses | FCFS | SJF | Priority | Round Robin |
|--------|------|-----|----------|-------------|
| P1     | 0    | 8   | 0        | 15          |
| P2     | 5    | 17  | 17       | 18          |
| P3     | 8    | 0   | 9        | 6           |
| P4     | 14   | 18  | 15       | 17          |
| P5     | 16   | 4   | 9        | 12          |

---

### d. Which od htese algorithms results in the minimum average waiting time (over all processes)?

Rata-rata waktu tunggu:

- **FCFS:** (0 + 5 + 8 + 14 + 16) / 5 = **8.6**
- **SJF:** (8 + 17 + 0 + 18 + 4) / 5 = **9.4**
- **Priority:** (0 + 17 + 9 + 15 + 9) / 5 = **10.0**
- **Round Robin:** (15 + 18 + 6 + 17 + 12) / 5 = **13.6**

**FCFS menghasilkan waktu tunggu rata-rata paling kecil: 8.6 satuan waktu**

---
## 5.18 The following processes are being scheduled using a preemptive, priority-based, round-robin scheduling algorithm.

| Process | Priority | Burst | Arrival |
|---------|----------|-------|---------|
| P1      | 8        | 15    | 0       |
| P2      | 3        | 20    | 0       |
| P3      | 4        | 20    | 20      |
| P4      | 4        | 20    | 25      |
| P5      | 5        | 5     | 45      |
| P6      | 5        | 15    | 55      |

Each process is assigned a numerical priority, with a higher number indi-cating a higher relative priority. The scheduler will execute the highest-priority process. For processes with the same priority, a round-robin scheduler will be used with a time quantum of 10 units. If a process is preempted by a higher-priority process, the preempted process is placed at the end of the queue.

### a. Show the scheduling order of the processes using a Gantt chart.

- t = 0–15: P₁ (prio 8) dijalankan, selesai.
- t = 15–20: P₂ mulai, tapi preempted oleh P₃.
- t = 20–30: P₃ (prio 4) jalan, sisa 10.
- t = 30–40: P₄ (prio 4) masuk dan dijalankan, sisa 10.
- t = 40–45: P₃ lanjut, selesai.
- t = 45–50: P₅ (prio 5) preempt, selesai (burst 5).
- t = 50–55: P₄ lanjut, selesai.
- t = 55–70: P₆ (prio 5) jalan, selesai (2 kuantum).
- t = 70–90: P₂ lanjut, selesai.

| Proses | P1 | P1 | P1 | P3 | P4 | P3 | P5 | P4 | P6 | P6 | P2 | P2 |
|--------|----|----|----|----|----|----|----|----|----|----|----|----|
| Waktu  | 0  | 10 | 15 | 20 | 30 | 40 | 45 | 50 | 55 | 65 | 70 | 80 | 90 |

### b. What is the turnaround time for each process?

**Turnaround Time = Completion Time − Arrival Time**

| Process | Arrival | Completion | Turnaround |
|---------|---------|------------|------------|
| P₁      | 0       | 15         | 15         |
| P₂      | 0       | 90         | 90         |
| P₃      | 20      | 45         | 25         |
| P₄      | 25      | 55         | 30         |
| P₅      | 45      | 50         | 5          |
| P₆      | 55      | 70         | 15         |

### c. What is the waiting time for each process?

**Waiting Time = Turnaround Time − Burst Time**

| Process | Burst | Turnaround | Waiting |
|---------|-------|------------|---------|
| P₁      | 15    | 15         | 0       |
| P₂      | 20    | 90         | 70      |
| P₃      | 20    | 25         | 5       |
| P₄      | 20    | 30         | 10      |
| P₅      | 5     | 5          | 0       |
| P₆      | 15    | 15         | 0       |


---

[Nabillatun Nafista 3124521027 ]
