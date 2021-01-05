### 중복문자 제거
- 중복 문자를 제거하고 사전 식 순서로 나열
- 사전식 순서는 글자 그대로 사전에서 먼저 찾을 수 있는 순서
- ebcabc가 입력되면 eabc가 된다.
- e 문자 자체는 해당 문자열 내에서 사전 순으로는 가장 뒤에 있지만 
- e 는 입력 값에서 한 번만 등장하고 abc는 뒤이어서 등장하기 때문에 e의 위치를 변경할 수 없다.

```
class Solution:
    def removeDuplicateLetters(self, s: str) -> str:
        
        for char in sorted(set(s)):
            suffix = s[s.index(char):] # a, b, c 순서대로 문자열에서 시작 점을 찾아 문자열을 반환한다.
        
            if set(s) == set(suffix):
                return char + self.removeDuplicateLetters(suffix.replace(char, ''))
            
        return ''
```
문자열이 들어오면 집합을 사용해 정렬하고 해당 순서대로 문자열 위치를 찾아 새로운 분할된 문자열을 만든다.

그리고 새로 만들어진 문자열과 현재 문자 집합의 동일하다면 분할된 문자열로 재귀를 한다.

정렬 순서대로 분할이 되므로 사전 식 나열이 되고 중복을 제거한다.

```
class Solution:
    def removeDuplicateLetters(self, s: str) -> str:
        counter = collections.Counter(s)
        seen = set()  # 처리 여부 확인
        stack = []
        
        for char in s:
            counter[char] -= 1
            if char in seen:  # 처리 된 경우 넘어간다.
                continue
            
            # 뒤에 붙일 문자가 남아 있으면 스택에서 제거
            while stack and char < stack[-1] and counter[stack[-1]] >0:
                seen.remove(stack.pop())

            stack.append(char)
            seen.add(char)
            
        return ''.join(stack)

```
스택을 이용하여 풀수도 있고 각 문자의 개수를 카운팅 한 후 

각 문자를 돌면서 새로운 문자가 현재 스택보다 앞서고 현재 스택에 있는게 뒤에 더 존재한다면 스택에서 제거하고 새로운 문자를 추가한다.

없다면 제거하지 않고 새로운 문자를 그냥 추가한다.
