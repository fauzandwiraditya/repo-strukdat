
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
<img width="527" height="655" alt="Image" src="https://github.com/user-attachments/assets/fe1ffb57-0c35-404f-8412-c4113e608acc" />

Program pada soal ini bertujuan untuk menyimpan data mahasiswa dengan jumlah maksimal sepuluh orang menggunakan sebuah array berisi elemen-elemen bertipe struct. Setiap data mahasiswa memiliki beberapa field, yaitu nama, NIM, nilai UTS, nilai UAS, nilai tugas, dan nilai akhir. Untuk menghitung nilai akhir, program membutuhkan sebuah fungsi khusus, yang menerima nilai UTS, UAS, dan tugas sebagai parameter, lalu mengolahnya berdasarkan rumus 0.3 × UTS + 0.4 × UAS + 0.3 × tugas.

#### Full code Screenshot:
<img width="674" height="908" alt="Image" src="https://github.com/user-attachments/assets/c7fe4681-564a-4a65-88d1-fe865dac866e" />


### 2. [Soa2]

*pelajaran.h*
```C++
#ifndef PELAJARAN_H_INCLUDED
#define PELAJARAN_H_INCLUDED

#include <string>
using namespace std;

struct pelajaran {
    string namaMapel;
    string kodeMapel;
};

pelajaran create_pelajaran(string namapel, string kodepel);
void tampil_pelajaran(pelajaran pel);

#endif
```
*pelajaran.cpp*

```C++
#include <iostream>
#include "pelajaran.h"
using namespace std;

pelajaran create_pelajaran(string namapel, string kodepel){
    pelajaran p;
    p.namaMapel = namapel;
    p.kodeMapel = kodepel;
    return p;
}

void tampil_pelajaran(pelajaran pel){
    cout << "nama pelajaran : " << pel.namaMapel << endl;
    cout << "nilai : " << pel.kodeMapel << endl;
}
```
*main.cpp*

```C++

#include <iostream>
#include "pelajaran.h"
using namespace std;

int main(){
    string namapel = "Struktur Data";
    string kodepel = "STD";

    pelajaran pel = create_pelajaran(namapel, kodepel);

    tampil_pelajaran(pel);

    return 0;
}

```
#### Output:
<img width="366" height="132" alt="Image" src="https://github.com/user-attachments/assets/1f85085c-e319-43f0-adb3-edd4154f8bd9" />

#### Full code Screenshot:
<img width="668" height="437" alt="Image" src="https://github.com/user-attachments/assets/ffe7dcbb-02a7-46e3-abb4-613f6e2ba164" />
<img width="682" height="454" alt="Image" src="https://github.com/user-attachments/assets/d2297998-7411-4227-9177-895c4321935f" />
<img width="646" height="406" alt="Image" src="https://github.com/user-attachments/assets/09d19a57-013c-48ee-b2b8-8853ce9c8e33" />


### 3. [Soa3]

```C++
#include <iostream>
using namespace std;

void tampilArray(int A[3][3]){
    for(int i=0; i<3; i++){
        for(int j=0; j<3; j++){
            cout << A[i][j] << " ";
        }
        cout << endl;
    }
}

void tukarPosisi(int A[3][3], int B[3][3], int x, int y){
    int temp = A[x][y];
    A[x][y] = B[x][y];
    B[x][y] = temp;
}

void tukarPointer(int *p1, int *p2){
    int temp = *p1;
    *p1 = *p2;
    *p2 = temp;
}

int main(){
    int arr1[3][3] = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}
    };

    int arr2[3][3] = {
        {10, 11, 12},
        {13, 14, 15},
        {16, 17, 18}
    };

    int a = 50;
    int b = 99;
    int *p1 = &a;
    int *p2 = &b;

    cout << "Array 1 awal:\n";
    tampilArray(arr1);
    cout << "\nArray 2 awal:\n";
    tampilArray(arr2);

    cout << "\nMenukar posisi (1,1) pada kedua array...\n";
    tukarPosisi(arr1, arr2, 1, 1);

    cout << "Array 1 setelah ditukar:\n";
    tampilArray(arr1);
    cout << "\nArray 2 setelah ditukar:\n";
    tampilArray(arr2);

    cout << "\nNilai pointer sebelum ditukar: p1=" << *p1 << ", p2=" << *p2 << endl;
    tukarPointer(p1, p2);
    cout << "Nilai pointer sesudah ditukar:  p1=" << *p1 << ", p2=" << *p2 << endl;

    return 0;
}

```
#### Output:
<img width="602" height="564" alt="Image" src="https://github.com/user-attachments/assets/776a682e-5c26-406d-8df1-6cb90cf937f2" />

Program ini bekerja dengan tiga bagian utama: menampilkan array 2D, menukar elemen tertentu dari dua array, dan menukar nilai dua variabel melalui pointer. Pada bagian awal, program mendefinisikan fungsi tampilArray yang bertugas mencetak isi sebuah array 3×3 ke layar dengan format baris dan kolom sehingga isi matriks terlihat rapi. Berikutnya ada fungsi tukarPosisi, yang menerima dua array dan sebuah indeks baris serta kolom. Fungsi ini akan mengambil elemen pada posisi yang sama dari kedua array, kemudian menukarnya menggunakan variabel sementara. Dengan cara itu, elemen pada indeks tersebut tertukar tanpa mengubah elemen lain.

#### Full code Screenshot:
<img width="678" height="897" alt="Image" src="https://github.com/user-attachments/assets/3bf730c1-bee0-4cdf-9ea9-ef517fcc2dbb" />

## Kesimpulan
Secara keseluruhan, program ini menunjukkan penerapan dasar manipulasi data menggunakan array 2D dan pointer dalam C++. Dua buah array berukuran 3×3 digunakan sebagai contoh untuk memperlihatkan bagaimana elemen-elemen di dalamnya dapat ditampilkan dengan rapi dan ditukar pada posisi tertentu melalui sebuah fungsi khusus.
## Referensi
https://cplusplus.com/doc/tutorial/structures/
https://cplusplus.com/doc/tutorial/functions2/
https://cplusplus.com/doc/tutorial/arrays/

