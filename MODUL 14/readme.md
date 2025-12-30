# <h1 align="center">Graph</h1>
<p align="center">Fauzan Dwi Raditya</p>

## Dasar Teori

Graph adalah kumpulan node (vertex) yang tidak kosong beserta garis penghubungnya (edge). Contoh sederhana dari graph dapat dilihat pada hubungan antara tempat kos Anda dan Common Lab. Tempat kos dan Common Lab berperan sebagai node (vertex), sedangkan jalan yang menghubungkan keduanya merupakan edge yang menghubungkan kedua node tersebut.
## Guided 

### 1. Graph]

```C++
#ifndef GRAPH_H_INCLUDE
#define GRAPH_H_INCLUDE
typedefintinfoGraph;
typedefstruct ElmNode*adrNode;
typedefstruct ElmEdge*adrEdge;

structElmNode{
    infoGraph info;
    intVisited;
    intPred;
    adrEdgefirstEdge;
    adrNode Next;
};
    structElmEdge{
    adrNode Node;
    adrEdge Next;
};

struct Graph {
    adrNode First;
};

adrNode AllocateNode(infoGraphX);
adrEdgeAllocateEdge(adrNodeN);
void CreateGraph(Graph &G);
void InsertNode(Graph &G,infoGraphX);
void DeleteNode(Graph &G,infoGraphX);
void ConnectNode(adrNodeN1,adrNode N2);
void DisconnectNode (adrNodeN1, adrNodeN2);
adrNodeFindNode(Graph G,infoGraphX);
adrEdgeFindEdge(adrNodeN,adrNodeNFind);
void PrintInfoGraph (Graph G);
void PrintTopologicalSort(Graph G);

#endif

#ifndef GRAPH_H_INCLUDE
#define GRAPH_H_INCLUDE

typedefintinfoGraph;
typedefstruct ElmNode*adrNode;
typedefstruct ElmEdge*adrEdge;

structElmNode{
    infoGraph info;
    intVisited;
    adrEdgefirstEdge;
    adrNode Next;
};

struct ElmEdge{
    adrNode Node;
    adrEdge Next;
};
struct Graph {
    adrNode First;
};

//Adds Node
ElmNode addNode(infoGrapha,intb, adrEdgec,adrNoded){
    ElmNodenewNode;
    newNode.Info= a;
    newNode.Visited=b ;
    newNode.firstEdge= c;
    newNode.Next = d;
returnnewNode;
}
//Addsanedgetoa graph
void addEdge(ElmNodenewNode){
    ElmEdgenewEdge;
    newEdge.Node = newNode.Next;
    newEdge.Next = newNode.firstEdge;
}
```


## Unguided 

### 1. [Soal]
**Graph.h**
```C++
#ifndef GRAPH_H
#define GRAPH_H

#include <iostream>
using namespace std;

typedef char infoGraph;
typedef struct ElmNode *adrNode;
typedef struct ElmEdge *adrEdge;

struct ElmEdge {
    adrNode Node;
    adrEdge Next;
};

struct ElmNode {
    infoGraph info;
    int visited;
    adrEdge firstEdge;
    adrNode Next;
};

struct Graph {
    adrNode first;
};

void CreateGraph(Graph &G);
adrNode AllocateNode(infoGraph X);
adrEdge AllocateEdge(adrNode N);
void InsertNode(Graph &G, infoGraph X);
adrNode FindNode(Graph G, infoGraph X);
void ConnectNode(adrNode N1, adrNode N2);
void PrintInfoGraph(Graph G);
void ResetVisited(Graph &G);

void PrintDFS(Graph G, adrNode N);
void PrintBFS(Graph G, adrNode N);

#endif

```
**Graph.cpp**
```c++
#include "graph.h"
#include <queue>

void CreateGraph(Graph &G) {
    G.first = NULL;
}

adrNode AllocateNode(infoGraph X) {
    adrNode P = new ElmNode;
    P->info = X;
    P->visited = 0;
    P->firstEdge = NULL;
    P->Next = NULL;
    return P;
}

adrEdge AllocateEdge(adrNode N) {
    adrEdge E = new ElmEdge;
    E->Node = N;
    E->Next = NULL;
    return E;
}

void InsertNode(Graph &G, infoGraph X) {
    adrNode P = AllocateNode(X);
    if (G.first == NULL) {
        G.first = P;
    } else {
        adrNode Q = G.first;
        while (Q->Next != NULL)
            Q = Q->Next;
        Q->Next = P;
    }
}

adrNode FindNode(Graph G, infoGraph X) {
    adrNode P = G.first;
    while (P != NULL) {
        if (P->info == X)
            return P;
        P = P->Next;
    }
    return NULL;
}

void ConnectNode(adrNode N1, adrNode N2) {
    adrEdge E1 = AllocateEdge(N2);
    E1->Next = N1->firstEdge;
    N1->firstEdge = E1;

    adrEdge E2 = AllocateEdge(N1);
    E2->Next = N2->firstEdge;
    N2->firstEdge = E2;
}

void PrintInfoGraph(Graph G) {
    adrNode P = G.first;
    while (P != NULL) {
        cout << P->info << " : ";
        adrEdge E = P->firstEdge;
        while (E != NULL) {
            cout << E->Node->info << " ";
            E = E->Next;
        }
        cout << endl;
        P = P->Next;
    }
}

void ResetVisited(Graph &G) {
    adrNode P = G.first;
    while (P != NULL) {
        P->visited = 0;
        P = P->Next;
    }
}

void PrintDFS(Graph G, adrNode N) {
    if (N == NULL || N->visited == 1)
        return;

    cout << N->info << " ";
    N->visited = 1;

    adrEdge E = N->firstEdge;
    while (E != NULL) {
        if (E->Node->visited == 0)
            PrintDFS(G, E->Node);
        E = E->Next;
    }
}

void PrintBFS(Graph G, adrNode N) {
    queue<adrNode> Q;
    Q.push(N);
    N->visited = 1;

    while (!Q.empty()) {
        adrNode P = Q.front();
        Q.pop();
        cout << P->info << " ";

        adrEdge E = P->firstEdge;
        while (E != NULL) {
            if (E->Node->visited == 0) {
                E->Node->visited = 1;
                Q.push(E->Node);
            }
            E = E->Next;
        }
    }
}

```
**main.cpp**
```c++
#include "graph.h"

int main() {
    Graph G;
    CreateGraph(G);

    InsertNode(G, 'A');
    InsertNode(G, 'B');
    InsertNode(G, 'C');
    InsertNode(G, 'D');
    InsertNode(G, 'E');
    InsertNode(G, 'F');
    InsertNode(G, 'G');
    InsertNode(G, 'H');

    adrNode A = FindNode(G, 'A');
    adrNode B = FindNode(G, 'B');
    adrNode C = FindNode(G, 'C');
    adrNode D = FindNode(G, 'D');
    adrNode E = FindNode(G, 'E');
    adrNode F = FindNode(G, 'F');
    adrNode Gg = FindNode(G, 'G');
    adrNode H = FindNode(G, 'H');

    ConnectNode(A, B);
    ConnectNode(A, C);
    ConnectNode(B, D);
    ConnectNode(B, E);
    ConnectNode(C, F);
    ConnectNode(C, Gg);
    ConnectNode(D, H);
    ConnectNode(E, H);
    ConnectNode(F, H);
    ConnectNode(Gg, H);

    cout << "Adjacency List:\n";
    PrintInfoGraph(G);

    cout << "\nDFS Traversal: ";
    ResetVisited(G);
    PrintDFS(G, A);

    cout << "\n\nBFS Traversal: ";
    ResetVisited(G);
    PrintBFS(G, A);

    return 0;
}

```
#### Output:
<img width="325" height="341" alt="image" src="https://github.com/user-attachments/assets/25905269-d677-466c-abaf-605cad9da8c2" />

Soal ini berfokus pada pemahaman ADT Graph tak berarah dalam menggambarkan hubungan antar simpul dengan memanfaatkan struktur adjacency list. Penerapan operasi penambahan simpul, pembentukan sisi, serta proses penelusuran menggunakan DFS dan BFS memperlihatkan keterhubungan antar simpul melalui pointer edge sehingga graph dapat ditelusuri secara teratur. Selain itu, penggunaan atribut visited sangat berperan dalam menjaga kelancaran traversal, menghindari kunjungan berulang, serta memastikan proses penjelajahan seluruh simpul yang saling terhubung berjalan secara efisien dan tepat.
#### Full code Screenshot:
<img width="598" height="917" alt="image" src="https://github.com/user-attachments/assets/a7b1b668-7d91-4854-9152-a7aab014388b" />
<img width="534" height="926" alt="image" src="https://github.com/user-attachments/assets/f539134b-7189-4a0a-96ee-e0434481610c" />
<img width="582" height="903" alt="image" src="https://github.com/user-attachments/assets/f6108f2b-f547-4d79-9ba2-3e718301325b" />


## Kesimpulan
Praktikum ini bertujuan untuk mempelajari cara kerja ADT Graph tidak berarah dengan menggunakan representasi adjacency list, terutama dalam proses penambahan simpul, pembentukan hubungan antar simpul, serta penelusuran graph menggunakan algoritma Depth First Search (DFS) dan Breadth First Search (BFS). Melalui kegiatan ini, mahasiswa diharapkan dapat memahami proses traversal graph yang berjalan secara teratur, sistematis, dan efisien dengan bantuan penanda visited untuk mencegah terjadinya kunjungan berulang pada simpul yang sama.
## Referensi
Modul Praktikum Struktur Data Modul 14 Graph, AI
