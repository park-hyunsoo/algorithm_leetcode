### 홀짝 연결 리스트
홀수 짝수를 찾는것이 아닌 연결리스트의 홀수 노드 뒤에 짝수 노드가 오게
시간복잡도 O(n), 공간복잡도 O(1)
홀수와 짝수 노드를 기억하고 별개의 연결리스트 두개로 나눈 뒤 결합

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def oddEvenList(self, head: ListNode) -> ListNode:
        
        if head is None:
            return None
        
        odd = head
        even = head.next
        even_head = head.next
        
        while even and even.next:
            odd.next = odd.next.next
            odd = odd.next
            even.next = even.next.next
            even = even.next
            
        odd.next = even_head
        
        return head
```        
