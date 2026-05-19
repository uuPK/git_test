# 快速排序

快速排序是一种高效的排序算法，采用分治思想。

## 算法步骤

1. 从数列中选择一个基准值（pivot）。
2. 将比基准值小的元素放到左边，比基准值大的元素放到右边。
3. 对左右两边的子序列递归执行快速排序。

## 伪代码

```text
function quickSort(arr)
    if length(arr) <= 1
        return arr
    pivot = arr[floor(length(arr) / 2)]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    return quickSort(left) + middle + quickSort(right)
```

## C++ 实现

```cpp
#include <iostream>
#include <vector>

void quickSort(std::vector<int>& arr, int left, int right) {
    if (left >= right) return;
    int pivot = arr[(left + right) / 2];
    int i = left;
    int j = right;
    while (i <= j) {
        while (arr[i] < pivot) i++;
        while (arr[j] > pivot) j--;
        if (i <= j) {
            std::swap(arr[i], arr[j]);
            i++;
            j--;
        }
    }
    if (left < j) quickSort(arr, left, j);
    if (i < right) quickSort(arr, i, right);
}

int main() {
    std::vector<int> data = {33, 10, 55, 71, 29, 3, 18};
    quickSort(data, 0, static_cast<int>(data.size()) - 1);
    for (int value : data) {
        std::cout << value << " ";
    }
    std::cout << std::endl;
    return 0;
}
```

## 特点

- 平均时间复杂度：O(n log n)
- 最坏时间复杂度：O(n^2)
- 空间复杂度：O(log n)
- 不稳定排序
