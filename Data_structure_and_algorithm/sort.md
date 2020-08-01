## 排序算法(Python)
- [插入排序](#插入排序)
- [快速排序](#快速排序)
- [选择排序](#选择排序)
- [冒泡排序](#冒泡排序)
- [归并排序](#归并排序)
- [堆排序](#堆排序)
- [希尔排序](#希尔排序)

### 插入排序

```
def insertion_sort(arr):
    for i in range(1, len(arr)):
        idx = i - 1
        key = arr[i]
        while idx > 0 and key < arr[idx]:
            arr[idx + 1] = arr[idx]
            idx -= 1
        arr[idx + 1] = key
    return arr
    # return ' '.join(str(i) for i in arr)
```

### 快速排序
```
def quick_sort(arr):
    if len(arr) < 2:
        return arr
    else:
        tmp = arr[0]
        less = [i for i in arr[1:] if i < tmp]
        great = [i for i in arr[1:] if i >= tmp]
        return quick_sort(less) + [tmp] + quick_sort(great)
```

### 选择排序
```
def selection_sort(arr):
    for i in range(len(arr) - 1):
        idx = i
        for j in range(i + 1, len(arr)):
            if arr[j] < arr[idx]:
                idx = j
        arr[i], arr[idx] = arr[idx], arr[i]
    return arr
```
### 冒泡排序
```
def bubble_sort(arr):
    n = len(arr)
    for i in range(n - 1):
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
    return arr
```
### 归并排序
```
def merge_sort(arr):
    if len(arr) < 2:
        return arr
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])
    merged = []
    while left and right:
        merged.append(left.pop(0) if left[0] <= right[0] else right.pop(0))
    merged.extend(left if left else right)
    return merged
```
### 堆排序
```
def heap_tree(arr, i, n):
    large = i
    l = 2 * i + 1
    r = 2 * i + 2
    if l < n and arr[l] > arr[large]:
        large = l
    if r < n and arr[r] > arr[large]:
        large = r
    if large != i:
        arr[large], arr[i] = arr[i], arr[large]
        heap_tree(arr, large, n)


def heap_sort(arr):
    for i in range(len(arr) - 1, -1, -1):
        heap_tree(arr, i, len(arr))

    for i in range(len(arr) - 1, 0, -1):
        arr[0], arr[i] = arr[i], arr[0]
        heap_tree(arr, 0, i)
    return arr
```
### 希尔排序
```
def shell_sort(arr):
    gap = len(arr) // 2
    while gap > 0:
        for i in range(gap, len(arr)):
            key = arr[i]
            idx = i - gap
            while idx >= 0 and arr[idx] > key:
                arr[idx + gap] = arr[idx]
                idx -= gap
            arr[idx + gap] = key
        gap = gap // 2
    return arr
```
### 主函数测试
```
def main():
    arr = [1, 4, 5, 2, 41, 4, 24, 5, 100]
    print("Original arr:      ", arr)

    # insertion_sort_arr = insertion_sort(arr)
    # quick_sort_arr = quick_sort(arr)
    # bubble_sort_arr = bubble_sort(arr)
    # selection_sort_arr = selection_sort(arr)
    # merged_sort_arr = merge_sort(arr)
    # heap_sort_arr = heap_sort(arr)
    shell_sort_arr = shell_sort(arr)

    # print("After insertion sort: ", insertion_sort_arr)
    # print("After quick sort:  ", quick_sort_arr)
    # print("After bubble sort: ", bubble_sort_arr)
    # print("After selection sort: ", selection_sort_arr)
    # print("After merged sort: ", merged_sort_arr)
    # print("After heap sort: ", heap_sort_arr)
    print("After shell sort: ", shell_sort_arr)
  ```

  部分代码参考[菜鸟教程](https://www.runoob.com/python3/python3-examples.html)。
