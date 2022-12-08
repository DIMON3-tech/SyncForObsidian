```cpp
#include <iostream>
int main(){
    int size;
    std::cin>>size; // считал колво элементов

    int array[size];
    for(int y = 0; y < size; y++){
        std::cin >>array[y];
    }
      ;
    for(int i = 1; i < size; i++){
        int key = array[i];
        int j = i -1;
        while(key < array[j] && j >= 0){
            array[j + 1] = array[j];
            j -= 1;
        }
        array[j + 1] = key;
    }
    for(int j = 0; j < size; j++){
        std::cout<<array[j]<<" ";
    }
    return 0;
}
```