# Kalkulator-sederhana
P3
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int tambah(int a, int b) {
    return a + b;
}

int kurang(int a, int b) {
    return a - b;
}

int kali(int a, int b) {
    return a * b;
}

int bagi(int a, int b) {
    if (b != 0) {
        return a / b;
    } else {
        printf("Error: Pembagian dengan nol tidak diperbolehkan.\n");
        return 0;
    }
}

int faktorial(int n) {
    if (n <= 1) return 1;
    return n * faktorial(n - 1);
}

// Fungsi untuk mencari FPB 
int fpb(int a, int b) {
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

// Fungsi untuk mencari KPK 
int kpk(int a, int b) {
    return (a * b) / fpb(a, b);
}

// Fungsi untuk menangani input pengguna
void kalkulator() {
    char operasi[10];
    int a, b, hasil;

    while (1) {
        printf("Masukkan perintah (contoh: ADD 4 5) atau 'EXIT' untuk keluar:\n");
        scanf("%s", operasi);

        if (strcmp(operasi, "EXIT") == 0) {
            printf("Kalkulator dihentikan.\n");
            break;
        }
        
        if (strcmp(operasi, "ADD") == 0 || strcmp(operasi, "SUB") == 0 ||
            strcmp(operasi, "MULT") == 0 || strcmp(operasi, "DIV") == 0 ||
            strcmp(operasi, "KPK") == 0 || strcmp(operasi, "FPB") == 0) {
            
            scanf("%d %d", &a, &b);
            
            if (strcmp(operasi, "ADD") == 0) {
                hasil = tambah(a, b);
            } else if (strcmp(operasi, "SUB") == 0) {
                hasil = kurang(a, b);
            } else if (strcmp(operasi, "MULT") == 0) {
                hasil = kali(a, b);
            } else if (strcmp(operasi, "DIV") == 0) {
                hasil = bagi(a, b);
            } else if (strcmp(operasi, "KPK") == 0) {
                hasil = kpk(a, b);
            } else if (strcmp(operasi, "FPB") == 0) {
                hasil = fpb(a, b);
            }
            printf("Hasil: %d\n", hasil);

        // Operasi faktorial dengan satu operand
        } else if (strcmp(operasi, "FACT") == 0) {
            scanf("%d", &a);
            hasil = faktorial(a);
            printf("Hasil: %d\n", hasil);

        } else {
            printf("Operasi tidak dikenali.\n");
        }
    }
}

int main() {
    kalkulator();
    return 0;
}
