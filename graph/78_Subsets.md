### 부분집합
- 주어진 리스트의 모든 부분집합
- DFS로 모든 경로를 탐색하면 되는데
- 부분 집합이므로 완성된 경로가 아닌 모든 경로가 답이 된다.

```
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        result = []
        
        def dfs(index, path):
            result.append(path)
            
            for i in range(index, len(nums)):
                dfs(i+1, path+[nums[i]])
            
        dfs(0, [])
        
        return result 
```  
 
