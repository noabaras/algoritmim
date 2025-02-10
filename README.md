# algoritmim
Prim's algorithm
#include <stdio.h>
#define a 0
#define b 1
#define c 2
#define d 3
#define numofAdj 9
#define infinite 1000

int i = 0;
int matrixGrap1[9][9] = {
    {-1, 4, -1, -1, -1, -1, -1, 8, -1},
    {-1, -1, 8, -1, -1, -1, -1, -1, -1},
    {-1, -1, -1, 7, -1, 4, -1, -1, 2},
    {-1, -1, -1, -1, 9, 14, -1, -1, -1},
    {-1, -1, -1, -1, -1, 10, -1, -1, -1},
    {-1, -1, -1, -1, -1, -1, 2, -1, -1},
    {-1, -1, -1, -1, -1, -1, -1, 1, -1},
    {-1, -1, -1, -1, -1, -1, -1, -1, 7},
    {-1, -1, -1, -1, -1, -1, -1, -1, -1},
};
int three[9][9] = { 0 };
int visited[9] = { 0 };
int parent[9] = { -1, -1, -1, -1, -1, -1, -1, -1, -1 };
int previousweight[9] = { infinite, infinite, infinite, infinite, infinite, infinite, infinite, infinite, infinite };
int v = 0;
int indexminweight = 0;
int length = sizeof(previousweight) / sizeof(int);

int min(int arrweight[], int visited[]) {
    int m = infinite;
    int index = -1;
    for (int i = 0; i < length; i++) {
        if (arrweight[i] < m && visited[i] == 0) {
            m = arrweight[i];
            index = i;
        }
    }
    return index;
}

int main() {
    previousweight[v] = 0;
    while (i < numofAdj) {
        for (int j = 0; j < numofAdj; j++) {
            if (matrixGrap1[v][j] != -1 && previousweight[v] + matrixGrap1[v][j] < previousweight[j]) {
                previousweight[j] = previousweight[v] + matrixGrap1[v][j];
                parent[j] = v;
            }
        }
        visited[v] = 1;
        indexminweight = min(previousweight, visited);
        if (indexminweight != -1) {
            three[parent[indexminweight]][indexminweight] = matrixGrap1[parent[indexminweight]][indexminweight];
            v = indexminweight;
        }
        i++;
    }

    for (int i = 0; i < length; i++) {
        for (int j = 0; j < length; j++) {
            printf(" %d", three[i][j]);
        }
        printf("\n");
    }
    return 0;
}
