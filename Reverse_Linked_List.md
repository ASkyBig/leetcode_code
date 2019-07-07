反转一个单链表。

示例:

```
输入: 1->2->3->4->5->NULL
输出: 5->4->3->2->1->NULL
```

```
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
var reverseList = function(head) {
    if (!head) return head
    let arr = []
    while(head !== null) {
        arr.push(head)
        head = head.next
    }

    for (let i = arr.length - 1; i > 0; i--) {
        arr[i].next = arr[i-1]
    }
    arr[0].next = null
    return arr[arr.length-1]
};
```
