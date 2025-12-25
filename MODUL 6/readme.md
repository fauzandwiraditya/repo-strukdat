# <h1 align="center">Modul 6 DOUBLY LINKED LIST (BAGIAN PERTAMA)</h1>
<p align="center">Arvinanto Bahtiar</p>

## Dasar Teori

Doubly Linked list adalah linked list yang masing – masing elemen nya memiliki 2 successor, yaitu
successor yang menunjuk pada elemen sebelumnya (prev) dan successor yang menunjuk pada elemen
sesudahnya (next).
## Guided 

### 1. [Nama Topik]

```C++
#include <iostream>
#define Nil NULL
using namespace std;

typedef int infotype; // Definisikan tipe data infotype sebagai integer untuk menyimpan informasi elemen
typedef struct elmlist *address; // Definisikan tipe address sebagai pointer ke struct elmlist

struct elmlist {
    infotype info; // Deklarasikan field info untuk menyimpan data elemen
    address next;
    address prev;
};

struct List { 
    address first; 
    address last; 
}; 

void insertFirst(List &L, address P) { 
    P->next = L.first; // Set pointer next dari P ke elemen pertama saat ini
    P->prev = Nil; // Set pointer prev dari P ke Nil karena menjadi elemen pertama
    if (L.first != Nil) L.first->prev = P; // Jika list tidak kosong, set prev elemen pertama lama ke P
    else L.last = P; // Jika list kosong, set last juga ke P
    L.first = P; // Update first list menjadi P
} 

void insertLast(List &L, address P) { 
    P->prev = L.last; // Set pointer prev dari P ke elemen terakhir saat ini
    P->next = Nil; // Set pointer next dari P ke Nil karena menjadi elemen terakhir
    if (L.last != Nil) L.last->next = P; // Jika list tidak kosong, set next elemen terakhir lama ke P
    else L.first = P; // Jika list kosong, set first juga ke P
    L.last = P; // Update last list menjadi P
} 

void insertAfter(List &L, address P, address R) { // Definisikan fungsi insertAfter untuk menyisipkan elemen setelah R
    P->next = R->next; // Set pointer next dari P ke elemen setelah R
    P->prev = R; // Set pointer prev dari P ke R
    if (R->next != Nil) R->next->prev = P; // Jika ada elemen setelah R, set prev elemen tersebut ke P
    else L.last = P; // Jika R adalah terakhir, update last menjadi P
    R->next = P; // Set next dari R ke P
}

address alokasi(infotype x) { // Definisikan fungsi alokasi untuk membuat elemen baru
    address P = new elmlist; // Alokasikan memori baru untuk elemen
    P->info = x; // Set info elemen dengan nilai x
    P->next = Nil; // Set next elemen ke Nil
    P->prev = Nil; // Set prev elemen ke Nil
    return P; 
} 

void printInfo(List L) { // Definisikan fungsi printInfo untuk mencetak isi list
    address P = L.first; // Set P ke elemen pertama list
    while (P != Nil) { // Loop selama P tidak Nil
        cout << P->info << " "; // Cetak info dari P 
        P = P->next; // Pindah ke elemen berikutnya
    } 
    cout << endl; 
}

int main() { 
    List L; 
    L.first = Nil; 
    L.last = Nil;
    address P1 = alokasi(1); 
    insertFirst(L, P1); 
    address P2 = alokasi(2); 
    insertLast(L, P2); 
    address P3 = alokasi(3); 
    insertAfter(L, P3, P1); 
    printInfo(L); 
    return 0; 
}
```
Program ini menunjukkan penggunaan Doubly Linked List untuk menyimpan data integer dengan operasi penambahan elemen di awal, akhir, dan setelah elemen tertentu, serta menampilkan isi list. Setiap node terhubung dua arah sehingga pengelolaan data menjadi lebih fleksibel dan dinamis.
## Unguided 

### 1. [Soal]
**Doublylist.h**
```C++
#ifndef DOUBLYLIST_H
#define DOUBLYLIST_H

#include <iostream>
#include <string>
using namespace std;

#define Nil NULL

struct kendaraan {
    string nopol;
    string warna;
    int thnBuat;
};

typedef kendaraan infotype;
typedef struct elmlist *address;

struct elmlist {
    infotype info;
    address next;
    address prev;
};

struct List {
    address First;
    address Last;
};

void CreateList(List &L);
address alokasi(infotype x);
void dealokasi(address &P);
void insertLast(List &L, address P);
void printInfo(List L);
address findElm(List L, string nopol);
void deleteFirst(List &L, address &P);
void deleteLast(List &L, address &P);
void deleteAfter(address Prec, address &P);

#endif


```
**Doublylist.cpp**
```c++
#include "Doublylist.h"

void CreateList(List &L) {
    L.First = Nil;
    L.Last = Nil;
}

address alokasi(infotype x) {
    address P = new elmlist;
    P->info = x;
    P->next = Nil;
    P->prev = Nil;
    return P;
}

void dealokasi(address &P) {
    delete P;
    P = Nil;
}

void insertLast(List &L, address P) {
    if (L.First == Nil) {
        L.First = P;
        L.Last = P;
    } else {
        P->prev = L.Last;
        L.Last->next = P;
        L.Last = P;
    }
}

void printInfo(List L) {
    address P = L.First;
    while (P != Nil) {
        cout << "No Polisi : " << P->info.nopol << endl;
        cout << "Warna     : " << P->info.warna << endl;
        cout << "Tahun     : " << P->info.thnBuat << endl;
        cout << "----------------------" << endl;
        P = P->next;
    }
}

address findElm(List L, string nopol) {
    address P = L.First;
    while (P != Nil) {
        if (P->info.nopol == nopol) {
            return P;
        }
        P = P->next;
    }
    return Nil;
}

void deleteFirst(List &L, address &P) {
    P = L.First;
    if (P != Nil) {
        if (L.First == L.Last) {
            L.First = Nil;
            L.Last = Nil;
        } else {
            L.First = P->next;
            L.First->prev = Nil;
        }
        P->next = Nil;
        P->prev = Nil;
    }
}

void deleteLast(List &L, address &P) {
    P = L.Last;
    if (P != Nil) {
        if (L.First == L.Last) {
            L.First = Nil;
            L.Last = Nil;
        } else {
            L.Last = P->prev;
            L.Last->next = Nil;
        }
        P->prev = Nil;
        P->next = Nil;
    }
}

void deleteAfter(address Prec, address &P) {
    if (Prec != Nil) {
        P = Prec->next;
        if (P != Nil) {
            Prec->next = P->next;
            if (P->next != Nil) {
                P->next->prev = Prec;
            }
            P->next = Nil;
            P->prev = Nil;
        }
    }
}

```
**main.cpp**
```c++
#include "Doublylist.h"

int main() {
    List L;
    CreateList(L);

    infotype x;
    address P;

    x.nopol = "D001";
    x.warna = "Hitam";
    x.thnBuat = 2019;
    insertLast(L, alokasi(x));

    x.nopol = "D002";
    x.warna = "Merah";
    x.thnBuat = 2020;
    insertLast(L, alokasi(x));

    x.nopol = "D003";
    x.warna = "Putih";
    x.thnBuat = 2021;
    insertLast(L, alokasi(x));

    cout << "=== Data Kendaraan ===" << endl;
    printInfo(L);

    cout << "\nCari kendaraan D001" << endl;
    P = findElm(L, "D001");
    if (P != Nil) {
        cout << "Data ditemukan: " << P->info.nopol << endl;
    }

    cout << "\nHapus kendaraan D003" << endl;
    P = findElm(L, "D003");
    if (P == L.Last) {
        deleteLast(L, P);
        dealokasi(P);
    }

    cout << "\n=== Data Setelah Dihapus ===" << endl;
    printInfo(L);

    return 0;
}

```
#### Output:
<img width="554" height="772" alt="image" src="https://github.com/user-attachments/assets/456e99bf-7baa-4959-9453-8c64b4d7a179" />

Program ini menggunakan Doubly Linked List untuk menyimpan data kendaraan yang berisi nomor polisi, warna, dan tahun pembuatan. Setiap elemen memiliki pointer next dan prev sehingga data bisa ditelusuri maju dan mundur. Program mendukung proses penambahan data di akhir list, pencarian berdasarkan nomor polisi, penghapusan data, serta penampilan seluruh isi list secara dinamis.
#### Full code Screenshot:
<img width="1240" height="934" alt="image" src="https://github.com/user-attachments/assets/5cb074cf-8828-48d3-9bed-2392b003db79" />


## Kesimpulan
Program ini menerapkan Doubly Linked List untuk mengelola data kendaraan secara dinamis.
Setiap elemen saling terhubung ke depan dan ke belakang sehingga proses insert, search, dan delete dapat dilakukan dengan lebih fleksibel dibanding singly linked list.
## Referensi
https://www.geeksforgeeks.org/cpp/doubly-linked-list-in-cpp/?utm_source=chatgpt.com
https://www.tutorialspoint.com/cplusplus-program-to-implement-doubly-linked-list?utm_source=chatgpt.com
https://www.programiz.com/dsa/doubly-linked-list?utm_source=chatgpt.com
