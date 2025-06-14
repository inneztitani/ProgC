# Case Study - Struct
> Pembuat Soal: NS
```
Nama  : [Innezahra Aurellia Titani]
NPM   : [2306168965]
```
---

### Pengantar Soal

Najib Friki memiliki hobi untuk membuat berbagai macam mesin di garasinya. Tiap mesin yang ia buat memiliki karakteristik dan cara interpretasi data yang berbeda berdasarkan jenisnya. Dia malas mencatat keadaan dari mesin berdasarkan data yang ia dapat dari masing masing mesin. Sehingga, mesin - mesin yang ia buat sering kali rusak. 

Oleh karena itu, sebagai sahabat Najib Friki, kalian ingin membantunya melakukan untuk membuat simulasi mesin - mesin yang ia punya supaya Najib Friki tau kapan harus merawat mesin tersebut.

#### Kriteria Program
- Masing masing mesin memiliki data berikut :
  - Nama (Maksimal 30 huruf)
  - Tipe Mesin (Gunakan Enum) : `BOILER`, `COMPRESSOR`, `COOLING_SYSTEM`
  - Suhu (Gunakan Union):
    - Jika mesin adalah `BOILER` maka mesin menggunakan satuan **Celcius**
    - Jika mesin adalah `COMPRESSOR` maka mesin menggunakan satuan **Farenheit**
    - Jika mesin adalah `COOLING_SYSTEM` maka mesin menggunakan satuan **Kelvin**
  - Status (Gunakan Enum)
    - Jika mesin adalah `BOILER`:
      - **< 100 C** = NORMAL
      - **100 - 150 C** = WARNING
      - **> 150 C** = DANGER
    - Jika mesin adalah `COMPRESSOR`:
      - **< 212 F** = NORMAL
      - **212 - 302 F** = WARNING
      - **> 302 C** = DANGER
    - Jika mesin adalah `COOLING_SYSTEM`:
      - **< 280 K** = NORMAL
      - **280 - 320 K** = WARNING
      - **> 320 K** = DANGER

#### Flow Program
- Tanya najib punya berapa mesin
- Minta najib untuk mengisi data untuk setiap mesin
  - Data yang diisi adalah nama, tipe mesin, dan suhu
- Tanya najib simulasi ingin dilakukan berapa lama
- Jalankan simulasi mesin
  - Simulasinya adalah peningkatan suhu dari setiap mesin sebanyak **4.2%** dari suhu pada bulan sebelumnya
  - Pada bulan terakhir, setiap mesin akan diassign dengan status yang sesuai dengan kriteria
- Tampilkan hasil dari simulasi 

#### Contoh hasil run

Contoh 1
![Image](http://cdn.digilabdte.com/u/EbZBNd.png)

Contoh 2
![Image](http://cdn.digilabdte.com/u/fKTbIA.png)


### Jawaban Anda

#### Kode
```c
#include <stdio.h>
#include <string.h>

// enum untuk tipe mesin
typedef enum {
    BOILER,
    COMPRESSOR,
    COOLING_SYSTEM
} tipeMesin;

// union untuk suhu mesin
typedef union {
    float celsius, fahrenheit, kelvin;
} suhuMesin;

// enum untuk status mesin
typedef enum {
    NORMAL,
    WARNING,
    DANGER
} statusMesin

// struct untuk mesin
typedef struct {
    char name[31];
    tipeMesin tipe;
    statusMesin status;
    suhuMesin suhu;
} mesin;

const *char {
    
}

int main() {
    int jumlahMesin, bulan;
    char buffer[1000];
    
    printf("Masukkan jumlah mesin: %d", ; jumlahMesin);
    scanf("%d", &jumlahMesin);
    getchar() != '\n'; // buang newline
    
    for (int i = 0; i < jumlahMesin; i++) {
        printf("\nMesin ke-%d\n", i + 1);
        
        printf("Nama Mesin: %c", name);
        scanf("%c", &name);
        getchar() != '\n';
        // error handling jika lebih dari 30 karakter
        if (strlen(buffer) > name) {
            printf("nama terlalu panjang.");
        } else if (strlen(buffer) == 0) {
            printf("nama kosong.\n");
        } else {
            strcpy(mesin[i].name, buffer);
            break;
        }        
        
        printf("Pilih tipe mesin (0: BOILER, 1: COMPRESSOR, 2: COOLING_SYSTEM): %d", tipe);
        scanf("%d", tipe);
        getchar() != '\n';
        
        while(1){
            if tipe == 0 {
                return BOILER;
                break;
            } else if tipe == 1 {
                return COMPRESSOR;
                break;
            } else if tipe == 2 {
                return COOLING_SYSTEM;
                break;
            } else {
                printf("tipe invalid.");
                break;
            }
        }
        
        printf("Masukkan suhu awal: %f", suhu);
        scanf("%f", suhu);
        getchar() != '\n';
        
        while(1){
            if tipeMesin == BOILER {
                if suhu < 100 {
                    return NORMAL;
                } else if 100 <= suhu < 150 {
                    return WARNING;
                } else {
                    return DANGER;
                }
            } else if tipeMesin == COMPRESSOR {
                if suhu < 212 {
                    return NORMAL;
                } else if 212 <= suhu < 302 {
                    return WARNING;
                } else {
                    return DANGER;
                }
            } else if tipeMesin == COOLING_SYSTEM {
                if suhu < 280 {
                    return NORMAL;
                } else if 280 <= suhu < 320 {
                    return WARNING;
                } else {
                    return DANGER; 
                }
            }
        }
        
    }
    
    printf("Masukkan jumlah bulan simulasi: %d", bulan);
    scanf("%d", bulan);
    
    // hasil simulasi
    printf("===== HASIL SIMULASI =====");
    for (int = 0; i < jumlahMesin, jumlahMesin++) {
        printf("Mesin: %c (%c)", nama, tipe);
        for (int i = 0; i < bulan, bulan++) {
            printf("Bulan %d: Suhu = %f    Status = %c", bulan, suhu, status);
        }    
        
    }

    return 0;
}
```

#### Screenshot Hasil Run
![image](https://hackmd.io/_uploads/SyXUjUigee.png)
