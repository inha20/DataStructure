# 스택 이어서 

> Depth First Search는 stack을 이용하는 알고리즘

<details>
    <summary>파이썬 코드</summary>

    
```py

from ArrayStack import ArrayStack

map = [
    [1,1,1,1,1,1],
    ['e',0,0,0,0,1],
    [1,0,1,0,1,1],
    [1,1,1,0,0,'x'],
    [1,1,1,0,1,1],
    [1,1,1,1,1,1]
]

MAXSIZE=6

def isValidPos(x,y):
    if 0<=x<MAXSIZE and 0<=y<MAXSIZE:
        if map[y][x]==0 or map[y][x]=='x':
            return True
    return False

def DFS():
    print("DFS: ")
    stack=ArrayStack(100)
    stack.push((0,1))

    while not stack.isEmpty():
        here=stack.pop()
        print(here, end="=>")

        (x,y)=here

        if(map[y][x]=='x'):
            return True
        else:
            map[y][x]="."
            if isValidPos(x,y-1):stack.push((x,y-1))#상
            if isValidPos(x,y+1):stack.push((x,y+1))#하
            if isValidPos(x-1,y):stack.push((x-1,y))#좌
            if isValidPos(x+1,y):stack.push((x+1,y))#우
        print("현재 스택: ", stack)
    return False


result = DFS()
if result: print("미로 탈출 성공!")
else: print("미로 탈출 실패")
print("\n[최종 지도]")
for row in map:
    print(row)



```

</details>
