# 연결리스트
> 큐로 스택 만들기
<details>
    <summary>파이썬 코드</summary>

    
```py
#단방향 노드
class Node:
    def __init__(self, e, link=None):
        self.data = e
        self.link=link

# 단순 연결 스택 글래스   
class LinkedStack:
    def __init__(self):
        self.top=None

    def isEmpty(self):
        return self.top==None
    
    def isFull(self):
        return False
    
    def push(self,item):
        n=Node(item)
        n.link=self.top
        self.top=n
        #self.top=Node(item, self.top)

    def pop(self):
        if not self.isEmpty():
            n=self.top
            self.top=n.link
            return n.data
        
    def peek(self):
        if not self.isEmpty():
            return self.top.data
        
    def size(self):
        node=self.top
        count=0
        while node != None:
                node=node.link
                count+=1
        return count

    def __str__(self):
        arr=[]
        node=self.top
        while node != None:
            arr.append(node.data)
            node=node.link
        return str(arr)
    
#Test
if __name__=="__main__":
    s=LinkedStack()
    print("연결리스트 스택 : ", s)
    msg=input("문자열 입력: ")
    for c in msg:
        s.push(c)
    print("문자열 연결리스트 스택 : ", s)  
    print("노드의 갯수: ", s.size(), "개") 
    print("문자열 pop 결과:", end='')
    while not s.isEmpty():
        print(s.pop(), end=' ')

    

```

</details>
