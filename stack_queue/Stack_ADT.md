### Stack의 ADT 구현
- Stack의 기본이 되는 push, pop 연결리스트로 구현

```
class Node:
    def __init__(self, item, next):
        self.item = item
        self.next = next
```
스택을 연결리스트로 구현하기 위해 기본이 되는 자료형을 정의


```
class Stack:
    def __init__(self):
        self.top = None
        
    def push(self, item): # 새로 추가 시 마지막을 가리키게 
        self.top = Node(item, self.top)
        
    def pop(self): # 반환 시 마지막 데이터를 반환하고 이전 노드로 이동
        item = self.top.item
        self.top = self.top.next
        return item

stack = Stack()
stack.push(1)
stack.push(2)
stack.push(3)

for _ in range(3):
    print(stack.pop())
```
스택의 ADT 구현 기본적인 push와 pop만 구현, 예외 처리 등 기타 다른 함수는 미구현
