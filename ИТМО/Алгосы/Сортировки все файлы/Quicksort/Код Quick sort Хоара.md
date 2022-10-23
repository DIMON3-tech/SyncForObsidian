```cpp
#include <iostream>  
void quick_sort(int *array, int l, int r) {  
    int i = l;  
    int j = r;  
    int x = array[(l + r) / 2]; // pivot  
  
    while (i <= j) {  
        while (array[i] < x) { // бежим до тех пор, пока не встретили элемент  
            // который больше либо равен pivot, тогда вылетаем из цикла и точно знаем            // , что текущий элемент массива больше чем pivot            i++;  
        }  
        while (array[j] > x) {  
            j--; // так же , как с i, когда вылетим из вайла, значит array[j] меньше, чем  
            // pivot, значит свапаем        }  
        if (i <= j) {  
            std::swap(array[i++], array[j--]); // свапаем элементы на один больше  
            // каждого индекса        }  
    }  
    if (l < j) { // если левый индекс и правый не дошли друг до друга, значит еще можно  // сортировать        
	    quick_sort(array, l, j);  
    }  
    if (r > i) { // если правый индекс и левый не дошли друг до друга, сортируем еще  
        quick_sort(array, i, r);  если j сдвинулся на 1, тогда дальше будем сортировать с начала до длина-1 , то есть массив для антиквиксорта это массив, где i и j сдвигаются каждый раз на 1
    }  
}  
  
int main(){  
    int n;  
    std::cin >> n;  
    int array[n];  
    for(int i = 0; i < n; i++){  
        std::cin >> array[i];  
    }  
    quick_sort(array, 0, n - 1);  
  
    for(int i = 0; i < n; i++){  
        std::cout << array[i] << " ";  
    }  
  
    return 0;  
}
```
