# <h1 align="center">Modul 7 Stack</h1>
<p align="center">Fauzan Dwi Raditya</p>

## Dasar Teori

Stack adalah struktur data linear yang bekerja dengan prinsip LIFO (Last In First Out), yaitu data yang terakhir dimasukkan akan menjadi data pertama yang dikeluarkan. Pada modul ini, stack diimplementasikan menggunakan array statis, sehingga ukuran stack bersifat tetap.
## Guided 

### 1. [Nama Topik]
**stack.h**
```C++
#ifndef STACK_TABLE
#define STACK_TABLE

#include <iostream>
using namespace std;

//ubah kapasitas sesuai kebutuhan
const int MAX = 10;

struct stackTable{
    int data[MAX];
    int top; // -1 = kosong

};

bool isEmpty(stackTable s);
bool isFull(stackTable s);
void createStack(stackTable &s);

void push(stackTable &s, int angka);
void pop(stackTable &s);
void update(stackTable &s, int posisi);
void view(stackTable s);
void searchData(stackTable s, int data);

#endif
```
**stak.cpp**
```c++
#include "stack.h"
#include <iostream>

using namespace std;

bool isEmpty(stackTable s) {
    return s.top == -1;
}

bool isFull(stackTable s){
    return s.top == MAX -1;
}

void createStack(stackTable &s) {
    s.top = -1;
}

void push(stackTable &s, int angka){
    if(isFull(s)){
        cout << "Stack Penuh!" << endl;
    } else {
        s.top++;
        s.data[s.top] = angka;
        cout << "Data " << angka << " berhasil ditambahkan kedalam stack!" << endl;
    }
}

void pop(stackTable &s){
    if(isEmpty(s)){
        cout << "Stack kosong!" << endl;
    } else {
        int val = s.data[s.top];
        s.top--;
        cout << "Data " << val << " Berhasil dihapus dari stack!" << endl;
    }
}

void update(stackTable &s, int posisi){
    if(isEmpty(s)){
        cout << "Stack kosong!" << endl;
        return;
    }
    if(posisi <= 0){
        cout << "Posisi tidak valid!" << endl;
        return;
    }

    //index = top - (posisi -1)
    int idx = s.top - (posisi -1);
    if(idx < 0 || idx > s.top){
        cout << "Posisi " << posisi << " Tidak valid!" << endl;
        return;
    }

    cout << "Update data posisi ke-" << posisi << endl;
    cout << "Masukkan angka: ";
    cin >> s.data[idx];
    cout << "Data berhasil diupdate!" << endl;
    cout << endl;
}

void view(stackTable s){
    if(isEmpty(s)){
        cout << "Stack Kosong!" << endl;
    } else {
        for(int i = s.top; i >= 0; --i){
            cout << s.data[i] << " ";
        }
    }
    cout << endl;
}

void searchData(stackTable s, int data){
    if(isEmpty(s)){
        cout << "Stack Kosong!" << endl;
        return;
    }
    cout << "Mencari data" << data << "..." << endl;
    int posisi = 1;
    bool found = false;

    for(int i = s.top; i >= 0; --i){
        if(s.data[i] == data){
            cout << "Data " << data << " ditemukan pada posisi ke-" << posisi << endl;
            cout << endl;
            found = true;
            break;
        }
        posisi++;
    }

    if(!found){
        cout << "Data " << data << " tidak ditemukan didalam stack!" << endl;
        cout << endl;
    }
}
```
**main.cpp**
```c++
#include "stack.h"
#include <iostream>

using namespace std;

int main(){
    stackTable s;
    createStack(s);

    push(s, 1);
    push(s, 2);
    push(s, 3);
    push(s, 4);
    push(s, 5);
    cout << endl;

    cout << "--- Stack setelah push ---" << endl;
    view(s);
    cout << endl;

    pop(s);
    pop(s);
    cout << endl;

    cout << "--- Stack setelah pop 2 kali ---" << endl;
    view(s);
    cout << endl;

    //Posisi dihitung dari TOP(1-based)
    update(s, 2);
    update(s, 1);
    update(s, 4);
    cout << endl;

    cout << "--- Stack setelah update ---" << endl;
    view(s);
    cout << endl;

    searchData(s, 4);
    searchData(s, 9);

    return 0;
}
```

Program ini menerapkan struktur data stack berbasis array yang menyediakan operasi utama seperti push dan pop, serta dilengkapi dengan fitur tambahan untuk melakukan pencarian dan pembaruan data.

## Unguided 

### 1. [Soal]
stack.h
```C++
#ifndef STACK_H
#define STACK_H

#include <iostream>
using namespace std;

typedef int infotype;

typedef struct {
    infotype info[20];
    int top;
} Stack;

void createStack(Stack &S);
void push(Stack &S, infotype x);
infotype pop(Stack &S);

void printInfo(Stack S);
void balikStack(Stack &S);

void pushAscending(Stack &S, infotype x);
void getInputStream(Stack &S);

#endif
```
**stack.cpp**
```c++
#include "stack.h"

void createStack(Stack &S) {
    S.top = -1;
}

void push(Stack &S, infotype x) {
    if (S.top < 19) {
        S.top++;
        S.info[S.top] = x;
    }
}

infotype pop(Stack &S) {
    infotype x = -1;
    if (S.top >= 0) {
        x = S.info[S.top];
        S.top--;
    }
    return x;
}

void printInfo(Stack S) {
    cout << "[TOP] ";
    for (int i = S.top; i >= 0; i--) {
        cout << S.info[i] << " ";
    }
    cout << endl;
}

void balikStack(Stack &S) {
    Stack temp;
    createStack(temp);

    while (S.top != -1) {
        push(temp, pop(S));
    }
    S = temp;
}

void pushAscending(Stack &S, infotype x) {
    Stack temp;
    createStack(temp);

    while (S.top != -1 && S.info[S.top] > x) {
        push(temp, pop(S));
    }

    push(S, x);

    while (temp.top != -1) {
        push(S, pop(temp));
    }
}

void getInputStream(Stack &S) {
    char c;
    cout << "Input angka (ENTER untuk berhenti): ";
    while ((c = cin.get()) != '\n') {
        if (c >= '0' && c <= '9') {
            push(S, c - '0');
        }
    }
}

```
**main.cpp**
```c++
#include "stack.h"

int main() {
    cout << "Hello world!" << endl;

    Stack S1;
    createStack(S1);

    push(S1, 3);
    push(S1, 4);
    push(S1, 8);
    pop(S1);
    push(S1, 2);
    push(S1, 3);
    pop(S1);
    push(S1, 9);

    printInfo(S1);
    cout << "balik stack" << endl;
    balikStack(S1);
    printInfo(S1);

    cout << endl;

    Stack S2;
    createStack(S2);

    pushAscending(S2, 3);
    pushAscending(S2, 4);
    pushAscending(S2, 8);
    pushAscending(S2, 2);
    pushAscending(S2, 3);
    pushAscending(S2, 9);

    printInfo(S2);
    cout << "balik stack" << endl;
    balikStack(S2);
    printInfo(S2);

    cout << endl;

    Stack S3;
    createStack(S3);

    getInputStream(S3);
    printInfo(S3);

    cout << "balik stack" << endl;
    balikStack(S3);
    printInfo(S3);

    return 0;
}

```
#### Output:
<img width="457" height="387" alt="image" src="https://github.com/user-attachments/assets/54c005a3-1ee0-47de-8a09-a3caf20151e3" />

Program ini membentuk sebuah stack, kemudian secara otomatis memasukkan deretan angka 4729601 ke dalam stack dan menampilkan isinya dari elemen paling atas hingga paling bawah. Selanjutnya, urutan stack dibalik dengan bantuan stack sementara, lalu hasilnya ditampilkan kembali.

#### Full code Screenshot:
<img width="574" height="922" alt="image" src="https://github.com/user-attachments/assets/c2fd7c24-d536-4d39-bdeb-ec5b342b979d" />
<img width="706" height="893" alt="image" src="https://github.com/user-attachments/assets/7c815c53-cf16-491e-b0b4-4cdf4715550f" />
<img width="562" height="639" alt="image" src="https://github.com/user-attachments/assets/dbafcbba-2a01-4389-9455-145e96f0fad7" />


## Kesimpulan
Stack bekerja dengan prinsip LIFO, yaitu elemen yang terakhir dimasukkan akan menjadi elemen pertama yang dikeluarkan. Pada percobaan ini dilakukan operasi dasar seperti push dan pop, serta pembuatan fungsi untuk menampilkan isi stack dan membalik urutannya. Hasilnya menunjukkan bahwa mekanisme stack berjalan sesuai konsep dan proses pembalikan data dapat dilakukan dengan baik. Praktikum ini membantu memperdalam pemahaman dalam penggunaan stack pada pemrograman.

## Referensi
https://www.geeksforgeeks.org/dsa/stack-data-structure/
https://www.programiz.com/dsa/stack
https://en.wikipedia.org/wiki/Stack_(abstract_data_type)
