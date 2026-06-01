# 정렬
오름차순과 내림차순, 비교 가능하면 정렬 할 수 있음.<br>
여려개의 필드 중 정렬 기준 필드를 정렬 키 sort key라 한다.
## 선택정렬
하나 잡아서 맨 앞으로.O(n^2).

<details>
    <summary>파이썬 코드</summary>

    
```py
class SortAlgorism:
    def __init__(self, capacity=100):
        self.capacity=capacity
        self.array=[None]*capacity
        self.size=0

    def selection_sort(A):
    
    def PrintStep(arr, val):


def selection_sort(A):
    n=len(A)
    for i in range(n-1):
        least=i
        for j in range(i+1,n):
            if(A[j]<A[least]):
                least=j
        A[i], A[least] = A[least], A[i]
        printStep(A, i+1)

def PrintStep(arr, val):
    print("step=%2", val, end='')
    print(arr)
```

</details>

## 버블정렬
하나 잡아서 맨 앞으로.O(n^2).


## 삽입정렬
