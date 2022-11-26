![[Pasted image 20221123184523.png]]
Процесс установки CLion:
![[Pasted image 20221122210824.png]]
![[Pasted image 20221122210838.png]]
![[Pasted image 20221122211058.png]]
Компилятор MinGw уже автоматически настроен:
![[Pasted image 20221122211424.png]]
Интерфейс IDE CLion:
![[Pasted image 20221122202642.png]]

==CMake== — кроcсплатформенная утилита для автоматической сборки программы из исходного кода.

Поставил галочку, чтобы cmake автоматически перезагружался, когда добавлены новые файлы для компиляции ![[Pasted image 20221122202929.png]]

Написал программу (простой консольный калькулятор на c++,  где вместо * используется . )
```cpp
#include <iostream>  
#include <cassert>  
#include <stack>  
  
int Sum(int x, int y) { return x + y; }  
int Difference(int x, int y) { return x - y; }  
int Multiplication(int x, int y) { return x * y; }  
int DivisionToInteger(int x, int y) { return x / y; }  
  
void TestSum() {  
    assert(Sum(2, 3) == 5);  
    assert(Sum(-2, 2) == 0);  
    std::cout << "testSum working correct" << std::endl;  
}  
  
void TestDif() {  
    assert(Difference(2, 3) == -1);  
    assert(Difference(-2, 2) == -4);  
    std::cout << "testDif working correct" << std::endl;  
}  
  
void TestMult() {  
    assert(Multiplication(2, 3) == 6);  
    assert(Multiplication(-2, 2) == -4);  
    std::cout << "testMult working correct" << std::endl;  
}  
  
void TestDivision() {  
    assert(DivisionToInteger(2, 3) == 0);  
    assert(DivisionToInteger(-2, 2) == -1);  
    std::cout << "testDivision working correct" << std::endl;  
}  
  
int main(int argc, char** argv){  
    std::stack<int> stack;  
    int number_from_stack;  
    char operation = '?';  
    for(int i = 1; i < argc; i++){  
        if(std::isdigit(argv[i][0])){  
            if(operation == '?'){  
                stack.push(int(argv[i][0] - '0'));  
            }  
            else {  
                number_from_stack = stack.top();  
                stack.pop();  
                switch(operation){  
                    case '+':  
                        stack.push(Sum(number_from_stack, int(argv[i][0] - '0')));  
                        break;  
                    case '-':  
                        stack.push(Difference(number_from_stack, int(argv[i][0] - '0')));  
                        break;  
                    case '.':  
                        stack.push(Multiplication(number_from_stack, int(argv[i][0] - '0')));  
                        break;  
                    case '/':  
                        stack.push(DivisionToInteger(number_from_stack, int(argv[i][0] - '0')));  
                        break;  
                }  
  
            }  
        } else {  
            operation = argv[i][0];  
        }  
    }  
    TestSum();  
    TestDif();  
    TestDivision();  
    TestMult();  
    std::cout << "Answer is: " << stack.top() << std::endl;  
}
```
![[Pasted image 20221122211601.png]]

Запустил код:
![[Pasted image 20221122211619.png]]
# Hot keys CLoin
1. Shift + Shift  - поиск файла/класса/символа/инструмента
2. Ctrl+Shift+A - найти действие (найти команду и выполнить)
3. Alt+Enter - показать действия над кодом
4. F2 - навигация между проблемами кода
5. Shift+F2 перейти к следующей или предыдущей выделенной ошибке
6. Ctrl+E просмотр последних файлов
7. Ctrl+/ - закомментировать строку/строки
8. Shift+Tab - Сдвингуть блок кода влево
9. Tab - сдвинуть блок кода вправо
10. Ctrl+X - удалить строку, на которую указывает курсор, полностью
11. Ctrl + F5 запустить код
