---
title: "Case Study I - Array"
---

# Case Study I - Array

> Pembuat Soal: GI

```bash
Nama    : Innezahra Aurellia Titani
NPM     : 2306168965
```

## Deskripsi Soal

Kali ini Oscar tidak memiliki ketertarikan dengan matematika maupun pemrograman. Kali ini Ia menyebabkan masalah dengan istrinya, Tinasha. Ketika Oscar sedang bermain handphone, Tinasha mendapatinya kadang senyum-senyum sendiri ketika sedang mengetik sesuatu di handphone. Tinasha, yang dilanda kecurigaan, menggeledah ponsel Oscar. Ia menemukan percakapan yang dienkripsi, membuatnya curiga bahwa Oscar berselingkuh. Setelah mengamati pola enkripsi pada beberapa pesan, Tinasha menyadari bahwa setiap huruf alfabet telah digeser posisinya. "a" diubah menjadi "r", "b" menjadi "s", dan seterusnya. Ia juga menyadari bahwa huruf besar juga dienkripsi dengan pola yang sama, "A" menjadi "R", "B" menjadi "S", dan seterusnya. Angka dan karakter non-alfabet lainnya dibiarkan tidak berubah.

Tinasha, yang tidak terlalu mahir dalam pemrograman, meminta bantuan Anda untuk membuat program yang dapat mendekripsi pesan-pesan tersebut. Tinasha menambahkan beberapa ketentuan dari program yang akan Anda buat nantinya, yaitu:

- Program akan memiliki 2 fungsi (selain fungsi `main()`), yaitu fungsi `enkripsi` dan `dekripsi`
- Fungsi `enkripsi` akan menerima parameter berupa array of char yang berisi pesan yang akan dienkripsi
- Fungsi `dekripsi` akan menerima parameter berupa array of char yang berisi pesan yang akan didekripsi
- Program akan meminta input berupa pilihan, apakah user ingin melakukan enkripsi atau dekripsi
- Penggunaan library `string.h` dan `ctype.h` diperbolehkan
- Program hanya menerima input berupa huruf alfabet (baik huruf besar maupun huruf kecil) dan karakter non-alfabet lainnya
- Program tidak menerima input berupa angka

### Hint (Gunakan ketika sudah terpojok)

<details>
  <summary>Klik untuk melihat hint</summary>

- Anda dapat menggunakan fungsi `isalpha()` dari library `ctype.h` untuk mengecek apakah karakter yang diinputkan adalah huruf atau bukan  
- Anda dapat menggunakan fungsi `isupper()` dari library `ctype.h` untuk mengecek apakah karakter yang diinputkan adalah huruf besar atau bukan  
- Anda dapat menggunakan fungsi `islower()` dari library `ctype.h` untuk mengecek apakah karakter yang diinputkan adalah huruf kecil atau bukan
- Gunakan `strcspn()` dari library `string.h` untuk mengecek apakah karakter yang diinputkan adalah angka atau bukan
- Gunakan `strlen()` dari library `string.h` untuk mengecek panjang string yang diinputkan
- Gunakan konversi ASCII untuk menggeser posisi huruf
- Jumlah huruf dalam alfabet adalah 26
- Untuk mengubah A atau a menjadi R atau r, Anda dapat menggunakan rumus `(char - 'A' + 17) % 26 + 'A'` atau `(char - 'a' + 17) % 26 + 'a'`
- Sementara itu, untuk mengubah R atau r menjadi A atau a, Anda dapat menggunakan rumus `(char - 'A' + 9) % 26 + 'A'` atau `(char - 'a' + 9) % 26 + 'a'`
- Jika Anda kesulitan dalam mengubah huruf, Anda dapat menggunakan tabel ASCII sebagai referensi

Referensi pembelajaran:
- [Passing string in function](https://dyclassroom.com/c/c-functions-and-strings)
- [ASCII Table](https://en.cppreference.com/w/c/language/ascii)
- [String.h](https://www.w3schools.com/c/c_ref_string.php)
- [Ctype.h](https://www.w3schools.com/c/c_ref_ctype.php)
- [Remove newline character in C](https://www.geeksforgeeks.org/removing-trailing-newline-character-from-fgets-input/)

</details>


### Penjelasan Enkripsi

Enkripsi yang digunakan oleh Oscar adalah variasi dari enkripsi Caesar. Enkripsi Caesar adalah teknik enkripsi sederhana yang menggunakan sandi substitusi. Sandi ini menggeser huruf-huruf dalam alfabet sejumlah posisi tertentu. Contoh, jika kita menggeser huruf "a" sebanyak 3 posisi, maka "a" akan menjadi "d".

### Contoh Input dan Output

<table border="1">
  <tr>
    <th>Contoh</th>
    <th>Contoh</th>
    <th>Contoh</th>
  </tr>
  <tr>
    <td>
      <pre>
Pilih operasi:
1. Enkripsi
2. Dekripsi
Masukkan pilihan: 1
Masukkan teks: Hello hello, I'm under the water
Hasil enkripsi: Yvccf yvccf, Z'd leuvi kyv nrkvi
      </pre>
    </td>
    <td>
      <pre>
Pilih operasi:
1. Enkripsi
2. Dekripsi
Masukkan pilihan: 1
Masukkan teks: Nishiyama daddy daddy
Hasil enkripsi: Ezjyzprdr uruup uruup
      </pre>
    </td>
    <td>
      <pre>
Pilih operasi:
1. Enkripsi
2. Dekripsi
Masukkan pilihan: 1
Masukkan teks: @Valorant -5
Hasil enkripsi: @Mrcfirek -5
      </pre>
    </td>
  </tr>
  <tr>
    <td>
      <pre>
Pilih operasi:
1. Enkripsi
2. Dekripsi
Masukkan pilihan: 2
Masukkan teks: Fjtri rdsilb bv dvarepr
Hasil dekripsi: Oscar ambruk ke mejanya
      </pre>
    </td>
    <td>
      <pre>
Pilih operasi:
1. Enkripsi
2. Dekripsi
Masukkan pilihan: 2
Masukkan teks: kjlbz xr bzivz
Hasil dekripsi: tsuki ga kirei
      </pre>
    </td>
    <td>
      <pre>
Pilih operasi:
1. Enkripsi
2. Dekripsi
Masukkan pilihan: 2
Masukkan teks: Jfkf zez verb jvbrcz
Hasil dekripsi: Soto ini enak sekali
      </pre>
    </td>
  </tr>
</table>


### Kode Template

```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

void enkripsi(char teks[]) {
    // TODO: Tulis kode enkripsi di sini
}

void dekripsi(char teks[]) {
    // TODO: Tulis kode dekripsi di sini
}

int main() {
    // TODO: Deklarasi variabel

    printf("Pilih operasi:\n");
    printf("1. Enkripsi\n");
    printf("2. Dekripsi\n");
    printf("Masukkan pilihan: ");

    // TODO: Input pilihan

    // TODO: Netralisir karakter newline

    // TODO: Input teks

    // TODO: Pemilihan operasi

    return 0;
}
```

## Jawaban Praktikan

### Kode Praktikan

```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

void enkripsi(char teks[]) {

    for (int i = 0; i < strlen(teks); i++) {
        int isupper = isupper(teks[i]);
        int islower = islower(teks[i]);
        int isalpha = isalpha(teks[i]);

    for (int i = 0; i < strlen(teks); i++) {
        if (isalpha != 0){
            if (isupper != 0){
                teks[i] = ((teks[i] - 'A' + 17) % 26 + 'A');
                printf(" %c", teks[i]);
            }
            if (islower != 0){
                teks[i] = ((teks[i] - 'a' + 17) % 26 + 'a');
                printf(" %c", teks[i]);
            }
        }
    }
}
}

void dekripsi(char teks[]) {

    for (int i = 0; i < strlen(teks); i++) {
        int isupper = isupper(teks[i]);
        int islower = islower(teks[i]);
        int isalpha = isalpha(teks[i]);

        for (int i = 0; i < strlen(teks); i++) {
            if (isalpha != 0){
                if (isupper != 0){
                    teks[i] = ((teks[i] - 'A' + 17) % 26 + 'A');
                    printf(" %c", teks[i]);
                }
                if (islower != 0){
                    teks[i] = ((teks[i] - 'a' + 17) % 26 + 'a');
                    printf(" %c", teks[i]);
                }
            }
        }
    }
}

int main() {
    char teks[100]; // TODO: Deklarasi variabel
    char encrypt_result[100], decrypt_result[100];
    int option;

    printf("Pilih operasi:\n");
    printf("1. Enkripsi\n");
    printf("2. Dekripsi\n");
    printf("Masukkan pilihan: ");
    scanf("%d", &option); // TODO: Input pilihan
    scanf("%d", &option);
    
    printf("Masukkan teks:");
    scanf(" [^\n]s", teks);
    
    switch (option) {
        case 1: 
            enkripsi(teks);
        case 2:
            dekripsi(teks);
        default:
            printf("Input tidak valid");
    }
}
```

### Screenshot Program Berjalan

Untuk bagian `dekripsi`, silakan isi outputnya dengan  screenshot program dengan kalimat enkripsi yang telah disediakan. Sedangkan untuk `enkripsi`, silakan isi outputnya dengan screenshot program dengan kalimat bebas sesuka kalian.

| Input (Dekripsi) | Output | Input (Enkripsi) | Output |
| --- | --- | --- | --- |
| Rbl zexze dvdsvcz bruf lcrex kryle leklb Kzerjyr, szjrbry brl dvdsreklbl? | ![change-me](![![image](https://hackmd.io/_uploads/HJyuFYWhyg.png)
]()
) | change-me | ![change-me](http://cdn.digilabdte.com/u/Qh8OTL.jpg) |
| Brcrl szjr jvjlrkl prex svinrier szil rqliv rkrl yzkrd xvcrg jvgvikz drcrd | ![change-me](http://cdn.digilabdte.com/u/d8eclU.jpg) | change-me | ![change-me](http://cdn.digilabdte.com/u/NcadXf.jpg) |
| Rbl kzurb gvulcz yrixrepr, srekl jrpr dvdzczyepr | ![change-me](http://cdn.digilabdte.com/u/U40PN3.jpg) | change-me | ![change-me](http://cdn.digilabdte.com/u/Qh8OTL.jpg) |
| Jrpr rbre dvdsrpri leklb arjr reur | ![change-me](http://cdn.digilabdte.com/u/Qh8OTL.jpg) | change-me | ![change-me](http://cdn.digilabdte.com/u/Xza010.jpg) |