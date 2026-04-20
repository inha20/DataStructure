# 스택

<details>
    <summary>스택 개론</summary>
➜ top, elements, LIFO <br>
➜ top이 달라지면 구조가 바뀐다고 표현함.<br>
➜ 예시 <br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 입 출력을 역순으로.  <br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ undo(되돌리기).  <br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 이전폐이지로 이동.  <br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 함수 호출(시스템 스택). <br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 괄호 검사. <br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 미로 탐색. <br>
</details>

<details>
    <summary>파이썬 코드</summary>

    
```py
class ArrayStack:
    def __init__(self, capacity):
        self.capacity = capacity
        self.array=[None]*capacity
        self.top=-1

    def isEmpty(self):
        return self.top==-1
        
    def isFull(self):
        return self.top==(self.capacity-1)
        
    def push(self,e):
        if not self.isFull():
            self.top+=1
            self.array[self.top]=e
        else:
            print("OverFlow")
            pass

    def pop(self):
        if not self.isEmpty():
            self.top-=1
            return self.array[self.top+1]
        else:
            print("UnderFlow")
            pass 

    def peek(self):
        if not self.isEmpty():
            return self.array[self.top]
        else:pass

    def __str__(self):
        return str(self.array[0:self.top+1])
```

</details>
<details>
    <summary>후위식</summary>
➜ 괄호 없어, 연산자 우선순위 없어. <br>
➜ 수식을 읽으면 바로 계산 가능.<br>
&nbsp;&nbsp;&nbsp;&nbsp;⤷ 후위식으로 돌린 후 계산하기.  <br>
```py
from ArrayStack import ArrayStack

def evalPostFix(expr):
    s=ArrayStack(100)
    for token in expr:
        if token in "+-*/":
            val2=s.pop()
            val1=s.pop()
            if(token=="+"): s.push(val1+val2)
            if(token=="-"): s.push(val1-val2)
            if(token=="*"): s.push(val1*val2)
            if(token=="/"): s.push(val1/val2)
        else:
            s.push(float(token))
    return s.pop()

expr1=['8','2','/','3','-','3','2','*','+']
print(expr1, "==>", evalPostFix(expr1))
```
```py


```
</details>
