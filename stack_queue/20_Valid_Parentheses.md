### 유효한 괄호
- 괄호로 된 입력 값이 올바른지 판단

```
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        table = {
            ')' : '(',
            ']' : '[',
            '}' : '{',
        }
        
        for char in s:
            if char not in table:
                stack.append(char)
        
            elif not stack or table[char] != stack.pop():
                return False
        
        return len(stack) == 0
```
stack을 사용한 기본 문제로 매핑 테이블을 만들고 ( [ { 는 push 를 하고 ) ] } 를 만나면 pop을 한 뒤 일치하는지 비교 
