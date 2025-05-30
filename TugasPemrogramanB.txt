#include <stdio.h>
#include <math.h>
#include <stdlib.h>

#define EPSILON 1e-6
#define MAX_ITER 100

// Fungsi gaya total: f(v) = mg - c*v^2
double f(double v) {
    double m = 68.1;   // massa (kg)
    double g = 9.8;    // gravitasi (m/s^2)
    double c = 12.5;   // koefisien drag (kg/s)
    return m * g - c * v * v;
}

// Fungsi utama: Brent's Method
double brent(double a, double b) {
    double fa = f(a);
    double fb = f(b);

    if (fa * fb >= 0) {
        printf("Brent error: akar tidak dibatasi dalam interval [a,b]\n");
        exit(1);
    }

    double c = a;
    double fc = fa;
    int iter;
    int mflag = 1;
    double s = b;
    double d;

    for (iter = 1; iter < MAX_ITER; iter++) {
        if (fa != fc && fb != fc) {
            // Interpolasi inverse kuadratik
            s = (a * fb * fc) / ((fa - fb) * (fa - fc)) +
                (b * fa * fc) / ((fb - fa) * (fb - fc)) +
                (c * fa * fb) / ((fc - fa) * (fc - fb));
        } else {
            // Metode secant
            s = b - fb * (b - a) / (fb - fa);
        }

        // Kondisi untuk mengganti s agar tetap konvergen
        if ((s < (3 * a + b) / 4 || s > b) ||
            (mflag && fabs(s - b) >= fabs(b - c) / 2) ||
            (!mflag && fabs(s - b) >= fabs(c - d) / 2) ||
            (mflag && fabs(b - c) < EPSILON) ||
            (!mflag && fabs(c - d) < EPSILON)) {
            s = (a + b) / 2;
            mflag = 1;
        } else {
            mflag = 0;
        }

        double fs = f(s);
        d = c;
        c = b;
        fc = fb;

        if (fa * fs < 0) {
            b = s;
            fb = fs;
        } else {
            a = s;
            fa = fs;
        }

        if (fabs(fa) < fabs(fb)) {
            // Swap a dan b
            double temp = a;
            a = b;
            b = temp;

            temp = fa;
            fa = fb;
            fb = temp;
        }

        if (fabs(fb) < EPSILON) {
            printf("Konvergen dalam %d iterasi.\n", iter);
            return b;
        }
    }

    printf("Gagal konvergen setelah %d iterasi.\n", MAX_ITER);
    return b;
}

int main() {
    double akar = brent(0.0, 20.0);
    printf("Akar ditemukan: v = %.6f m/s\n", akar);
    return 0;
}
