# 선택 정렬(Selection Sort)


## 선택 정렬이란?
* Selection Sort는 Bubble Sort과 유사한 알고리즘으로, 해당 순서에 원소를 넣을 위치는 이미 정해져 있고,</br> 어떤 원소를 넣을지 선택하는 알고리즘이다.
* 즉, 배열에서 해당 자리를 선택하고 그 자리에 오는 값을 찾는 정렬 알고리즘이다.


## Process
1. 주어진 배열 중에 최소값을 찾는다.
2. 그 값을 맨 앞에 위치한 값과 교체한다.
3. 맨 처음 위치를 뺀 나머지 배열을 같은 방법으로 교체한다.


## C++ Code(Ascending)
```C++
//Selection Sort
 
#include<iostream>
using namespace std;
 
void Swap(int &a, int &b){
    int tmp;
    tmp = a;
    a = b;
    b = tmp;
}
 
void SelectionSort(int *arr, int len){
 
    int min_idx;
    for(int i=0; i<len-1; i++){
        min_idx = i;
 
        for(int j=i+1; j<len; j++){
            if(arr[min_idx] > arr[j]){
                min_idx = j;
            }
        }
        Swap(arr[min_idx], arr[i]);
    }
 
}
 
int main(void){
 
    int arr[5] = {3, 5, 1, 2, 4};
    int len = 5;
 
    for(int i=0; i<len; i++){
        cout << arr[i] << " ";
    }
    cout << endl;
 
 
    SelectionSort(arr, len);
 
    for(int i=0; i<len; i++){
        cout << arr[i] << " ";
    }
 
    return 0;
}
```

https://github.com/GimunLee/tech-refrigerator/blob/master/Algorithm/resources/selection-sort-001.gif?raw=true
## 시간복잡도

* 배열의 요소가 N개라고 가정해봅니다. </br> 우선 첫번째 자리에 올 요소를 찾기 위해 N개의 요소를 검사합니다.
* 이제 두번째 자리에 올 요소를 찾으려면 N-1개의 요소를 검사하고 세번째는 N-2, 네번째는 N-3 ...이 됩니다.
모두 다 더하면 N + N-1 + N-2 + .... + 1 = N(N-1)/2가 되고, 시간 복잡도는 O(N^2)가 됩니다.
