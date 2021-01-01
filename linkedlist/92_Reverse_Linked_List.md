### 역순 연결 리스트
- 인덱스 m에서 n 까지를 역순으로 만들어라 인덱스는 1부터 시작

```
m = 2, start = 1, end = 2
1->2->3->4->5->6
1->3 
2->4
3->2
1 cycle을 돌아도 start, end는 그대로 1, 2
1->3->2->4->5->6
1->4 # end는 한칸 이동하였으므로 
```
시작점과 종료점을 사용해서 연결리스트의 연결을 바꿔나간다.

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseBetween(self, head: ListNode, m: int, n: int) -> ListNode:
        if not head or m == n :
            return head
        
        root = start = ListNode(None)
        start.next = head
        
        for _ in range(m - 1):
            start = start.next
        end = start.next
        
        for _ in range(n - m):
            print(end.val)
            tmp = start.next # 역순으로 정렬되므로 임시 저장  
            start.next = end.next # 기준 점의 다음은 그 다음을 가리켜야 되고 
            end.next = end.next.next # 다음점의 다음은 그 다음을 가리켜야 된다.  
            start.next.next = tmp # 기준 점의 다음이 다음이 tmp를 가르켜야 된다.  
            
        return root.next
```    

