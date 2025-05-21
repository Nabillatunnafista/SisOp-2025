# SISTEM OPERASI # 

Nama  : Nabillatun Nafista  

NRP   : 3124521027

Kelas : Teknik Informatika - A
 
---
## 1.	Buatkan Analisa terkait SJF Scheduling Algorithm Without Arrival Time

### Code :

```c
#include<stdio.h>
struct proc
{
    int no,bt,ct,tat,wt;
};
struct proc read(int i)
{
    struct proc p;
    printf("\nProcess No: %d\n",i);
    p.no=i;
    printf("Enter Burst Time: ");
    scanf("%d",&p.bt);
    return p;
}
int main()
{
    struct proc p[10],tmp;
    float avgtat=0,avgwt=0;
    int n,ct=0;
    printf("<--SJF Scheduling Algorithm Without Arrival Time (Non-Preemptive)-->\n");
    printf("Enter Number of Processes: ");
    scanf("%d",&n);
    for(int i=0;i<n;i++)
        p[i]=read(i+1);
    for(int i=0;i<n-1;i++)
        for(int j=0;j<n-i-1;j++)    
            if(p[j].bt>p[j+1].bt)
            {
				tmp=p[j];
				p[j]=p[j+1];
				p[j+1]=tmp;
            }
    printf("\nProcessNo\tBT\tCT\tTAT\tWT\tRT\n");
    for(int i=0;i<n;i++)
    {
        ct+=p[i].bt;
		p[i].ct=p[i].tat=ct;
		avgtat+=p[i].tat;
        p[i].wt=p[i].tat-p[i].bt;
        avgwt+=p[i].wt;

        printf("P%d\t\t%d\t%d\t%d\t%d\t%d\n",p[i].no,p[i].bt,p[i].ct,p[i].tat,p[i].wt,p[i].wt);
    }
    avgtat/=n,avgwt/=n;
    printf("\nAverage TurnAroundTime=%f\nAverage WaitingTime=%f",avgtat,avgwt);
}
```
### Output :
![Image Alt](https://github.com/Nabillatunnafista/SisOp-2025/blob/5ecd1b357c571137e97cbb76517dc4e85eaee44c/img/so1.png)

### Analisa :
Kode C ini mengimplementasikan algoritma penjadwalan CPU SJF (Shortest Job First) Non-Preemptive. Ia membaca burst time proses, lalu mengurutkannya (menggunakan bubble sort) dari yang terpendek untuk dieksekusi. 
Kemudian, dihitung dan ditampilkan completion time, turnaround time, waiting time, serta rata-rata dari turnaround time dan waiting time setiap proses.

### Gantt Chart

```
| P4 | P2 | P3 | P1 |
0   3     8    16   26
```
#### Average Turnaround Time (⟨TAT⟩)
⟨TAT⟩ = (3 + 8 + 16 + 26) / 4  
⟨TAT⟩ = 53 / 4  
⟨TAT⟩ = **13.25**

#### Average Waiting Time (⟨WT⟩)
⟨WT⟩ = (0 + 3 + 8 + 16) / 4  
⟨WT⟩ = 27 / 4  
⟨WT⟩ = **6.75**

---
## 2. Buatkan Analisa terkait SJF Scheduling Algorithm (Non-Preemptive)

### Code :

```c
#include<stdio.h>
struct proc
{
    int no,at,bt,it,ct,tat,wt;
};
struct proc read(int i)
{
    struct proc p;
    printf("\nProcess No: %d\n",i);
    p.no=i;
    printf("Enter Arrival Time: ");
    scanf("%d",&p.at);
    printf("Enter Burst Time: ");
    scanf("%d",&p.bt);
    return p;
}
int main()
{
  
    int  n,j,min=0;
    float avgtat=0,avgwt=0;
    struct proc p[10],temp;
    printf("<--SJF Scheduling Algorithm (Non-Preemptive)-->\n");
    printf("Enter Number of Processes: ");
    scanf("%d",&n);
    for(int i=0;i<n;i++)
        p[i]=read(i+1);
    for(int i=0;i<n-1;i++)
        for(j=0;j<n-i-1;j++)    
            if(p[j].at>p[j+1].at)
            {
            temp=p[j];
            p[j]=p[j+1];
            p[j+1]=temp;
            }
    for(j=1;j<n&&p[j].at==p[0].at;j++)
        if(p[j].bt<p[min].bt)
            min=j;
    temp=p[0];
    p[0]=p[min];
    p[min]=temp;
    p[0].it=p[0].at;
    p[0].ct=p[0].it+p[0].bt;
    for(int i=1;i<n;i++)
    {
        for(j=i+1,min=i;j<n&&p[j].at<=p[i-1].ct;j++)
            if(p[j].bt<p[min].bt)
                min=j;
        temp=p[i];
        p[i]=p[min];
        p[min]=temp;
        if(p[i].at<=p[i-1].ct)
            p[i].it=p[i-1].ct;
        else
            p[i].it=p[i].at;
        p[i].ct=p[i].it+p[i].bt;
    }
    printf("\nProcess\t\tAT\tBT\tCT\tTAT\tWT\tRT\n");
    for(int i=0;i<n;i++)
    {
        p[i].tat=p[i].ct-p[i].at;
        avgtat+=p[i].tat;
        p[i].wt=p[i].tat-p[i].bt;
        avgwt+=p[i].wt;
        printf("P%d\t\t%d\t%d\t%d\t%d\t%d\t%d\n",p[i].no,p[i].at,p[i].bt,p[i].ct,p[i].tat,p[i].wt,p[i].wt);
    }
    avgtat/=n,avgwt/=n;
    printf("\nAverage TurnAroundTime=%f\nAverage WaitingTime=%f",avgtat,avgwt);
}
```
### Output :
![Image Alt](https://github.com/Nabillatunnafista/SisOp-2025/blob/5ecd1b357c571137e97cbb76517dc4e85eaee44c/img/so2.png)

### Analisa :
Kode C ini mengimplementasikan algoritma penjadwalan CPU SJF Non-Preemptive dengan Arrival Time. Program mengurutkan proses berdasarkan waktu kedatangan, 
lalu memilih yang memiliki burst time terpendek di antara proses yang sudah tiba untuk dieksekusi. Ini menghitung dan mencetak completion time, turnaround time, waiting time setiap proses, serta rata-ratanya.

### Gantt Chart
```
| P1 | P3 | P4 | P2 |
0    7    8    10   14
```
#### Average Turnaround Time (⟨TAT⟩)
⟨TAT⟩=(3+8+16+26)/4
⟨TAT⟩=53/4
⟨TAT⟩=13.25

#### Average Waiting Time (⟨WT⟩)
⟨WT⟩=(0+3+8+16)/4
⟨WT⟩=27/4
⟨WT⟩=6.75

---
3. Buatkan Analisa terkait SRTF Scheduling Algorithm (Preemptive)

### Code :

```c
#include<stdio.h>
#define MAX 9999
struct proc
{
    int no,at,bt,rt,ct,tat,wt;
};
struct proc read(int i)
{
    struct proc p;
    printf("\nProcess No: %d\n",i);
    p.no=i;
    printf("Enter Arrival Time: ");
    scanf("%d",&p.at);
    printf("Enter Burst Time: ");
    scanf("%d",&p.bt);
    p.rt=p.bt;
    return p;
}
int main()
{
    struct proc p[10],temp;
    float avgtat=0,avgwt=0;
    int n,s,remain=0,time;
    printf("<--SRTF Scheduling Algorithm (Preemptive)-->\n");
    printf("Enter Number of Processes: ");
    scanf("%d",&n);
    for(int i=0;i<n;i++)
        p[i]=read(i+1);
    for(int i=0;i<n-1;i++)
        for(int j=0;j<n-i-1;j++)    
            if(p[j].at>p[j+1].at)
            {
            temp=p[j];
            p[j]=p[j+1];
            p[j+1]=temp;
            }
    printf("\nProcess\t\tAT\tBT\tCT\tTAT\tWT\n");
    p[9].rt=MAX;
    for(time=0;remain!=n;time++)
    {
        s=9;
        for(int i=0;i<n;i++)
            if(p[i].at<=time&&p[i].rt<p[s].rt&&p[i].rt>0)
                s=i;
        p[s].rt--;
        if(p[s].rt==0)
        {
            remain++;
            p[s].ct=time+1;
            p[s].tat=p[s].ct-p[s].at;
            avgtat+=p[s].tat;
            p[s].wt=p[s].tat-p[s].bt;
            avgwt+=p[s].wt;
            printf("P%d\t\t%d\t%d\t%d\t%d\t%d\n",p[s].no,p[s].at,p[s].bt,p[s].ct,p[s].tat,p[s].wt);
        }
    }
    avgtat/=n,avgwt/=n;
    printf("\nAverage TurnAroundTime=%f\nAverage WaitingTime=%f",avgtat,avgwt);
}
```
### Output :
![Image Alt](https://github.com/Nabillatunnafista/SisOp-2025/blob/5ecd1b357c571137e97cbb76517dc4e85eaee44c/img/so3.png)

### Analisa :
Kode C ini mengimplementasikan algoritma penjadwalan CPU SRTF (Shortest Remaining Time First), yaitu versi preemptive dari SJF. Program membaca waktu kedatangan (arrival time) dan burst time setiap proses, 
lalu mengurutkannya berdasarkan arrival time. Selama eksekusi, pada setiap unit waktu, CPU akan memilih proses yang sudah tiba dan memiliki sisa burst time (remaining time) paling sedikit. 
Jika sisa waktu sebuah proses menjadi nol, berarti proses tersebut selesai, dan program akan menghitung serta mencetak completion time, turnaround time, dan waiting time untuk proses tersebut, serta akumulasi rata-ratanya.

### Gantt Chart

---





