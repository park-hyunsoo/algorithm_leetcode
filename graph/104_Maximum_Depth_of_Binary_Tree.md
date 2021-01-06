### 트리의 깊이
- 트리의 깊이를 구하는 문제
- 완전 이진 트리가 아니므로 DFS 가 아닌 BFS로 구하고
- DFS는 스택, BFS는 큐를 사용해 구현한다.

```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def maxDepth(self, root: TreeNode) -> int:
        if root is None:
            return 0
        
        queue = collections.deque([root])
        depth = 0
        
        while queue:
            depth += 1
            for _ in range(len(queue)):
                cur_root = queue.popleft() # 큐에 값을 꺼내서
                
                if cur_root.left:
                    queue.append(cur_root.left) # 왼쪽 확인 후 추가
                    
                if cur_root.right:
                    queue.append(cur_root.right) # 오른쪽 확인 후 추가
        
        return depth
```
레벨 별로 모든 트리의 노드를 저장하고 깊이를 증가 시킨다.
