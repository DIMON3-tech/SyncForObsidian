>[!Минусы сортировки именно в таком виде]
>Размер массива count_every_number не определен заранее. Если надо отсортировать числа 1 2 100, нужен массив размером 100, хотя у нас всего 3 числа. Кроме того, реализация неустойчивая.


```cpp
#include <iostream>  
void CountingSort(int *array, int n) {  
    int k = 100;  
    int count_every_number[k]; // каждый i элемент массива хранит количество чисел i в массиве  
    for(int i = 0; i < k; i++){  
        count_every_number[i] = 0;  
    }  
    for(int i = 0; i < n; i++){  
        count_every_number[array[i]] += 1; // заполнили массив count_every_number  
        // , то есть посчитали сколько раз каждое число встречается в array    }  
    int pos = 0;  
    for (int number = 0; number < k; number++){  
        for(int i = 0; i < count_every_number[number]; i++){  
            array[pos] = number; // столько раз, сколько number  
            // есть в цикле записали его в array (двигаемся за счет pos)            pos = pos + 1;  
        }  
    }  
  
}  
int main(){  
    int n;  
    std::cin >> n;  
    int array[n];  
    for(int i = 0; i < n; i++){  
        std::cin >> array[i];  
    }  
    CountingSort(array, n);  
  
    for(int i = 0; i < n; i++){  
        std::cout << array[i] << " ";  
    }  
  
    return 0;  
  
}
```
