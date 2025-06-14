---
title: 'Case Study I - Function'

---

# Case Study I - Function

> Pembuat Soal: GI

```bash
Nama    : Tinasha
NPM     : 2312345678
```

## Deskripsi Soal

### Part I - Soal

Kembali lagi dengan Oscar, Ia masih memiliki ketertarikan dengan angka, dan baru saja Ia mempelajari mengenai bilangan palindrome. Namun disini Ia mengalami kesulitan dan meminta bantuan anda untuk membuat sebuah program untuk **mengecek apakah angka yang diberikan merupakan bilangan palindrom atau bukan**. Selain itu, Oscar tentu memberikan beberapa batasan dari program yang akan kalian buat nantinya, yaitu

- Program mencari apakah bilangan tersebut merupakan bilangan palindrome atau tidak
- Input yang diberikan adalah dalam bentuk angka (bukan string - *"array of character"*). Dilarang menggunakan string untuk menerima input dari user
- Bagian untuk mencari apakah bilangan tersebut merupakan bilangan palindrome atau bukan dibuat pada fungsi terpisah (diluar fungsi `main()`)
- Aturan mengenai bilangan palindrome adalah sebagai berikut:
  - Bilangan palindrome adalah bilangan yang jika dibaca dari depan maupun belakang akan tetap sama
  - Contoh bilangan palindrome adalah 121, 12321, 123454321, dan seterusnya
  - Contoh bilangan bukan palindrome adalah 123, 1234, 123456, dan seterusnya
  - Bilangan yang hanya memiliki 1 digit (0-9) dianggap sebagai bilangan palindrome
  - Bilangan negatif tidak dianggap sebagai bilangan palindrome
- Program hanya menerima input berupa bilangan bulat (integer) dan tidak menerima input berupa bilangan desimal (float)
- Program hanya menerima input berupa bilangan bulat positif (>= 0) dan tidak menerima input berupa bilangan bulat negatif (< 0)

### Part I - Contoh Input dan Output

| Contoh | Contoh | Contoh |  Contoh |
| --- | --- | --- | --- |
| ![picture-1](http://cdn.digilabdte.com/u/qPIVxW.png) | ![picture-2](http://cdn.digilabdte.com/u/nqxZiM.png) | ![picture-3](http://cdn.digilabdte.com/u/Lrvd3h.png) | ![picture-4](http://cdn.digilabdte.com/u/y9DgC8.png) |
| ![picture-5](http://cdn.digilabdte.com/u/cG3LdK.png) | ![picture-6](http://cdn.digilabdte.com/u/hA6pyK.png) | ![picture-7](http://cdn.digilabdte.com/u/jBHGIn.png) | ![picture-8](https://cdn.digilabdte.com/u/YHnKAh.png) |

### Part II - Soal

Karena Oscar merasa bahwa program yang kalian buat ini terlalu mudah, maka Ia meminta kalian untuk membuatkannya fungsi tambahan untuk **mengubah angka** yang sebelumnya diberikan oleh user **menjadi angka romawi**. Adapun ketentuan yang diminta oleh Oscar terkait program tersebut adalah

- Program akan mengubah angka yang diberikan oleh user menjadi angka romawi
- Inputnya sama dengan part I, yaitu dalam bentuk angka (bukan string - *"array of character"*). Dilarang menggunakan string untuk menerima input dari user
- Angka yang dirubah adalah **4 angka terakhir** dari angka yang diberikan oleh user
- Bagian untuk mengubah angka tersebut menjadi angka romawi dibuat pada fungsi terpisah (diluar fungsi `main()`)
- Aturan mengenai angka romawi adalah sebagai berikut:
    - Angka romawi tidak memiliki konsep angka nol (0) dan angka negatif
    - Angka romawi hanya memiliki 7 simbol, yaitu I, V, X, L, C, D, dan M
    - Angka romawi memiliki aturan tertentu dalam penulisan, yaitu:
        - I, X, C, dan M dapat diulang sebanyak 3 kali berturut-turut
        - D, L, dan V tidak dapat diulang
        - I dapat ditempatkan sebelum V dan X untuk membuat angka 4 dan 9
        - X dapat ditempatkan sebelum L dan C untuk membuat angka 40 dan 90
        - C dapat ditempatkan sebelum D dan M untuk membuat angka 400 dan 900
    - Angka romawi ditulis dari yang terbesar ke yang terkecil
    - Angka romawi ditulis dari kiri ke kanan
    - Angka romawi ditulis dengan menggunakan simbol yang paling sedikit
- Program hanya menerima input berupa bilangan bulat (integer) dan tidak menerima input berupa bilangan desimal (float)
- Program hanya menerima input berupa bilangan bulat positif (>= 0) dan tidak menerima input berupa bilangan bulat negatif (< 0)

### Part II - Contoh Input dan Output

| Contoh | Contoh | Contoh |  Contoh |
| --- | --- | --- | --- |
| ![picture-1](http://cdn.digilabdte.com/u/rUCH47.png) | ![picture-2](http://cdn.digilabdte.com/u/NFTIDH.png) | ![picture-3](http://cdn.digilabdte.com/u/xsYPsK.png) | ![picture-4](http://cdn.digilabdte.com/u/QCwUEF.png) |
| ![picture-5](http://cdn.digilabdte.com/u/jei7cB.png) | ![picture-6](http://cdn.digilabdte.com/u/Idtyi4.png) | ![picture-7](http://cdn.digilabdte.com/u/Th6aMD.png) | ![picture-8](http://cdn.digilabdte.com/u/suYGFi.png) |

## Jawaban Praktikan

### Source Code

```c
// 2306168965

#include <stdio.h>

void palindrome(){
    int num, reversed = 0, remainder;
    
    // Integer yang dibalik akan disimpan pada variabel reversed
    while (num != 0) {
        remainder = num % 10;
        reversed = reversed * 10 + remainder;
        num /= 10;
    }
}

void num_to_roman(int num){

    printf("Roman numerals: ");        

    // Print angka roman berdasarkan syaratannya
    while(num != 0){
        if (num >= 1000)       // 1000 - m
        {
           printf("M");
           num -= 1000;
        }

        else if (num >= 900)   // 900 -  cm
        {
           printf("CM");
           num -= 900;
        }        

        else if (num >= 500)   // 500 - d
        {           
           printf("D");
           num -= 500;
        }

        else if (num >= 400)   // 400 -  cd
        {
           printf("CD");
           num -= 400;
        }

        else if (num >= 100)   // 100 - c
        {
           printf("C");
           num -= 100;                       
        }

        else if (num >= 90)    // 90 - xc
        {
           printf("XC");
           num -= 90;                                         
        }

        else if (num >= 50)    // 50 - l
        {
           printf("L");
           num -= 50;                                       
        }

        else if (num >= 40)    // 40 - xl
        {
           printf("XL");           
           num -= 40;
        }

        else if (num >= 10)    // 10 - x
        {
           printf("X");
           num -= 10;           
        }

        else if (num >= 9)     // 9 - ix
        {
           printf("IX");
           num -= 9;                         
        }

        else if (num >= 5)     // 5 - v
        {
           printf("V");
           num -= 5;                                     
        }

        else if (num >= 4)     // 4 - iv
        {
           printf("IV");
           num -= 4;                                        
        }

        else if (num >= 1)     // 1 - i
        {
           printf("I");
           num -= 1;                                          
        }
    }
}

int main(){
    int num, tempPalin, reversed, remainder;
    
    printf("Enter an integer: ");
    scanf("%d", &num);
    
    palindrome(num);
    tempPalin = num;
    
    if (tempPalin == reversed){
        printf("%d is a palindrome.\n", tempPalin);
    }
    else {
        printf("%d is not a palindrome.\n", tempPalin);
    }

    num_to_roman(num);
}
```

### Screenshot Program Perjalan

> Praktikan, diperkenankan menggunakan dan mendaftarkan akun pada laman https://public-cdn.digilabdte.com untuk mengunggah screenshot program yang telah kalian buat. Jika ada pertanyaan lebih lanjut, silakan ditanyakan kepada asisten praktikum terkait.

#### Screenshot dengan memasukan NPM kalian

| Input/Output| 
| --- |
| ![input-output](http://cdn.digilabdte.com/u/Km8HRN.jpeg) |

#### Screenshot angka lainnya (bebas)

| Input | Output | Input | Output |
| --- | --- | --- | --- |
| 50 | ![image](https://hackmd.io/_uploads/Hkbm6BOj1g.png)
 | 104 | ![image](https://hackmd.io/_uploads/HykCTHOoyx.png)
 |
| 223 | ![image](https://hackmd.io/_uploads/H1FyRBdj1e.png)
 | 5000 | ![image](https://hackmd.io/_uploads/BJ--AH_oyl.png)
 |

> Cukup 4 saja, apabila ingin menambahkan lebih dari 4 screenshot dipersilakan

### Kesimpulan

- Function digunakan untuk menyimpan blok kode yang akan digunakan secara repetitif atau untuk merapikan program dan meingkatkan readabilitas dari program tersebut.
- Untuk memeriksa jika angka palindrom, digunakan function untuk membuat angka tersebut jadi reversed, lalu memeriksa jika angka tersebut sama dengan reversed.
- Untuk mengubah angka menjadi angka romawi, digunakan if else untuk setiap kondisi lalu akan dipanggil di main()