
# <h1 align="center">Laporan Praktikum Modul 3 Abstract Data Type (ADT) </h1>
<p align="center">Fauzan Dwi Raditya</p>

## Dasar Teori

Abstract Data Type (ADT), yaitu sebuah tipe data yang didefinisikan berdasarkan apa yang bisa dilakukan, bukan bagaimana cara ia disimpan atau diimplementasikan. ADT terdiri dari dua bagian utama: TYPE (struktur data) dan PRIMITIF (operasi-operasi dasar) yang boleh dilakukan terhadap tipe tersebut. ADT bersifat statik, artinya hanya menjelaskan spesifikasi dan aturan sebuah tipe, bukan implementasinya.
## Guided 

### 1. [Code mahasiswa.h]

*Code mahasiswa.h*
```C++
#ifndef MAHASISWA_H_INCLUDED 
#define MAHASISWA_H_INCLUDED 

struct mahasiswa { 
    char nim[10]; 
    int nilai1, nilai2; 
};

void inputMhs(mahasiswa &m); 
float rata2(mahasiswa m); 

#endif
}
```
*code mahasiswa.cpp*
```C++
#include <iostream>
#include "mahasiswa.h"
void inputMhs(mahasiswa &m){ 
    cout << "input nama = "; 
    cin >> (m).nim; 
    cout << "input nilai = "; 
    cin >> (m).nilai1; 
    cout << "input nilai2 = "; 
    cin >> (m).nilai2;
} 
 
float rata2(mahasiswa m){ 
  return float(m.nilai1+m.nilai2)/2; 
}
```

*code main.cpp*
```C++
#include <iostream>
using namespace std;

struct mahasiswa{ 
    char nim[10]; 
    int nilai1,nilai2;
};

void inputMhs(mahasiswa &m); 
float rata2(mahasiswa m);

int main() { 
mahasiswa mhs; 
inputMhs(mhs); 
    cout << "rata-rata = " << rata2(mhs); 
return 0; 
}

void inputMhs(mahasiswa &m){ 
    cout << "input nama = "; 
    cin >> m.nim; 
    cout << "input nilai = "; 
    cin >> m.nilai1; 
    cout << "input nilai2 = ";
    cin >> m.nilai2; 
} 
float rata2(mahasiswa m){ 
return float(m.nilai1+m.nilai2)/2; 
}
```
Program tersebut membuat sebuah struktur mahasiswa yang berisi NIM, nilai pertama, dan nilai kedua. Fungsi inputMhs() digunakan untuk meminta input dari pengguna dan mengisi data mahasiswa tersebut. Fungsi rata2() menghitung rata-rata dari dua nilai yang dimasukkan. Di dalam main(), program membuat satu objek mahasiswa, meminta pengguna mengisi datanya melalui inputMhs(), lalu menampilkan hasil rata-ratanya dengan memanggil rata2(). Program ini pada dasarnya hanya untuk menerima data mahasiswa dan menghitung nilai rata-ratanya.
## Unguided 

### 1. [Soal]

```C++
#include <iostream>
#include <string>
using namespace std;

struct Mahasiswa {
    string nama;
    string nim;
    float uts, uas, tugas, nilaiAkhir;
};

float hitungNilaiAkhir(float uts, float uas, float tugas) {
    return (0.3 * uts) + (0.4 * uas) + (0.3 * tugas);
}

int main() {
    Mahasiswa mhs[10];
    int jumlah;

    cout << "Masukkan jumlah mahasiswa (max 10): ";
    cin >> jumlah;

    if(jumlah > 10) jumlah = 10;

    for(int i = 0; i < jumlah; i++) {
        cout << "\nData mahasiswa ke-" << i+1 << endl;

        cout << "Nama  : ";
        cin >> mhs[i].nama;

        cout << "NIM   : ";
        cin >> mhs[i].nim;

        cout << "UTS   : ";
        cin >> mhs[i].uts;

        cout << "UAS   : ";
        cin >> mhs[i].uas;

        cout << "Tugas : ";
        cin >> mhs[i].tugas;

        mhs[i].nilaiAkhir = hitungNilaiAkhir(mhs[i].uts, mhs[i].uas, mhs[i].tugas);
    }

    cout << "\n=== DATA MAHASISWA ===\n";
    for(int i = 0; i < jumlah; i++) {
        cout << "\nMahasiswa " << i+1 << endl;
        cout << "Nama        : " << mhs[i].nama << endl;
        cout << "NIM         : " << mhs[i].nim << endl;
        cout << "Nilai Akhir : " << mhs[i].nilaiAkhir << endl;
    }

    return 0;
}

```
#### Output:

Kode di atas berfungsi untuk menghitung hasil dari dua bilangan yang dimasukkan oleh pengguna. Setelah pengguna mengetikkan dua angka, program akan menampilkan hasil penjumlahan, pengurangan, perkalian, dan pembagiannya. Semua proses tersebut ditampilkan langsung di layar menggunakan perintah `cout`.


#### Full code Screenshot:
<img width="679" height="426" alt="image" src="https://github.com/user-attachments/assets/734dbdcd-69a4-454e-9a9f-82a2caad45f5" />

### 2. [Soa2]

```C++
#include <iostream>
using namespace std;

int main() {
    int angka;
    cout <<"masukkan angka (0 - 100): ";
    cin >> angka;

    cout << angka << " : ";

    if (angka == 0 ) cout << "Nol";
    else if (angka == 100 ) cout << "Seratus";
    else {
        string satuan[] = {"", "Satu", "Dua", "Tiga", "Empat", "Lima", "Enam", "Tujuh", "Delapan", "Sembilan"};
        int puluh = angka / 10;
        int satu = angka % 10;

        if (angka < 10) cout << satuan[satu];
        else if (angka < 20){
            if (angka == 10) cout << "Sepuluh";
            else if (angka == 11) cout << "Sebelas";
            else cout << satuan[satu] << " Belas";
        }
        else {
            cout << satuan[puluh] << " Puluh";
            if (satu > 0) cout << " " << satuan[satu];
        }
        
    }
    cout << endl;
    return 0;
}
```
#### Output:
<img width="498" height="88" alt="image" src="https://github.com/user-attachments/assets/9f180cfe-4ab2-4dd7-926b-57466db8fbff" />
Kode di atas digunakan untuk mengubah angka yang dimasukkan pengguna menjadi bentuk tulisan. Saat program dijalankan, pengguna diminta mengetikkan angka antara 0 sampai 100. Setelah itu, program akan menampilkan hasilnya dalam bentuk kata, misalnya jika memasukkan angka 45 maka akan muncul “Empat Puluh Lima”. Prosesnya dilakukan dengan membagi angka menjadi puluhan dan satuan, lalu menyesuaikan hasilnya menggunakan kondisi `if` dan `else if` agar kata yang muncul sesuai dengan angkanya.

#### Full code Screenshot:
<img width="1144" height="757" alt="image" src="https://github.com/user-attachments/assets/0a9be719-9de9-4971-9aa9-e9c58dafd3fe" />

### 3. [Soa3]

```C++
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Input: ";
    cin >> n;
    cout << "Output:\n";

    for (int i = n; i >= 1; i--) {
    
        for (int s = 0; s < (n - i) * 2; s++)
            cout << " ";


        for (int j = i; j >= 1; j--)
            cout << j << " ";

        cout << "* ";

        for (int j = 1; j <= i; j++)
            cout << j << " ";

        cout << endl;
    }

    return 0;
}
```
#### Output:
<img width="513" height="337" alt="image" src="https://github.com/user-attachments/assets/42ec5ef2-40ce-4ad5-9bbe-28e16d6f3429" />
Kode di atas digunakan untuk menampilkan pola angka berbentuk segitiga terbalik dengan tanda bintang di tengahnya. Program meminta pengguna memasukkan sebuah angka sebagai batas tinggi pola. Kemudian, melalui perulangan `for`, program mencetak angka menurun dari nilai input hingga 1 di sisi kiri, menampilkan tanda `*` di tengah, lalu mencetak angka naik kembali di sisi kanan. Setiap baris bergeser ke kanan dengan menambahkan spasi agar pola terlihat rapi dan simetris.

#### Full code Screenshot:
<img width="525" height="676" alt="image" src="https://github.com/user-attachments/assets/e2c8b71b-813a-48d5-a0c9-b4a644ecde03" />


## Kesimpulan
Dari ketiga program di atas, bisa disimpulkan bahwa setiap kode memiliki fungsi berbeda tapi sama-sama membantu memahami dasar logika pemrograman C++. Program pertama mengajarkan cara melakukan operasi aritmatika sederhana dengan input dari pengguna. Program kedua memperkenalkan penggunaan percabangan `if` untuk menampilkan hasil dalam bentuk tulisan sesuai angka yang dimasukkan. Sedangkan program ketiga menunjukkan penerapan perulangan `for` untuk membuat pola angka yang menarik dan terstruktur. Dari ketiganya, bisa dipahami bahwa logika, struktur, serta alur berpikir dalam menyusun kode sangat penting agar program bisa berjalan sesuai yang diinginkan.

## Referensi
GeeksforGeeks. (n.d.). C++ Arithmetic Operators. Diakses pada 23 Oktober 2025, dari https://www.geeksforgeeks.org/cpp/cpp-arithmetic-operators/
PrepInsta. (n.d.). C++ program to convert digit number to words. Diakses pada 23 Oktober 2025, dari https://prepinsta.com/cpp-program/convert-digit-number-to-words/
Programiz. (n.d.). C++ Programs to Create Pyramid and Pattern. Diakses pada 23 Oktober 2025, dari https://www.programiz.com/cpp-programming/examples/pyramid-pattern
