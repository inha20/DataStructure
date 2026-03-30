# 리스트 : 선형 자료구조

> 0을 뒤로 옮기기

<details>
    <summary>리스트 개론</summary>
➜ 항목들은 순서와 위치를 가짐. <br>
➜ 임의의 위치에서 삽입, 삭제 가능.<br>
➜ 연산에 대한 인자의 갯수는 0개 이상.<br>
➜ 배열 구조 : 삽입, 삭제시 크기 변경. vs 연결 구조 : 구현이 복잡하고 항목 접근이 O(n)으로 느림.<br>
</details>

<details>
    <summary>파이썬 코드</summary>
    
```py
#데이터멤버_전역변수선언
capacity=100
size=0
array=[None]*capacity

#isEmpty 선언
def isEmpty():
    if size==0 :
        return True
    else : 
        return False

#isFull 선언
def isFull():
    if size==capacity :
        return True
    else :
        return False

#getEntry 선언
def getEntry(pos):
    if 0<=pos<size:
        return array[pos]
    else:
        return None
 
#insert 선언
def getEntry(pos,e):
    global size
    if 0<=pos<size and not isFull():
        for i in range(size, pos,-1):
            array[i]=array[i-1] 
        array[pos]=e
        size+=1
        return array[pos]
    else:
        print("리스트가 오버플로우 또는 유효하지 않은 삽입 위치")
        exit()


#delete 선언
def delete(pos):
    global size
    if 0<=pos<size and not isEmpty():
        R=array[pos]
        for i in range(pos, size-1):
            array[i]=array[i+1] 
        size-=1
        return R
    else:
        print("리스트가 언더플로우 또는 유효하지 않은 삽입 위치")
        exit()
```

    
</details>

# 집합 : 비선형 자료구조


<details>
    <summary>투 포인터 활용</summary>
    
```python
ExampleInputList = [0, 1, 0, 2, 3, 0, 0]
IndexZero = 0
for Index, Value in enumerate(ExampleInputList):
    if Value != 0:
        ExampleInputList[IndexZero] = Value
        if IndexZero != Index:
            ExampleInputList[Index] = 0
        IndexZero += 1
print(ExampleInputList)
```
선형시간과 상수공간을 만족시킨다는 점에서 기존보다 개선된 알고리즘이다. <br>
Value가 0일 때 작동되는 코드 없이, 0이지 않을 때만 위와 같은 코드가 작동한다. 그럼에도 불구하고 0이 뒤쪽으로 옮겨지는 것은 어떻게 한 것일까? temp=a; a=b; b=temp를 메서드로 쓰기라도 했단 말인가? 이를 사용하는 매우 비효율적인 코드 대신에, 더 간단한 0이 뒤로 밀려나는 방법을 사용하였다. Value가 0이지 않을 경우에만 리스트 앞쪽으로 값을 가져오고(if Value != 0: ; ExampleInputList[IndexZero] = Value), 이후 기존 자리에 0을 대입 연산하는 조건으로 (if IndexZero != Index: )를 배치시킨 후 그 다음 숫자를 받을 준비를 위해 (IndexZero += 1)를 둔 것이다. 들여쓰기를 적절히 조절하는 것도 잊지 말자.
</details>






