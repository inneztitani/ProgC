
# Case Study 1 Modul Pointer

```bash
Nama    : Innezahra Aurellia Titani
NPM     : 2306168965
```

## Soal
### Deskripsi Soal

Cristian mencoba membuat program untuk perkalian matriks N x N. Tetapi ia nyadar bahwa programnya jika N lebih besar dari 293, program tidak akan jalan. Lalu temannya, Vella, memberitahukan Cristian hal tersebut karena matrix disimpan pada stack, jika ingin lebih besar dari 293, matrix harus disimpan pada heap. Cristian masih bingung apa maksudnya, jadi ia bertanya pada AI. Responsnya seperti ini:

![Gemini Screenshot](https://i.ibb.co.com/JWV52txX/image.png)

Namun, Cristian masih tidak mengerti. Akhirnya, Cristian meminta bantuanmu untuk membuat program perkalian matriks N x N dengan N bisa nilai yang besar (N > 1000). Ubahlah program dia agar dapat perkalian matriks dengan ukuran besar. Hint: gunakan malloc untuk mengalokasikan memori pada heap.

Vella sudah menyediakan kode program perkalian matriks yang sudah diubah agar bisa mengalikan matriks dengan ukuran besar, ia hanya meminta kamu untuk menuliskan function main dari kode yang ia buat.

> [!WARNING]
> Tidak boleh menggunakan AI untuk mengerjakan

## Kode Program Awal

```c
#include <stdio.h>
#include <math.h>
#include <time.h>
#include <stdlib.h> // Hint

#define N 293 // Jumlah kolom dan baris matriks

void printMatrix();
void matrixMultiply();
void fillRandomMatrix();
double findAverage();

int main() {
    double matrixA[N][N];
    double matrixB[N][N];
    double resultMatrix[N][N];

    // Mengisi matriks A dan B dengan angka acak
    fillRandomMatrix(matrixA, N);
    fillRandomMatrix(matrixB, N);

    printf("Matriks A:\n");
    // printMatrix(matrixA, N); // Jika terlalu besar, bisa tidak perlu dicetak
    printf("Matriks B:\n");
    // printMatrix(matrixB, N); // Jika terlalu besar, bisa tidak perlu dicetak

    printf("Hasil Perkalian Matriks A dan B:\n");
    matrixMultiply(matrixA, matrixB, resultMatrix, N);
    printf("Matriks hasil:\n");
    // printMatrix(resultMatrix, N); // Jika terlalu besar, bisa tidak perlu dicetak

    printf("Average dari matriks hasil:\n");
    double average = findAverage(resultMatrix, N);
    printf("%.2f\n", average);

    return 0;
}

void printMatrix(double matrix[][N], int rows) {
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < rows; j++) {
            printf("%.2f ", matrix[i][j]); // Cetak dengan 2 angka desimal
        }
        printf("\n");
    }
}

void matrixMultiply(double matrixA[][N], double matrixB[][N], double resultMatrix[][N], int n) {
    // Inisialisasi matriks hasil dengan nol
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            resultMatrix[i][j] = 0.0;
        }
    }

    // Lakukan perkalian matriks
    for (int i = 0; i < n; i++) { // Iterasi melalui baris matriks hasil (dan baris A)
        for (int j = 0; j < n; j++) { // Iterasi melalui kolom matriks hasil (dan kolom B)
            // Hitung elemen resultMatrix[i][j]
            for (int k = 0; k < n; k++) { // Iterasi melalui dimensi 'dalam' (m)
                resultMatrix[i][j] += matrixA[i][k] * matrixB[k][j];
            }
        }
    }
}

double findAverage(double matrix[][N], int rows) {
    double sum = 0.0;
    long long count = 0;
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < rows; j++) {
            sum += matrix[i][j];
            count++;
        }
    }
    return sum / count;
}

void fillRandomMatrix(double matrix[][N], int rows) {
    srand(time(NULL)); // Inisialisasi seed untuk random number generator
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < rows; j++) {
            matrix[i][j] = rand() % 10; // Mengisi dengan angka acak antara 0 dan 9
        }
    }
}
```

## Kode Program dari Vella

```c
#include <stdio.h>
#include <math.h>
#include <time.h>
#include <stdlib.h>

#define N 1000 // Jumlah kolom dan baris matriks

// Perlu mengubah signature fungsi untuk menerima pointer ke pointer atau cara lain
void printMatrix(double** matrix, int rows);
void matrixMultiply(double** matrixA, double** matrixB, double** resultMatrix, int n);
void fillRandomMatrix(double** matrix, int rows);
double findAverage(double** matrix, int rows);

int main() {
    int i;
    
    // melakukan dynamic memory allocation untuk setiap matrix 
    double **matrixA = (double **)malloc(N * sizeof(double *));
    double **matrixB = (double **)malloc(N * sizeof(double *));
    double **resultMatrix = (double **)malloc(N * sizeof(double *));
    
    if (matrixA == NULL || matrixB == NULL || resultMatrix == NULL) {
        printf("Allocation Failed");
        exit(0);
    }

    // mengalokasi memory untuk baris dari setiap matrix
    for (i = 0; i < N; i++){
        matrixA[i] = (double *)malloc(N * sizeof(double **));
        matrixB[i] = (double *)malloc(N * sizeof(double **));
        resultMatrix[i] = (double *)malloc(N * sizeof(double **));
    }
    
    // mengisi matrixA dan matrixB dengan angka random menggunakan function fillRandomMatrix
    fillRandomMatrix(matrixA, N);
    fillRandomMatrix(matrixB, N);
    
    // menjalankan function untuk perkalian matrix dan mencari average
    // display matrix tidak memungkinkan karena jumlah digit yang besar
    matrixMultiply(matrixA, matrixB, resultMatrix, N);
    printf("Average dari matriks hasil:\n");
    double average = findAverage(resultMatrix, N);
    printf("%.2f\n", average);

    //free memory dari setiap matrix
    free(matrixA);
    matrixA = NULL;
    free(matrixB);
    matrixB = NULL;
    free(resultMatrix);
    resultMatrix = NULL;

    return 0;
}

// Function dibawah ini perlu diubah signature-nya untuk menerima double**
void printMatrix(double** matrix, int rows) {
    if (matrix == NULL) {
        printf("Matriks NULL (tidak ada).\n");
        return;
    }
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < rows; j++) {
            printf("%.2f ", matrix[i][j]); // Cetak dengan 2 angka desimal
        }
        printf("\n");
    }
}

void matrixMultiply(double** matrixA, double** matrixB, double** resultMatrix, int n) {
    // Cek apakah matriks input atau output adalah NULL
    if (matrixA == NULL || matrixB == NULL || resultMatrix == NULL) {
        printf("Error: Salah satu matriks NULL (tidak ada).\n");
        return; // Keluar dari fungsi void
    }

    // Cek dimensi non-negatif
    if (n <= 0) {
        printf("Error: Dimensi matriks harus positif.\n");
        return; // Keluar dari fungsi void
    }

    // Inisialisasi matriks hasil dengan nol
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            resultMatrix[i][j] = 0.0;
        }
    }

    // Lakukan perkalian matriks
    for (int i = 0; i < n; i++) { // Iterasi melalui baris matriks hasil (dan baris A)
        for (int j = 0; j < n; j++) { // Iterasi melalui kolom matriks hasil (dan kolom B)
            // Hitung elemen resultMatrix[i][j]
            for (int k = 0; k < n; k++) { // Iterasi melalui dimensi 'dalam' (m)
                resultMatrix[i][j] += matrixA[i][k] * matrixB[k][j];
            }
        }
    }
}

double findAverage(double** matrix, int rows) {
    double sum = 0.0;
    long long count = 0;
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < rows; j++) {
            sum += matrix[i][j];
            count++;
        }
    }
    return sum / count;
}

void fillRandomMatrix(double** matrix, int rows) {
    srand(time(NULL));
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < rows; j++) {
            matrix[i][j] = rand() % 10;
        }
    }
}
```

Screenshot hasil
![image](https://hackmd.io/_uploads/Byque1tyge.png)
