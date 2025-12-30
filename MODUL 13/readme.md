# <h1 align="center">MULTILINKEDLIST</h1>
<p align="center">Fauzan Dwi Raditya</p>

## Dasar Teori

Secara makna, rekursif dapat diartikan sebagai proses pengulangan yang dilakukan dengan memanggil dirinya sendiri. Dalam pemrograman, prosedur dan fungsi berfungsi sebagai subprogram yang sangat berguna, khususnya dalam pengembangan program atau proyek yang berskala besar.

## Guided 

### 1. [MILL]

```C++
/* buat dahulu elemen yang akan disisipkan */ 
address_anak alokasiAnak(infotypeanak X){
    address_anak P = alokasi(X); 
    P→next = Nil; 
    P→prev = Nil; 
    return P; 
} 
/* mencari apakah ada elemen pegawai dengan info X */ 
address findElm(listinduk L, infotypeinduk X){ 
    address cariInduk = L.first; 
    do{ 
        if(cariInduk.info == X){ 
            return cariInduk; 
        }else{ 
            cariInduk = cariInduk→next; 
}  
    }while(cariInduk.info != X || cariInduk != L→last) 
} 
/* menyisipkan anak pada akhir list anak */ 
void insertLastAnak(listanak &Lanak, address_anak P){ 
    address_anak ! = head(&Lanak); 
    do{ 
        Q = Q→next; 
    }while(next(&Lanak)!=Nil) 
    Q→next = P; 
    P→prev = Q; 
    P→next = Nil; 
}
```
Kode di atas digunakan untuk mencetak teks "ini adalah file code guided praktikan" ke layar menggunakan function cout untuk mengeksekusi nya.

## Unguided 

### 1. [Soal]

```C++
#include <iostream>
using namespace std;

int main() {
    cout << "ini adalah file code unguided praktikan" << endl;
    return 0;
}
```
**multilist.h**
```c++
/* contoh ADT list berkait dengan representasi fisik pointer*/ 
/* representasi address dengan pointer*/ 
 
/* info tipe adalah integer */ 
#ifndef MULTILIST_H_INCLUDED 
#define MULTILIST_H_INCLUDED 
#define Nil NULL 
 
typedef int infotypeanak; 
typedef int infotypeinduk; 
typedef struct elemen_list_induk *address; 
typedef struct elemen_list_anak *address_anak; 
/* define list : */ 
 
/* list kosong jika L.first=Nil 
setiap elemen address P dapat diacu P→info atau P→next 
elemen terakhir list jika addressnya last, maka L.last = Nil */ 
struct elemen_list_anak{ 
/* struct ini untuk menyimpan elemen anak dan pointer penunjuk 
   elemen tetangganya */ 
     infotypeanak info; 
     address_anak next; 
     address_anak prev; 
}; 
 
struct listanak { 
/* struct ini digunakan untuk menyimpan list anak itu sendiri */ 
   address_anak first; 
   address_anak last; 
}; 
 
struct elemen_list_induk{ 
/* struct ini untuk menyimpan elemen induk dan pointer penunjuk 
   elemen tetangganya */
      infotypeanak info; 
      listanak lanak;
      address next; 
      address prev; 
}; 
struct listinduk { 
/* struct ini digunakan untuk menyimpan list induk itu sendiri */ 
  address first;
  address last;
}; 
 
/********* pengecekan apakah list kosong ***********/ 
boolean ListEmpty(listinduk L); 
/*mengembalikan nilai true jika list induk kosong*/ 
boolean ListEmptyAnak(listanak L); 
/*mengembalikan nilai true jika list anak kosong*/ 
 
/********* pembuatan list kosong *********/ 
void CreateList(listinduk &L); 
/* I.S. sembarang 
   F.S. terbentuk list induk kosong*/ 
void CreateListAnak(listanak &L); 
/* I.S. sembarang 
   F.S. terbentuk list anak kosong*/ 
    
/********* manajemen memori *********/ 
address alokasi(infotypeinduk P); 
/* mengirimkan address dari alokasi sebuah elemen induk 
   jika alokasi berhasil, maka nilai address tidak Nil dan jika gagal 
   nilai address Nil */ 
    
address_anak alokasiAnak(infotypeanak P); 
/* mengirimkan address dari alokasi sebuah elemen anak 
   jika alokasi berhasil, maka nilai address tidak Nil dan jika gagal 
   nilai address_anak Nil */ 
    
void dealokasi(address P); 
/* I.S. P terdefinisi 
   F.S. memori yang digunakan P dikembalikan ke sistem */ 
 
void dealokasiAnak(address_anak P); 
/* I.S. P terdefinisi 
   F.S. memori yang digunakan P dikembalikan ke sistem */    
/********* pencarian sebuah elemen list *********/ 
address findElm(listinduk L, infotypeinduk X); 
/* mencari apakah ada elemen list dengan P→info = X 
   jika ada, mengembalikan address elemen tab tsb, dan Nil jika sebaliknya 
*/ 
address_anak findElm(listanak Lanak, infotypeanak X); 
/* mencari apakah ada elemen list dengan P→info = X 
   jika ada, mengembalikan address elemen tab tsb, dan Nil jika sebaliknya 
*/ 
boolean fFindElm(listinduk L, address P); 
/* mencari apakah ada elemen list dengan alamat P 
   mengembalikan true jika ada dan false jika tidak ada */ 
boolean fFindElmanak(listanak Lanak, address_anak P); 
/* mencari apakah ada elemen list dengan alamat P 
   mengembalikan true jika ada dan false jika tidak ada */ 
 
address findBefore(listinduk L, address P); 
/* mengembalikan address elemen sebelum P 
   jika P berada pada awal list, maka mengembalikan nilai Nil */ 
address_anak findBeforeAnak(listanak Lanak, infotypeinduk X, address_anak 
P); 
/* mengembalikan address elemen sebelum P dimana P→info = X 
   jika P berada pada awal list, maka mengembalikan nilai Nil */ 
    
/********* penambahan elemen **********/ 
void insertFirst(listinduk &L, address P); 
/* I.S. sembarang, P sudah dialokasikan 
   F.S. menempatkan elemen beralamat P pada awal list */ 
    
void insertAfter(listinduk &L, address P, address Prec); 
/* I.S. sembarang, P dan Prec alamt salah satu elemen list 
   F.S. menempatkan elemen beralamat P sesudah elemen beralamat Prec */
void insertLast(listinduk &L, address P); 
/* I.S. sembarang, P sudah dialokasikan 
   F.S. menempatkan elemen beralamat P pada akhir list */ 
    
void insertFirstAnak(listanak &L, address_anak P); 
/* I.S. sembarang, P sudah dialokasikan 
   F.S. menempatkan elemen beralamat P pada awal list */ 
    
void insertAfterAnak(listanak &L, address_anak P, address_anak Prec); 
/* I.S. sembarang, P dan Prec alamt salah satu elemen list 
   F.S. menempatkan elemen beralamat P sesudah elemen beralamat Prec */ 
 
void insertLastAnak(listanak &L, address_anak P); 
/* I.S. sembarang, P sudah dialokasikan 
   F.S. menempatkan elemen beralamat P pada akhir list */ 
    
/********* penghapusan sebuah elemen *********/ 
void delFirst(listinduk &L, address &P); 
/* I.S. list tidak kosong 
   F.S. adalah alamat dari alamat elemen pertama list 
   sebelum elemen pertama list dihapus 
   elemen pertama list hilang dan list mungkin menjadi kosong 
   first elemen yang baru adalah successor first elemen yang lama */ 
void delLast(listinduk &L, address &P); 
/* I.S. list tidak kosong 
   F.S. adalah alamat dari alamat elemen terakhir list 
   sebelum elemen terakhir list dihapus 
   elemen terakhir list hilang dan list mungkin menjadi kosong 
   last elemen yang baru adalah successor last elemen yang lama */ 
 
void delAfter(listinduk &L, address &P, address Prec); 
/* I.S. list tidak kosng, Prec alamat salah satu elemen list 
   F.S. P adalah alamatdari Prec→next, menghapus Prec→next dari list */ 
void delP (listinduk &L, infotypeinduk X); 
/* I.S. sembarang 
   F.S. jika ada elemen list dengan alamat P, dimana P→info = X,  
        maka P dihapus dan P di-dealokasi,  
        jika tidak ada maka list tetap list mungkin akan menjadi kosong  
        karena penghapusan */ 
   
void delFirstAnak(listanak &L, address_anak &P); 
/* I.S. list tidak kosong 
   F.S. adalah alamat dari alamat elemen pertama list 
   sebelum elemen pertama list dihapus 
   elemen pertama list hilang dan list mungkin menjadi kosong 
   first elemen yang baru adalah successor first elemen yang lama */ 
void delLastAnak(listanak &L, address_anak &P); 
/* I.S. list tidak kosong 
   F.S. adalah alamat dari alamat elemen terakhir list 
   sebelum elemen terakhir list dihapus 
   elemen terakhir list hilang dan list mungkin menjadi kosong 
   last elemen yang baru adalah successor last elemen yang lama */ 
 
void delAfterAnak(listanak &L, address_anak &P, address_anak Prec); 
/* I.S. list tidak kosng, Prec alamat salah satu elemen list 
   F.S. P adalah alamatdari Prec→next, menghapus Prec→next dari list */ 
void delPAnak (listanak &L, infotypeanak X); 
/* I.S. sembarang 
   F.S. jika ada elemen list dengan alamat P, dimana P→info = X,  
        maka P dihapus dan P di-dealokasi,  
        jika tidak ada maka list tetap list mungkin akan menjadi kosong  
        karena penghapusan */ 
/********** proses semau elemen list *********/ 
void printInfo(list L); 
/* I.S. list mungkin kosong 
   F.S. jika list tidak kosong menampilkan semua info yang ada pada list 
*/ 

int nbList(list L); 
/* mengembalikan jumlah elemen pada list */ 
 
void printInfoAnak(listanak Lanak); 
/* I.S. list mungkin kosong 
   F.S. jika list tidak kosong menampilkan semua info yang ada pada list 
*/ 
 
int nbListAnak(listanak Lanak); 
/* mengembalikan jumlah elemen pada list anak */ 
 
/********** proses terhadap list **********/ 
void delAll(listinduk &L); 
/* menghapus semua elemen list dan semua elemen di-dealokasi */ 
#endif
```
## **Unguided**
circularlist.h
```c++
#ifndef CIRCULARLIST_H_INCLUDED
#define CIRCULARLIST_H_INCLUDED

#include <iostream>
#include <string>
using namespace std;

#define Nil NULL

typedef struct mahasiswa {
    string nama;
    string nim;
    char jenis_kelamin;
    float ipk;
} infotype;

typedef struct ElmList *address;

struct ElmList {
    infotype info;
    address next;
};

struct List {
    address First;
};

void createList(List &L);
address alokasi(infotype x);
void dealokasi(address &P);

void insertFirst(List &L, address P);
void insertAfter(List &L, address Prec, address P);
void insertLast(List &L, address P);

void deleteFirst(List &L, address &P);
void deleteAfter(List &L, address Prec, address &P);
void deleteLast(List &L, address &P);

address findElm(List L, infotype x);
void printInfo(List L);

#endif

```
**circularlist.cpp**
```c++
#include "circularlist.h"

void createList(List &L) {
    L.First = Nil;
}

address alokasi(infotype x) {
    address P = new ElmList;
    P->info = x;
    P->next = Nil;
    return P;
}

void dealokasi(address &P) {
    delete P;
    P = Nil;
}

void insertFirst(List &L, address P) {
    if (L.First == Nil) {
        L.First = P;
        P->next = P;
    } else {
        address Q = L.First;
        while (Q->next != L.First) {
            Q = Q->next;
        }
        P->next = L.First;
        Q->next = P;
        L.First = P;
    }
}

void insertAfter(List &L, address Prec, address P) {
    if (Prec != Nil) {
        P->next = Prec->next;
        Prec->next = P;
    }
}

void insertLast(List &L, address P) {
    if (L.First == Nil) {
        insertFirst(L, P);
    } else {
        address Q = L.First;
        while (Q->next != L.First) {
            Q = Q->next;
        }
        Q->next = P;
        P->next = L.First;
    }
}

void deleteFirst(List &L, address &P) {
    if (L.First != Nil) {
        address Q = L.First;
        if (Q->next == Q) {
            P = Q;
            L.First = Nil;
        } else {
            address R = L.First;
            while (R->next != L.First) {
                R = R->next;
            }
            P = L.First;
            L.First = P->next;
            R->next = L.First;
        }
        P->next = Nil;
    }
}

void deleteAfter(List &L, address Prec, address &P) {
    if (Prec != Nil) {
        P = Prec->next;
        Prec->next = P->next;
        P->next = Nil;
    }
}

void deleteLast(List &L, address &P) {
    if (L.First != Nil) {
        address Q = L.First;
        if (Q->next == Q) {
            P = Q;
            L.First = Nil;
        } else {
            address Prec = Nil;
            while (Q->next != L.First) {
                Prec = Q;
                Q = Q->next;
            }
            P = Q;
            Prec->next = L.First;
        }
        P->next = Nil;
    }
}

address findElm(List L, infotype x) {
    if (L.First == Nil) return Nil;

    address P = L.First;
    do {
        if (P->info.nim == x.nim) {
            return P;
        }
        P = P->next;
    } while (P != L.First);

    return Nil;
}

void printInfo(List L) {
    if (L.First != Nil) {
        address P = L.First;
        do {
            cout << "Nama : " << P->info.nama << endl;
            cout << "NIM  : " << P->info.nim << endl;
            cout << "JK   : " << P->info.jenis_kelamin << endl;
            cout << "IPK  : " << P->info.ipk << endl;
            cout << "------------------" << endl;
            P = P->next;
        } while (P != L.First);
    }
}

```
**main.cpp**
```c++
#include "circularlist.h"

address createData(string nama, string nim, char jenis_kelamin, float ipk) {
    infotype x;
    address P;

    x.nama = nama;
    x.nim = nim;
    x.jenis_kelamin = jenis_kelamin;
    x.ipk = ipk;

    P = alokasi(x);
    return P;
}

int main() {
    List L;
    address P1 = Nil;
    address P2 = Nil;
    infotype x;

    createList(L);

    cout << "coba insert first, last, dan after" << endl;

    P1 = createData("Danu", "04", 'l', 4.0);
    insertFirst(L, P1);

    P1 = createData("Fahmi", "06", 'l', 3.45);
    insertLast(L, P1);

    P1 = createData("Bobi", "02", 'l', 3.71);
    insertFirst(L, P1);

    P1 = createData("Ali", "01", 'l', 3.3);
    insertFirst(L, P1);

    P1 = createData("Gita", "07", 'p', 3.75);
    insertLast(L, P1);

    x.nim = "07";
    P1 = findElm(L, x);
    P2 = createData("Cindi", "03", 'p', 3.5);
    insertAfter(L, P1, P2);

    x.nim = "02";
    P1 = findElm(L, x);
    P2 = createData("Hilmi", "08", 'p', 3.3);
    insertAfter(L, P1, P2);

    x.nim = "04";
    P1 = findElm(L, x);
    P2 = createData("Eli", "05", 'p', 3.4);
    insertAfter(L, P1, P2);

    printInfo(L);

    return 0;
}

```
#### Output:
<img width="413" height="819" alt="image" src="https://github.com/user-attachments/assets/2414441c-7a4d-4def-a91d-1b75734d58a7" />

Soal ini menyoroti pemahaman konsep ADT Circular Doubly Linked List dalam mengelola data mahasiswa secara dinamis. Penerapan operasi penyisipan, penghapusan, dan pencarian memperlihatkan keterhubungan antar node secara melingkar melalui pointer next, sehingga struktur list tetap terjaga, efisien, dan dapat ditelusuri dengan mudah tanpa adanya elemen NULL.

#### Full code Screenshot:
<img width="613" height="874" alt="image" src="https://github.com/user-attachments/assets/a89e42d2-4c6b-4a60-a3be-6cacaf881089" />
<img width="637" height="894" alt="image" src="https://github.com/user-attachments/assets/1357e3fc-93b2-4510-8e26-2a44a07c937a" />
<img width="856" height="885" alt="image" src="https://github.com/user-attachments/assets/fed6f66a-41a4-4812-8305-520c4959948c" />


## Kesimpulan
Praktikum ini bertujuan untuk mempelajari cara kerja Multi Linked List serta bagaimana data dikelola di dalamnya, terutama pada operasi penambahan data di awal, di akhir, dan setelah node tertentu, serta proses menampilkan kembali data secara terstruktur dan berurutan.
## Referensi
Modul Praktikum Struktur Data Multi Linked List, cplusplus.com
