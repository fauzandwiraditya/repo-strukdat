
# <h1 align="center">SINGLY LINKED LIST (BAGIAN 1) </h1>
<p align="center">Fauzan Dwi Raditya</p>

## Dasar Teori

Linked list (sering disebut list) adalah salah satu struktur data yang menyimpan sekumpulan data dalam bentuk node yang saling terhubung satu sama lain. Struktur ini bersifat fleksibel karena ukurannya bisa bertambah atau berkurang sesuai kebutuhan program. Data yang disimpan di dalam linked list bisa berupa data sederhana, misalnya satu variabel seperti nama, atau data yang lebih kompleks berupa beberapa atribut sekaligus, contohnya data mahasiswa yang terdiri dari nama, NIM, dan alamat.
## Guided 

### 1. [Nama Topik]
**list.h**
```
//
//
#ifndef LIST_H
#define LIST_H
#define Nil NULL

#include <iostream>
using namespace std;

//deklarasi isi data struct mahasiswa
struct mahasiswa{
    string nama;
    string nim;
    int umur;
};

typedef mahasiswa dataMahasiswa; //Membiarkan nama alias dataMahasiswa untuk struct mahasiswa

typedef struct node *address; //Mendefinisikan alias address sbg pointer ke struct node

struct node{
    dataMahasiswa isidata;
    address next;
};

struct linkedlist{ //ini linked list nya
    address first;
};

//semua function & prosedur yang akan dipakai
bool isEmpty(linkedlist List);
void createList(linkedlist &List);
address alokasi(string nama, string nim, int umur);
void dealokasi(address &node);
void printList(linkedlist List);
void insertFirst(linkedlist &List, address nodeBaru);
void insertAfter(linkedlist &List, address nodeBaru, address Prev);
void insertLast(linkedlist &List, address nodeBaru);

#endif
}
```
**Singlylist.cpp**
```
#include "Singlylist.h"

void createList(List &L) {
    L.First = nullptr;
}

address alokasi(infotype x) {
    address P = new ElmList;
    if (P != nullptr) {
        P->info = x;
        P->next = nullptr;
    }
    return P;
}

void dealokasi(address P) {
    delete P;
}

void insertFirst(List &L, address P) {
    if (P != nullptr) {
        P->next = L.First;
        L.First = P;
    }
}

void printInfo(List L) {
    address P = L.First;
    while (P != nullptr) {
        cout << P->info << " ";
        P = P->next;
    }
    cout << endl;
}
```
**main.cpp**
```
#include "Singlylist.h"

int main() {
    List L;
    address P1, P2, P3, P4, P5;

    createList(L);

    P1 = alokasi(2);
    insertFirst(L, P1);

    P2 = alokasi(0);
    insertFirst(L, P2);

    P3 = alokasi(8);
    insertFirst(L, P3);

    P4 = alokasi(12);
    insertFirst(L, P4);

    P5 = alokasi(9);
    insertFirst(L, P5);

    printInfo(L);

    return 0;
}
```


Program ini membangun sistem linked list mahasiswa yang dapat menyimpan, menambah, menghapus, dan menampilkan data secara dinamis.


## Unguided 

### 1. [Soal]
**Singlylist.h**


```
#ifndef SINGLYLIST_H
#define SINGLYLIST_H

#include <iostream>
using namespace std;

typedef int infotype;
typedef struct elmlist *address;

struct elmlist{
    infotype info;
    address next;
};

struct List{
    address First;
};

void createList(List &L);
address alokasi(infotype x);
void dealokasi(address &P);
void insertFirst(List &L, address P);
void printInfo(List L);

#endif

```
**Singlylist.cpp**
```
#include "Singlylist.h"

void createList(List &L){
    L.First = NULL;
}

address alokasi(infotype x){
    address P = new elmlist;
    P->info = x;
    P->next = NULL;
    return P;
}

void dealokasi(address &P){
    delete P;
}

void insertFirst(List &L, address P){
    P->next = L.First;
    L.First = P;
}

void printInfo(List L){
    address P = L.First;
    while(P != NULL){
        cout << P->info << " ";
        P = P->next;
    }
    cout << endl;
}

```
**main.cpp**
```
#include "Singlylist.h"

int main(){
    List L;
    address P1, P2, P3, P4, P5;

    createList(L);

    P1 = alokasi(2);
    insertFirst(L, P1);

    P2 = alokasi(0);
    insertFirst(L, P2);

    P3 = alokasi(8);
    insertFirst(L, P3);

    P4 = alokasi(12);
    insertFirst(L, P4);

    P5 = alokasi(9);
    insertFirst(L, P5);

    printInfo(L);

    return 0;
}


```



#### Output:
<img width="827" height="122" alt="image" src="https://github.com/user-attachments/assets/7ca639d4-9064-439b-8daf-06fe98d38cf0" />

Program ini digunakan untuk membuat dan menampilkan data menggunakan struktur singly linked list. Setiap data baru dimasukkan ke bagian depan list dengan metode insertFirst, sehingga urutan data menjadi kebalikan dari urutan saat dimasukkan. Setelah semua data ditambahkan, program menampilkan isi linked list ke layar, yaitu 9 12 8 0 2, sesuai dengan hasil yang diharapkan.

#### Full code Screenshot:
<img width="1264" height="717" alt="image" src="https://github.com/user-attachments/assets/0c54b620-d21c-4c4e-aa7f-6e09e0fc0d46" />

### 2. [Soa2]
**Singlylist.h**
```
#ifndef SINGLYLIST_H
#define SINGLYLIST_H

#include <iostream>
using namespace std;

typedef int infotype;
typedef struct elmlist *address;

struct elmlist{
    infotype info;
    address next;
};

struct List{
    address First;
};

void createList(List &L);
address alokasi(infotype x);
void dealokasi(address &P);

void insertFirst(List &L, address P);

void deleteFirst(List &L, address &P);
void deleteLast(List &L, address &P);
void deleteAfter(address Prec, address &P);

void deleteList(List &L);
int nbList(List L);

void printInfo(List L);

#endif

```
**Singlylist.cpp**
```
#include "Singlylist.h"

void createList(List &L){
    L.First = NULL;
}

address alokasi(infotype x){
    address P = new elmlist;
    P->info = x;
    P->next = NULL;
    return P;
}

void dealokasi(address &P){
    delete P;
}

void insertFirst(List &L, address P){
    P->next = L.First;
    L.First = P;
}

void deleteFirst(List &L, address &P){
    P = L.First;
    L.First = P->next;
    P->next = NULL;
}

void deleteLast(List &L, address &P){
    address Q;
    if(L.First->next == NULL){
        P = L.First;
        L.First = NULL;
    } else {
        Q = L.First;
        while(Q->next->next != NULL){
            Q = Q->next;
        }
        P = Q->next;
        Q->next = NULL;
    }
}

void deleteAfter(address Prec, address &P){
    P = Prec->next;
    Prec->next = P->next;
    P->next = NULL;
}

void deleteList(List &L){
    address P;
    while(L.First != NULL){
        deleteFirst(L, P);
        dealokasi(P);
    }
}

int nbList(List L){
    int n = 0;
    address P = L.First;
    while(P != NULL){
        n++;
        P = P->next;
    }
    return n;
}

void printInfo(List L){
    address P = L.First;
    while(P != NULL){
        cout << P->info << " ";
        P = P->next;
    }
    cout << endl;
}

```
**main.cpp**
```
#include "Singlylist.h"

int main(){
    List L;
    address P1, P2, P3, P4, P5, P;

    createList(L);

    P1 = alokasi(2);  insertFirst(L, P1);
    P2 = alokasi(0);  insertFirst(L, P2);
    P3 = alokasi(8);  insertFirst(L, P3);
    P4 = alokasi(12); insertFirst(L, P4);
    P5 = alokasi(9);  insertFirst(L, P5);

    deleteFirst(L, P);
    dealokasi(P);

    deleteLast(L, P);
    dealokasi(P);

    deleteAfter(L.First, P);
    dealokasi(P);

    printInfo(L);
    cout << "Jumlah node : " << nbList(L) << endl;

    deleteList(L);
    cout << "- List Berhasil Terhapus -" << endl;
    cout << "Jumlah node : " << nbList(L) << endl;

    return 0;
}

```
#### Output:
<img width="948" height="252" alt="image" src="https://github.com/user-attachments/assets/99d1fd8e-3644-44bc-a4d7-0d11e67e52e7" />
Program ini digunakan untuk menghapus beberapa data pada singly linked list sesuai perintah soal. Pertama, data di awal list dihapus, lalu dilanjutkan dengan menghapus data di bagian akhir dan satu data di tengah list. Setelah itu, program menampilkan sisa data beserta jumlah node yang masih ada. Terakhir, seluruh data di dalam list dihapus sehingga list menjadi kosong dan tidak menyimpan data lagi.


#### Full code Screenshot:
<img width="1332" height="889" alt="image" src="https://github.com/user-attachments/assets/e3ec7b4a-cb3d-45b4-860c-e678ae53ec49" />




## Kesimpulan
Kesimpulannya, program ini digunakan untuk mengelola data menggunakan singly linked list yang bersifat fleksibel. Data disimpan dalam bentuk node yang saling terhubung menggunakan pointer, sehingga penambahan dan penghapusan data bisa dilakukan dengan mudah. Program juga menunjukkan bahwa seluruh data dapat dihapus hingga list menjadi kosong, tanpa perlu menentukan ukuran tetap seperti pada array.
## Referensi
Modul Praktikum Struktur Data – Singly Linked List
https://www.geeksforgeeks.org/cpp/cpp-program-for-deleting-a-node-in-a-linked-list/
https://www.tutorialspoint.com/cplusplus-program-to-delete-the-first-node-in-a-given-singly-linked-list?utm_source=chatgpt.com
