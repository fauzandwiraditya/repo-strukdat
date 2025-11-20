# <h1 align="center">Laporan Praktikum Modul Pengenalan Bahasa C++ (1)</h1>
<p align="center">Fauzan Dwi Raditya</p>

## Dasar Teori
Operasi Matriks (Penjumlahan, Pengurangan, Perkalian)
## Guided 

### 1. [soal 1]

```C++
#include <iostream>
using namespace std;

int main() {
    int A[3][3], B[3][3], C[3][3];
    int i, j, k;

    cout << "Input matriks A (3x3):\n";
    for(i=0;i<3;i++)
        for(j=0;j<3;j++)
            cin >> A[i][j];

    cout << "Input matriks B (3x3):\n";
    for(i=0;i<3;i++)
        for(j=0;j<3;j++)
            cin >> B[i][j];

    cout << "\nHasil Penjumlahan A + B:\n";
    for(i=0;i<3;i++){
        for(j=0;j<3;j++){
            C[i][j] = A[i][j] + B[i][j];
            cout << C[i][j] << " ";
        }
        cout << endl;
    }

    cout << "\nHasil Pengurangan A - B:\n";
    for(i=0;i<3;i++){
        for(j=0;j<3;j++){
            C[i][j] = A[i][j] - B[i][j];
            cout << C[i][j] << " ";
        }
        cout << endl;
    }

    cout << "\nHasil Perkalian A * B:\n";
    for(i=0;i<3;i++){
        for(j=0;j<3;j++){
            C[i][j] = 0;
            for(k=0;k<3;k++)
                C[i][j] += A[i][k] * B[k][j];
            cout << C[i][j] << " ";
        }
        cout << endl;
    }

    return 0;
}

```

## Unguided 

### 2. [soal 2]

```C++
#include <iostream>
using namespace std;

int carimaksimum(int data[], int n) {
    int maks = data[0];
    for (int i = 1; i < n; i++) {
        if (data[i] > maks) 
            maks = data[i];
    }
    return maks;
}
    int cariminimum(int data[], int n) {
        int min = data[0];
        for (int i = 1; i < n; i++) {
            if (data[i] < min) 
                min = data[i];
        }
        return min;
}

void hitungratarata(int data[], int n) {
    float jumlah = 0;
    for(int i = 0; i < n; i++){
        jumlah = jumlah + data[i];
    }
    float rata = jumlah / n;
    cout << "nilai rata-rata = " << rata << endl;
}

int main() {
    int arr[] = {11, 8, 5, 7, 12, 26, 3, 54, 33, 55};
    int n = sizeof(arr) / sizeof(arr[0]);
    int pilih;

    do {
        cout << "\n--- menu program array ---" << endl;
        cout << "1. tampilkan isi array" << endl;
        cout << "2. cari nilai maksimum" << endl;
        cout << "3. cari nilai minimum" << endl;
        cout << "4. hitung nilai rata-rata" << endl;
        cout << "5. keluar" << endl;
        cout << "masukan pilihan : ";
        cin >> pilih;

        switch(pilih) {
            case 1:
            cout << "isi array : ";
            for (int i = 0; i < n; i++) {
                cout << arr[i] << " ";
            }
            cout << endl;
            break;
            case 2:
            cout << "nilai maksimum = " << carimaksimum(arr, n) << endl;
            break;
            case 3:
            cout << "nilai minimum = " << cariminimum(arr, n) << endl;
            break;
            case 4:
            hitungratarata(arr, n);
            break;
            case 5:
            cout << "trima kasih, program selesai" << endl;
            break;
            default:
            cout << "pilihan tidak tersedia" << endl;
        }
    } while (pilih != 5);
    return 0;
    }

```
#### Output:
<img width="606" height="396" alt="image" src="https://github.com/user-attachments/assets/64373269-2f0d-46ff-bb81-85d14be1a09a" />

Kode tersebut merupakan program C++ yang melakukan beberapa operasi dasar pada array menggunakan fungsi. Program menyimpan data dalam sebuah array berisi 10 angka, lalu menyediakan menu pilihan untuk menampilkan isi array, mencari nilai maksimum, mencari nilai minimum, dan menghitung rata-rata.

#### Full code Screenshot:
<img width="643" height="885" alt="image" src="https://github.com/user-attachments/assets/adbfa453-fdc0-4bdc-9861-cc9d23d0bb2b" />

### 3. [Soa 3]

```C++
#include <iostream>
using namespace std;

int cariMinimum(int arr[], int n) {
    int mn = arr[0];
    for(int i=1; i<n; i++)
        if(arr[i] < mn) mn = arr[i];
    return mn;
}

int cariMaksimum(int arr[], int n) {
    int mx = arr[0];
    for(int i=1; i<n; i++)
        if(arr[i] > mx) mx = arr[i];
    return mx;
}

void hitungRataRata(int arr[], int n) {
    float total = 0;
    for(int i=0; i<n; i++)
        total += arr[i];
    cout << "Rata-rata = " << total / n << endl;
}

int main() {
    int arrA[10] = {11, 8, 5, 7, 12, 26, 3, 54, 33, 55};
    int pilih;

    do {
        cout << "\n--- Menu Program Array ---\n";
        cout << "1. Tampilkan isi array\n";
        cout << "2. Cari nilai maksimum\n";
        cout << "3. Cari nilai minimum\n";
        cout << "4. Hitung nilai rata-rata\n";
        cout << "5. Keluar\n";
        cout << "Pilih menu: ";
        cin >> pilih;

        switch(pilih) {
            case 1:
                cout << "Isi array: ";
                for(int i=0;i<10;i++) cout << arrA[i] << " ";
                cout << endl;
                break;
            case 2:
                cout << "Nilai maksimum = " << cariMaksimum(arrA, 10) << endl;
                break;
            case 3:
                cout << "Nilai minimum = " << cariMinimum(arrA, 10) << endl;
                break;
            case 4:
                hitungRataRata(arrA, 10);
                break;
            case 5:
                cout << "Program selesai.\n";
                break;
            default:
                cout << "Menu tidak valid!\n";
        }
    } while(pilih != 5);

    return 0;
}

```
#### Output:
<img width="499" height="279" alt="image" src="https://github.com/user-attachments/assets/88d29cd9-0c83-4f02-a31c-c71442e56b51" />
Kode tersebut merupakan program C++ yang melakukan beberapa operasi dasar pada array menggunakan fungsi dan menu interaktif. Program dimulai dengan mendefinisikan tiga fungsi, yaitu cariMinimum() untuk menemukan nilai terkecil dalam array, cariMaksimum() untuk menemukan nilai terbesar, dan hitungRataRata() untuk menghitung nilai rata-rata elemen array. Ketiga fungsi ini bekerja dengan cara melakukan perulangan dan memproses setiap elemen untuk mendapatkan hasilnya. Pada fungsi main,
#### Full code Screenshot:
<img width="676" height="903" alt="image" src="https://github.com/user-attachments/assets/c1aa190f-9b82-4ccb-a565-9dfa7907bdba" />


## Kesimpulan
Ketiga program di atas menunjukkan penerapan dasar struktur data dan pemrograman dalam C++. Program pertama membahas cara melakukan operasi pada matriks 3×3 seperti penjumlahan, pengurangan, dan perkalian, yang melatih pemahaman tentang array dua dimensi dan perulangan bersarang
## Referensi
[GeeksforGeeks. (n.d.). C++ Arithmetic Operators. Diakses pada 23 Oktober 2025, dari https://www.geeksforgeeks.org/cpp/cpp-arithmetic-operators/
](https://www.geeksforgeeks.org/cpp/cpp-program-to-find-the-minimum-and-maximum-element-of-an-array/?utm_source=chatgpt.com)
[PrepInsta. (n.d.). C++ program to convert digit number to words. Diakses pada 23 Oktober 2025, dari https://prepinsta.com/cpp-program/convert-digit-number-to-words/
](https://www.programiz.com/cpp-programming/examples/average-arrays?utm_source=chatgpt.com)
