# Case Study I - C++ Introduction
> Pembuat Soal: MF
```
Nama  : [Innezahra Aurellia Titani]
NPM   : [2306168965]
```

Mengikuti tren perkembangan teknologi, Ryan mengimplementasikan sistem terbenam (*embedded systems*) berbasis Mikrokontroler (Mikon) untuk memantau berbagai sudut dari kafe-kafenya menggunakan sensor. Sebelum mengimplementasikan *million dollar idea* ini, Ryan mensimulasikan sistem tersebut.

```cpp
// Gunakan cuplikan ini di kode anda.

class Sensor {
    // Lengkapi
};

class Mikon {
    // Lengkapi
};

void printMenu() {
    puts(
        "1. Tambah Sensor\n"
        "2. Ubah Status Sensor\n"
        "3. Update\n"
        "4. Exit"
    );
    std::cout << ">> ";
}

void printStatus() {
    puts(
        "0. ACTIVE\n"
        "1. DEAD\n"
        "2. MAINTENANCE"
    );
    std::cout << ">> ";
}

int main() {
    srand(time(NULL));

    // Implementasikan Mikon
    Mikon mikon = Mikon();

    int option = 0;
    do {
        std::cout << "-----------------\n";
        std::cout << "= Gosling Corp. = \n";
        printMenu();

        std::string name;

        float lower, upper;
        int status_option;
        int device_index;
        
        std::cin >> option;

        switch (option) {

            case 1:
            std::cout << "Name? ";
            std::cin >> name;
            std::cout << "Batasan sensor? (lower upper): ";
            std::cin >> lower >> upper;
            // Implementasikan ini
            // mikon.addSensor(Sensor(name, lower, upper));
            break;

            case 2:
            mikon.printSensors();
            std::cout << "Sensor index? ";
            std::cin >> device_index;
            std::cout << "= Choose Status = \n";
            printStatus();
            std::cin >> status_option;
            if (status_option < 0 || status_option > 2) {
                std::cout << "Bukan status!\n";
                break;
            }
            // Implementasikan ini
            // mikon.setSensorStatus(device_index, (Status)status_option);
            break;

            case 3:
            // Implementasikan ini
            // mikon.update();
            break;

            case 4:
            break;
            default:
                std::cout << "Pilihan tidak valid!\n";
        }
        std::cout << "-----------------\n";
    } while (option != 4);
}
```

Sistem tersebut memiliki sebuah mikrokontroler `mikon` yang terhubung ke berbagai sensor. Setiap sensor dapat membaca bacaan tertentu berdasarkan spesifikasi batasannya masing-masing (batasan bawah dan batasan atas). Tidak hanya itu, untuk keperluan manajemen, setiap sensor dapat memiliki status yang dapat berupa `ACTIVE`, `DEAD`, dan `MAINTENANCE`. Sensor yang berstatus `DEAD` tidak membaca apapun dan tidak dianggap sementara itu sensor dengan status `MAINTENANCE` akan memberikan peringatan mengenai statusnya.

Program utama memiliki menu untuk memilih aksi yang dilakukan pengguna. Pengguna dapat menambahkan sensor baru ke sistem, mengubah status sensor yang ada, dan melakukan *update* di mana setiap sensor yang ada melakukan pembacaan. 

Berdasarkan ini, Ryan meminta anda (seorang programmer langganannya) untuk mengimplementasikan detail sistem ini dengan menggunakan `class` untuk mencapai *object-oriented programming* dasar dalam C++.

## Spesifikasi

### Enum Status
- Status merupakan enum yang berisi `ACTIVE`, `DEAD`, dan `MAINTENANCE`. Pastikan isi enum anda memiliki urutan yang sesuai.

### Class Sensor
- Menyimpan sebuah `std::string` nama dan dua buah `float` lower serta upper yang berupa batasan bacaan sensor. Sebuah sensor hanya akan menghasilkan bacaan di antara kedua nilai tersebut. Pastikan data-data tersebut memiliki *access specifier* yang sesuai sebagai bentuk *abstraction*.
- Menyimpan sebuah status yang merupakan `enum Status` yang telah dibuat. Sensor yang baru ditambahkan memiliki status `ACTIVE` secara *default*.
- Memiliki **constructor** yang mengisi data-data dari sensor tersebut ketika ditambahkan. 
- Memiliki method `printDetail()` yang akan menampilkan informasi yang dimiliki sensor (nama dan batasan).
- Memiliki method `read()` yang akan membaca data acak di antara lower dan upper.
    ```cpp
    float read() {
        float result = lower + static_cast <float> (rand()) / ( static_cast <float> (RAND_MAX / (upper - lower)));
        std::cout << "Read Result: " << result << "\n";
        return result;
    }
    ```

### Class Mikon (Microcontroller)
- Memiliki sebuah dynamic vector array yang menyimpan sensor-sensor yang ada.
- Memiliki sebuah method `addSensor(Sensor)` yang menambahkan `Sensor` ke dalam array daftar sensor.
- Memiliki sebuah method `setSensorStatus(index, newStatus)` yang mengubah status sensor pada urutan `index` ke `newStatus`.
- Memiliki method `printSensors()` yang melakukan printing detail setiap sensor yang ada (gunakan `printDetail()` yang dimiliki `Sensor`) serta indeksnya pada array. 
- Memiliki method `update()` untuk melakukan operasi pembacaan pada setiap sensor yang tidak berstatus `DEAD`. Detail dari sensor di-print lalu sensor melakukan pembacaan menggunakan `read()`. Jika sensor berstatus `MAINTENANCE`, sensor tidak melakukan pembacaan dan melakukan printing "UNDER MAINTENANCE".  

---

## Contoh
```
-----------------
= Gosling Corp. = 
1. Tambah Sensor
2. Ubah Status Sensor
3. Update
4. Exit
>> 1
Name? Toilet
Batasan sensor? (lower upper): 0 100
-----------------
```

Pengguna menambahkan sensor baru bernama "Toilet" dan memiliki batasan 0 hingga 100.

```
-----------------
= Gosling Corp. = 
1. Tambah Sensor
2. Ubah Status Sensor
3. Update
4. Exit
>> 1
Name? Kafe 
Batasan sensor? (lower upper): -100 200
-----------------
```

Pengguna menambahkan sensor kedua bernama "Kafe" dengan batasan -100 hingga 200.

```
-----------------
= Gosling Corp. = 
1. Tambah Sensor
2. Ubah Status Sensor
3. Update
4. Exit
>> 3
- Sensor Readings -
Sensor - Toilet - Range: 0 | 100
-> Read Result: 56.6698
Sensor - Kafe - Range: -100 | 200
-> Read Result: -25.3822
-----------------
```

Pengguna melakukan `update` dengan memilih `3`. Setiap sensor di-print detail serta hasil bacaan yang berupa angka acak dalam rentangnya.

```
-----------------
= Gosling Corp. =
1. Tambah Sensor
2. Ubah Status Sensor
3. Update
4. Exit
>> 2
0. Sensor - Toilet - Range: 0 | 100
1. Sensor - Kafe - Range: -100 | 200
Sensor index? 0
= Choose Status =
0. ACTIVE
1. DEAD
2. MAINTENANCE
>> 1
-----------------
```

Pengguna memilih untuk mengubah status sensor. Setiap sensor yang ada di-list dengan indeksnya. Pengguna lalu memilih untuk mengubah sensor indeks 0 ke `DEAD`

```
-----------------
= Gosling Corp. =
1. Tambah Sensor
2. Ubah Status Sensor
3. Update
4. Exit
>> 2
0. Sensor - Toilet - Range: 0 | 100
1. Sensor - Kafe - Range: -100 | 200
Sensor index? 1
= Choose Status =
0. ACTIVE
1. DEAD
2. MAINTENANCE
>> 2
-----------------
```

Pengguna memilih untuk mengubah status sensor lagi. Kini pengguna memilih untuk mengubah sensor indeks 1 ke `MAINTENANCE`

```
-----------------
= Gosling Corp. =
1. Tambah Sensor
2. Ubah Status Sensor
3. Update
4. Exit
>> 3
- Sensor Readings -
Sensor - Kafe - Range: -100 | 200
-> UNDER MAINTENANCE
-----------------
```

Pengguna memilih melakukan `update` lagi. Kali sensor "Toilet" tidak lagi ditampilkan karena berstatus `DEAD`. Sensor "Kafe" masih di-print namun karena statusnya, tidak membaca melainkan melakukan printing "UNDER MAINTENANCE".

```
-----------------
= Gosling Corp. =
1. Tambah Sensor
2. Ubah Status Sensor
3. Update
4. Exit
>> 4
-----------------
```
Pengguna keluar dari program.


## Jawaban
### Kode
```cpp
#include <iostream>
#include <string>
#include <ctime>
#include <vector>

enum Status {
    ACTIVE,
    DEAD,
    MAINTENANCE
};

// Class Sensor
class Sensor {
private:
    std::string name;
    float lower;
    float upper;
    Status status;

public:
    // Constructor for sensor
    Sensor(std::string name, float lower, float upper)
        : name(name), lower(lower), upper(upper), status(ACTIVE) {}

    //method untuk print detail sensor
    void printDetail() {
        std::cout << "Sensor - " << name << " - Range: " << lower << " | " << upper << "\n";
    }

    float read() {
        float result = lower + static_cast<float>(rand()) / (static_cast<float>(RAND_MAX / (upper - lower)));
        std::cout << "-> Read Result: " << result << "\n";
        return result;
    }

    Status getStatus() {
        return status;
    }

    void setStatus(Status newStatus) {
        status = newStatus;
    }
};

// Class Mikon
class Mikon {
private:
    std::vector<Sensor> sensors;

public:
    // menambahkan sensor dengan push_back
    void addSensor(Sensor sensor) {
        sensors.push_back(sensor);
    }

    // method untuk menentukan status sensor sesuai enum Status
    void setSensorStatus(int index, Status newStatus) {
        if (index >= 0 && index < sensors.size()) {
            sensors[index].setStatus(newStatus);
        }
    }

    // method untuk print isi array sensor
    void printSensors() {
        for (int i = 0; i < sensors.size(); ++i) {
            std::cout << i << ". ";
            sensors[i].printDetail();
        }
    }

    // method utk update sensor
    void update() {
        std::cout << "- Sensor Readings -\n";
        for (int i = 0; i < sensors.size(); ++i) {
            Status stat = sensors[i].getStatus();
            if (stat == DEAD) {
                continue;
            }
            sensors[i].printDetail();
            if (stat == MAINTENANCE) {
                std::cout << "-> UNDER MAINTENANCE\n";
            } else {
                sensors[i].read();
            }
        }
    }
};

void printMenu() {
    puts(
        "1. Tambah Sensor\n"
        "2. Ubah Status Sensor\n"
        "3. Update\n"
        "4. Exit"
    );
    std::cout << ">> ";
}

void printStatus() {
    puts(
        "0. ACTIVE\n"
        "1. DEAD\n"
        "2. MAINTENANCE"
    );
    std::cout << ">> ";
}

int main() {
    srand(time(NULL));
    Mikon mikon;

    int option = 0;
    do {
        std::cout << "-----------------\n";
        std::cout << "= Gosling Corp. = \n";
        printMenu();

        std::string name;
        float lower, upper;
        int status_option;
        int device_index;

        std::cin >> option;

        switch (option) {
        case 1:
            std::cout << "Name? ";
            std::cin >> name;
            std::cout << "Batasan sensor? (lower upper): ";
            std::cin >> lower >> upper;
            mikon.addSensor(Sensor(name, lower, upper));
            break;

        case 2:
            mikon.printSensors();
            std::cout << "Sensor index? ";
            std::cin >> device_index;
            std::cout << "= Choose Status = \n";
            printStatus();
            std::cin >> status_option;
            if (status_option < 0 || status_option > 2) {
                std::cout << "Bukan status!\n";
                break;
            }
            mikon.setSensorStatus(device_index, (Status)status_option);
            break;

        case 3:
            mikon.update();
            break;

        case 4:
            break;

        default:
            std::cout << "Pilihan tidak valid!\n";
        }

        std::cout << "-----------------\n";
    } while (option != 4);

    return 0;
}

```

### Screenshot Program Berjalan
Output 1:
![image](https://hackmd.io/_uploads/HyGvB9Nbxl.png)

Output 2:
![image](https://hackmd.io/_uploads/SyeABqVWee.png)

Output 3:
![image](https://hackmd.io/_uploads/B11JIcN-lx.png)

Output 4:
![image](https://hackmd.io/_uploads/Syt-UqEWgg.png)

Output 5:
![image](https://hackmd.io/_uploads/BkHfUq4-ge.png)

