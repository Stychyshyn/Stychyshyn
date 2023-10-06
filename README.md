#include <iostream>
#include <cmath>
using namespace std;

// Функцiя для обчислення F з додатковою умовою
int calculateF(double a, double b, double c, double x) {
    int Ac = static_cast<int>(a);
    int Bc = static_cast<int>(b);
    int Cc = static_cast<int>(c);

    int result;
    if ((Ac & Bc) % 2 != 0) { // Операцiя ЧИ
        if (x < 3 && Bc != 0) {
            result = static_cast<int>(a * x * x - b * x + c);
        }
        else if (x > 3 && Bc == 0) {
            result = static_cast<int>(x - a / x - c);
        }
        else {
            result = static_cast<int>(x / c);
        }
    }
    else {
        result = static_cast<int>(a * x * x - b * x + c);
    }

    return result;
}

int main() {
    setlocale(LC_CTYPE, "ukr");
    double a, b, c, X_start, X_end, H;

    // Введення значень a, b, c, Xпоч, Xкiн i H
    cout << "Введiть значення a: ";
    cin >> a;

    cout << "Введiть значення b: ";
    cin >> b;

    cout << "Введiть значення c: ";
    cin >> c;

    cout << "Введiть значення Xпоч: ";
    cin >> X_start;

    cout << "Введiть значення Xкiн: ";
    cin >> X_end;

    cout << "Введiть значення кроку H: ";
    cin >> H;

    // Виведення заголовка таблицi
    cout << "X\tF(X)" << endl;

    // Обчислення та виведення значень F у вигляді таблиці
    for (double x = X_start; x <= X_end; x += H) {
        int F = calculateF(a, b, c, x);
        cout << x << "\t" << F << endl;
    }

   
}
