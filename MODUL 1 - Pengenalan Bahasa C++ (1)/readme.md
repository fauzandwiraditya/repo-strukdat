# <h1 align="center">Laporan Praktikum Modul Pengenalan Bahasa C++ (1)</h1>
<p align="center">Fauzan Dwi Raditya</p>

## Dasar Teori

Code::Blocks adalah salah satu aplikasi yang digunakan untuk menulis dan menjalankan program C++. Aplikasi ini mempermudah pengguna karena sudah dilengkapi dengan fitur editor, compiler, dan debugger dalam satu tempat. Bahasa C++ sendiri merupakan pengembangan dari bahasa C yang mendukung konsep pemrograman berorientasi objek, sehingga lebih fleksibel dan efisien untuk berbagai keperluan. Dalam penulisannya, program C++ umumnya diawali dengan baris #include <iostream>, kemudian diikuti fungsi utama main() yang berisi perintah-perintah yang akan dijalankan oleh komputer
## Guided 

### 1. [pengenalan bahasa C++ (1)]

```C++
#include <iostream>

using namespace std;

void tulis (int x){
    for (int i = 0; 1 < x; i++ ){
        cout << "Baris ke -: " << i+1 << endl;
    }
}
int main () {
    int jum;
    cout << "Jumlah baris kata: ";
    cin >> jum;
    tulis(jum);

    return 0;
}
```
Kode di atas digunakan untuk menampilkan beberapa baris teks ke layar sesuai jumlah yang dimasukkan oleh pengguna. Program meminta input berupa jumlah baris, kemudian memanggil fungsi `tulis()` untuk mencetak kalimat “Baris ke -” diikuti nomor urutnya. Proses pencetakan dilakukan menggunakan perulangan `for` dan perintah `cout` untuk menampilkan hasilnya di layar.

## Unguided 

### 1. [Soal]

```C++
#include <iostream>

using namespace std;

int main() {
    float bilangan1, bilangan2;

    cout <<"Masukkan bilangan pertama: ";
    cin >> bilangan1;
    cout<<"Masukkan bilangan kedua: ";
    cin >> bilangan2;

    cout<<"Hasil penjumlahan: "<< bilangan1 + bilangan2 << endl;
    cout<<"Hasil pengurangan: "<< bilangan1 - bilangan2 << endl;
    cout<<"Hasil perkalian: "<< bilangan1 * bilangan2 << endl;
    cout<<"Hasil pembagian: "<< bilangan1 / bilangan2 << endl;
    return 0;
}
```
#### Output:
<img width="503" height="177" alt="image" src="https://github.com/user-attachments/assets/18dea020-cd26-4fe4-ae4c-e4a671f7366e" />
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
