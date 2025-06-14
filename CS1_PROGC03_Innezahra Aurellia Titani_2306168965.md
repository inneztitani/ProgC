---
title: CS1_PROGC03_Innezahra Aurellia Titani_2306168965

---

# Case Study Modul If Statement & While Loop

```bash
Nama    : Innezahra Aurellia Titani
NPM     : 2306168965
```

## Soal

### Deskripsi Soal

Oscar sangat tertarik dengan deret Fibonacci, yang dimulai dengan angka 1 dan 1, dan angka berikutnya adalah penjumlahan dari dua angka sebelumnya (1, 1, 2, 3, 5, 8, dan seterusnya). Ia ingin tahu bilangan Fibonacci ke-n, tetapi menghitungnya secara manual akan sangat melelahkan, apalagi jika n sangat besar.

Oscar, yang juga memiliki minat dalam pemrograman, memutuskan untuk membuat program sederhana dalam bahasa C. Program ini akan menerima input berupa angka n dari pengguna. Lalu program akan menghitung dan menampilkan bilangan Fibonacci ke-n.

Oscar menyadari ada beberapa skenario yang harus dia tangani:

- **Input tidak valid**, jika pengguna memasukkan nilai n yang lebih kecil atau sama dengan 0, program harus memberitahu pengguna bahwa input tidak valid
- **Base case (n=1)**, jika n adalah 1, maka bilangan Fibonacci ke-1 adalah 1
- **General case (n>1)**, jika n lebih besar dari 1, maka program harus menghitung bilangan Fibonacci ke-n

Setelah menulis kode, Oscar mengujinya dengan berbagai nilai n.  Ia merasa senang ketika programnya berhasil menghitung bilangan Fibonacci dengan benar, bahkan untuk nilai n yang besar. Oscar merasa bangga karena berhasil menggabungkan kecintaannya pada angka dan kemampuannya dalam pemrograman untuk memecahkan teka-teki dari buku tua tersebut. Ia kemudian melanjutkan petualangannya dalam mempelajari pola-pola angka yang lebih menantang.

### Contoh Input/Output

| Input | Output |
| --- | --- |
| `Masukkan nilai n: 1` | `Bilangan Fibonacci ke-1 adalah 1` |
| `Masukkan nilai n: 4` | `Bilangan Fibonacci ke-4 adalah 3` |
| `Masukkan nilai n: 8` | `Bilangan Fibonacci ke-8 adalah 21` |
| `Masukkan nilai n: 12` | `Bilangan Fibonacci ke-12 adalah 144` |
| `Masukkan nilai n: 16` | `Bilangan Fibonacci ke-16 adalah 987`|
| `Masukkan nilai n: 20` | `Bilangan Fibonacci ke-20 adalah 6765` |
| `Masukkan nilai n: -10` | `Masukkan nilai n yang lebih besar dari 0` |
| `Masukkan nilai n: 0` | `Masukkan nilai n yang lebih besar dari 0` |

## Jawaban

### Source Code Pekerjaan Praktikan

```c
#include <stdio.h>

int fib(int n) {
    // Menyimpan bilangan Fibonnaci sebelum (before), saat ini (cur), dan hasl penjumlahan (sum)
    int before = 1;
    int cur = 1;
    int sum;
    
    if (n <= 1) 
        return 1; //Mengembalikan 1 jika n <= 1
    
    for (int i = 2; i < n; i++) {
        sum = before + cur; //rumus menghitung nilai fibonacci
        before = cur;
        cur = sum; // mengupdate nilai fibonacci terbaru
    }
    return sum; //Mengembalikan hasil perhitungan sum dengan nilai terbaru
}

int main() {
    int n;
    
    printf("Masukkan nilai n: "); // Prompt user untuk input integer
    scanf("%d", &n);
    
    if (n <= 0) {
        printf("Masukkan nilai n yang lebih besar dari 0\n"); //Memvalidasi input intuk memasikan nilai n > 0
        return 1;
    }
    
    int result = fib(n); //menjalankan fib(n) untuk menghitung nilai fibonacci
    printf("Bilangan Fibonacci ke-%d adalah %d\n", n, result);  //menampilkan hasil
    
    return 0;
}
```

### Screenshot Program Berjalan
saat nilai n = 1
![image](https://hackmd.io/_uploads/BJIdKCH51x.png)


saat nilai n = 8
![image](https://hackmd.io/_uploads/HybADRScJe.png)

saat nilai n <= 0
![image](https://hackmd.io/_uploads/ry2YKRHqyx.png)


### Kesimpulan 
- Statement if digunakan untuk memvalidasi input
- Pada program ini, digunakan statement for untuk menghitung deret fibonacci secara iteratif
- iterasi yang digunakan dicontrol berdasarkan nilai n