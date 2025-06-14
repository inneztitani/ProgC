---
title: 'Case Study I - Do While, For & Switch'

---

# Case Study I - Do While, For & Switch

> Pembuat Soal: WN

```bash
Nama    : Innezahra Aurellia Titani
NPM     : 2306168965
```

## Deskripsi Soal

![Konstruksi](https://thumb.viva.co.id/media/frontend/thumbs3/2022/06/27/62b917b3d8320-kuli-bangunan_1265_711.jpg)

Kafu berkeinginan untuk membangun sebuah rumah. Namun ia memiliki keterbatasan budget, dimana ia hanya memiliki budget sebesar $2000. Untuk itu, ia ingin membuat simulator untuk mengamati rumah yang dihasilkan berdasarkan budgetnya.

Dari harga pasaran, ditentukan bahwa harga komponen rumah sebagai berikut:

1. Atap : $150
2. Gedung : $500
3. Halaman: $200
4. Pagar:Pagar:  $10 / kepingnya
5. Selesaikan konstruksi

Maka, buatlah program simulator untuk Kafu dengan ketentuan berikut:

- Program meminta input pilihan komponen rumah dari user di dalam do-while loop, program akan keluar bila user menginput 5.
- Pemilihan komponen rumah di implementasi menggunakan switch case.
- Jika memesan pagar, maka program akan menanyakan jumlah pagar yang dipesan
- Terdapat variable yang menghitung jumlah komponen yang dipesan, variable-variable ini akan ditampilkan setelah setiap pemilihan komponen (Liat pada running program)
- Pada simulator, akan menampilkan berupa rancangan ASCII art dari rumah yang dibangun, anda dapat menggunakan template kode dibawah untuk menampilkannya.
- Namun anda perlu menyelesaikan bagian penggambaran pagar pada output ASCII art menggunakan for loop, anda dapat merapikan output pagar sesuai selera anda.
- Agar program anda sempurna, tampahkan kondisional yang memeriksa apakah sisa budget yang dimiliki cukup untuk membeli komponen bangunan, dan tambahkan error message yang sesuai.

## Contoh Input/Output
![Screenshot 2025-02-26 123217](https://hackmd.io/_uploads/BJllYmn91x.png)

![Screenshot 2025-02-26 123330](https://hackmd.io/_uploads/SJSlFmn5yl.png)
![Screenshot 2025-02-26 123434](https://hackmd.io/_uploads/B1OgK739kl.png)

Contoh Kasus Over Budget
![Screenshot 2025-02-26 123645](https://hackmd.io/_uploads/HJTlF7h51e.png)
![Screenshot 2025-02-26 123720](https://hackmd.io/_uploads/ByRgFXh5yx.png)


### JAWABAN

```c

#include <stdio.h>

int main() {
    int jumlahAtap = 0;
    int jumlahGedung = 0;
    int jumlahHalaman = 0;
    int jumlahPagar = 0;
    int buildCounter;
    int option;
    int budgetAwal = 2000;

    printf("=== Rumah Simulator Kafu ===\n");
    printf("Budget awal = $%d\n", budgetAwal);
    
    // Switch case sebagai menu untuk user
    do {
        printf("\nPilih komponen yang ingin ditambahkan.\n");
        printf("1. Tambah Atap ($150)\n");
        printf("2. Tambah Gedung ($500)\n");
        printf("3. Tambah Halaman ($300)\n");
        printf("4. Tambah Pagar ($10 per keping)\n");
        printf("5. Selesaikan Konstruksi\n");
        printf("Pilihan Anda: ");
        scanf("%d", &option);
        // mendefinisikan case untuk setiap option
        switch (option){
            case 1:
                budgetAwal -= 150; 
                jumlahAtap++;
                printf("Atap ditambahkan! Sisa budget: %d\n", budgetAwal);
                break;
            case 2:
                budgetAwal -= 500;
                jumlahGedung++ ;
                printf("Gedung ditambahkan! Sisa budget: %d\n", budgetAwal);
                break;
            case 3:
                budgetAwal -= 300;
                jumlahHalaman++;
                printf("Halaman ditambahkan! Sisa budget: %d\n", budgetAwal);
                break;
            case 4: 
                printf("Berapa jumlah pagar yang ingin ditambahkan? ");
                scanf("%d", &jumlahPagar);
                budgetAwal -= (jumlahPagar*10);
                printf("Pagar sebanyak %d ditambahkan!\n", jumlahPagar);
                break;
            case 5:
                printf("Selesai konstruksi!\n");
                break;
            default:
                printf("Budget tidak cukup untuk menambahkan!\n");
        }
        //print status konstruksi setiap pemilihan option
        printf("\n=== Status Konstruksi ===\n");
        printf("atap\t: %d, gedung\t: %d, Halaman\t: %d, Pagar\t: %d keping\n", jumlahAtap, jumlahGedung, jumlahHalaman, jumlahPagar);
        printf("Sisa budget: %d\n", budgetAwal);
    } while (option != 5);
    
    // Output Atap
    for (buildCounter = 0; buildCounter < jumlahAtap; buildCounter++) {
 
        printf("   ________________________\n");
        printf("  /                        \\\n");
        printf(" /                          \\\n");
        printf("  |________________________|\n");
    }

    // Output Gedung
    for (buildCounter = 0; buildCounter < jumlahGedung; buildCounter++) {
        printf("       |                    |\n");
        printf("       | [__+__]    [__+__] |\n");
        printf("       | [__+__]    [__+__] |\n");
        printf("       |                    |\n");
        printf("       |                    |\n");
        printf("       |____________________|\n");
    }

    // Output Halaman
    for (buildCounter = 0; buildCounter < jumlahHalaman; buildCounter++) {
        printf("       ~~~~~~~~~~~~~~~~~~~~~~\n");
        printf("       ~~~~~~~~~~~~~~~~~~~~~~\n");
        printf("       ~~~~~~~~~~~~~~~~~~~~~~\n");
    }

    // Output Pagar
    for (buildCounter = 0; buildCounter < jumlahPagar; buildCounter++) {
        printf("_");
    }
    printf("\n");

    return 0;
}


```

#### Screenshot Program Berjalan:
![image](https://hackmd.io/_uploads/r1ejzzyoyx.png)


#### Kesimpulan:
- Kita dapat menggunakan do-while loop untuk memvalidasi input user. Pada program ini, program akan menjalankan terlebih dahulu isi dari loop tanpa memeriksa nilai `option`. Hal ini dilakukan agar user dapat memilih `option` dan program dapat memvalidasi input setelah loop dijalankan.
- For loop digunakan jika kita sudah memiliki iterasi tertentu (dari user), sehingga kita bisa mencetak langsung
- Switch case digunakan secara alternative yang lebih rapi dan sederhana, dan tidak mengharuskan program untuk membaca dan memvalidasi input user satu per satu. Pada kasus ini, switch case digunakan untuk menyederhanakan input user.
- 
---