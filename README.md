#include <iostream>
using namespace std;
int factorial(int n) {
    if (n < 0) {
        throw "Факторіал від'ємного числа неможливо обчислити";
    }
    int result = 1;
    for (int i = 2; i <= n; ++i) {
        result *= i;
    }
    return result;
}
int main() {
    int n;
    cout << "Введіть число n: ";
    cin >> n;
    try {
        int fact = factorial(n);
        cout << "Факторіал " << n << " = " << fact << endl;
    }
    catch (const char* message) {
        cerr << "Помилка: " << message << endl;
    }
    return 0;
}
