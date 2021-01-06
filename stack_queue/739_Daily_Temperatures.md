### 일일 온도
- 매일의 화씨 온도 리스트를 받아 더 따뜻한 날씨를 위해서는 며칠을 더 기다려야 하는지를 출력
- Input: T = [73, 74, 75, 71, 69, 72, 76, 73]
- Output: [1, 1, 4, 2, 1, 1, 0, 0].

```
class Solution:
    def dailyTemperatures(self, T: List[int]) -> List[int]:
        answer = [0] * len(T) # 정답 리스트 
        stack = []
        
        for i, cur in enumerate(T):
            
            # 현재 온도가 스택의 마지막 값보다 크다면 정답 계산
            while stack and cur > T[stack[-1]]:
                last = stack.pop()
                answer[last] = i - last
                
            stack.append(i)
            
        return answer
```
스택의 자료 형을 이용하여 풀 수 있고 스택에 인덱스를 저장하고 더 큰 값이 나올 경우 그 차이를 계산
