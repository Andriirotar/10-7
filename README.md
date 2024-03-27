#include <iostream>
int main() {
    char ch;
    int spaces = 0, tabs = 0, newlines = 0;
    // Зчитування символів зі стандартного вводу
    while (std::cin.get(ch)) {
        // Підрахунок кількості пробілів, табуляцій і нових рядків
        if (ch == ' ') {
            spaces++;
        } else if (ch == '\t') {
            tabs++;
        } else if (ch == '\n') {
            newlines++;
        }
    }
    // Виведення результатів у стандартний вивід
    std::cout << "Пробіли: " << spaces << std::endl;
    std::cout << "Табуляції: " << tabs << std::endl;
    std::cout << "Нові рядки: " << newlines << std::endl;
    return 0;
}
