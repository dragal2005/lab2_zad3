#include <stdio.h>

#define ROZMIAR 31

void wypelnijWskaznikami(double *wsk) {
    for (int x = 0; x < ROZMIAR; x++)
        for (int y = 0; y < ROZMIAR; y++)
            *(wsk + x * ROZMIAR + y) = (x - 15) * (x - 15) - (y - 15) * (y - 15);
}

void transponujWskaznikami(double *wsk_we, double *wsk_wy) {
    for (int x = 0; x < ROZMIAR; x++)
        for (int y = 0; y < ROZMIAR; y++)
            *(wsk_wy + y * ROZMIAR + x) = *(wsk_we + x * ROZMIAR + y);
}

void wypiszWskaznikami(double *wsk) {
    for (int x = 0; x < ROZMIAR; x++) {
        for (int y = 0; y < ROZMIAR; y++)
            printf("%.0f\t", *(wsk + x * ROZMIAR + y)); // Znak tabulacji dla Excela
        printf("\n");
    }
}

int main() {
    double macierzA[ROZMIAR][ROZMIAR], macierzB[ROZMIAR][ROZMIAR];
    double *wskA = &macierzA[0][0];
    double *wskB = &macierzB[0][0];

    wypelnijWskaznikami(wskA);
    transponujWskaznikami(wskA, wskB);

    printf("Zad 3 - wskazniki:\n");
    wypiszWskaznikami(wskA);

    printf("\nZad 3 - Transpozycja :\n");
    wypiszWskaznikami(wskB);

    return 0;
}
