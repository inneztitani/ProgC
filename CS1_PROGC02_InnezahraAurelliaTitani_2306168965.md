---
title: Case Study I - Dasar C

---

# Case Study I - Dasar C
> Pembuat Soal: 
```
Nama  : [Innezahra Aurellia Titani]
NPM   : [2306168965]
```
---
<center><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/00/USDnotesNew.png/800px-USDnotesNew.png" width="300 px"/></center>
<br>
Karena bisnisnya yang sukses dalam ranah internasional, Ryan kini memiliki sejumlah lembar dolar AS dengan denominasi $1, $2, $5, dan $10. Ryan berniat untuk menukarakan uang-uang tersebut ke rupiah jika berjumlah setidaknya $100. Untuk meningkatkan efisiensi bisnis, Ryan merekrut anda untuk menciptakan sebuah program yang dapat menghitung uangnya.
<br><br>
Ryan meminta anda untuk menciptakan program yang pertama-tama menerima 4 buah input, jumlah lembar masing-masing denominasi yang dimiliki Ryan. Program lalu harus mengeluarkan total uang dolar yang dimiliki Ryan. 
<br><br>
Setelah menghitung total uang yang dimiliki, jika total uang Ryan sudah melebihi $100, maka Ryan akan memasukkan nilai tukar USD ke IDR pada hari itu dan program akan mengeluarkan nominal hasil tukar uang Ryan dari dolar AS (USD) ke rupiah (IDR).

#### Contoh Program
![Contoh 1](https://i.imgur.com/PLQhoK6.png)  
Ryan memiliki 2 lembar \$1, 3 lembar \$2, 2 lembar \$5, dan 4 lembar \$10. Jumlah total uang Ryan berjumlah $58. Program selesai.

![Contoh 2](https://i.imgur.com/OpDzBjF.png)  
Jumlah total uang Ryan sebesar \$123. Jumlah tersebut telah melebihi $100 maka nilai tukar sebesar Rp15000 dimasukkan dan program menghasilkan total uang Ryan dalam rupiah sebsar Rp1845000,00.

![Contoh 3](https://i.imgur.com/X7Dy2Ti.png)  

#### Test Case
<table>
    <tr>
        <th>Input</th>
        <th>Output</th>
    </tr>
    <tr>
        <th>2 <br> 3 <br> 2 <br> 4</th>
        <th>58</th>
    </tr>
    <tr>
        <th>10 <br> 4 <br> 5 <br> 8 <br> 15000</th>
        <th>123 <br> 1845000.00</th>
    </tr>
    <tr>
        <th>0 <br> 5 <br> 16 <br> 1 <br> 16342.15</th>
        <th>100 <br> 1634215.00</th>
    </tr>
    <tr>
        <th>9 <br> 2 <br> 0 <br> 1</th>
        <th>23</th>
    </tr>
</table>

---
```c
#include <stdio.h>

int main (){
    // Mendeklarasi variabel uang $1, $2, $5, $10
    int satu, dua, lima, sepuluh;

    printf("Kalkulator USD\n");
    
    // Men-prompt user (Ryan) untuk input jumlah lembar dolar yang dimiliki
    printf("Jumlah $1\t: ");
    scanf("%d", &satu);

    printf("Jumlah $2\t: ");
    scanf("%d", &dua);

    printf("Jumlah $5\t: ");
    scanf("%d", &lima);

    printf("Jumlah $10\t: ");
    scanf("%d", &sepuluh);

    // Membuat variabel baru untuk total uang yang dimiliki dengan rumus berikut
    int total = (satu * 1) + (dua * 2) + (lima * 5) + (sepuluh * 10);
    printf("----------------\n");
    // Akan memberikan output total uang berdasarkan input user sebelumnya
    printf("Total\t\t: $%d\n", total);

    // Jika total melebihi atau sama dengan 100, maka program akan prompt user untuk input nilai tukar
    if (total >= 100) 
    {
        float tukar;
        printf("Nilai Tukar\t: Rp");
        scanf("%f", &tukar);
        
        // program akan memberika output dengan rumus nilai total * tukar
        float hasil_tukar = (float) total * tukar;
        printf("Hasil Tukar\t: Rp%.2f\n", hasil_tukar);
    }
    
    printf("----------------\n");

    return 0;
}
```
#### Screenshot Program Berjalan:
Jika total < 100
![image](https://hackmd.io/_uploads/HyMpqc3F1e.png)

Jika total = 100
![image](https://hackmd.io/_uploads/r1-Ih52tJe.png)

Jika total > 100
![image](https://hackmd.io/_uploads/S1mXsqnYkx.png)


#### Kesimpulan:
- Untuk membuat sebuah program dalam bahasa C, seringkali digunakan library <stdio.h> untuk bisa menggunakan input output standar
- Ada beberapa tipe data dalam bahasa C seperti integer (int), float, character (char), dan lain sebagainya
- Syntax aritmatika yang digunakan dalam program ini adalah pertambahan (+) dan perkalian (*)
- Program ini digunakan untuk membantu menghitung jumlah uang yang dimiliki berdasarkan lembar uang USD yang dimiliki
- Jika nilai total yang dimiliki melebihi $100, maka dapat ditukar berdasarkan nilai tukar yang diimput user
---