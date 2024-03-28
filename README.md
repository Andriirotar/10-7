#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;
int main() {
    int k;
    cout << "Введіть ціле число k (k > 5): ";
    cin >> k;
    const int N = 15 * k;
    // Оголошення та ініціалізація вектора v
    vector<double> v(N);
    // Отримання вхідних даних (елементів вектора v)
    cout << "Введіть " << N << " чисел для вектора v:\n";
    for (int i = 0; i < N; ++i) {
        cin >> v[i];
    }
    // Побудова векторів g0, g1, g2, g3
    vector<double> g0(v.begin() + 2, v.begin() + 9 * k + 2);
    vector<double> g1(v.begin() + 10, v.begin() + 10 + 9 * k);
    vector<double> g2(v.begin() + 3, v.begin() + 10);
    vector<double> g3(v.begin() + 20, v.begin() + 20 + 9 * k);
    // Побудова векторів g4, g5, g6
    vector<double> g4(g0.size());
    vector<double> g5(g0.size());
    vector<double> g6(g0.size());
    transform(g0.begin(), g0.end(), g1.begin(), g4.begin(), plus<double>());
    transform(g3.begin(), g3.end(), g2.begin(), g5.begin(), minus<double>());
    transform(g0.begin(), g0.end(), g6.begin(), [k](double value) { return value / k; });
    // Обчислення значення G
    double G = 0.0;
    for (int j = 1; j < g0.size(); ++j) {
        double maxGj = max({ g0[j], g1[j], g2[j], g3[j], g4[j], g5[j], g6[j] });
        double minGj_1 = min({ g0[j - 1], g1[j - 1], g2[j - 1], g3[j - 1], g4[j - 1], g5[j - 1], g6[j - 1] });
        G += maxGj - minGj_1;
    }
    // Виведення результату
    cout << "Результат обчислення G: " << G << endl;
    return 0;
}
