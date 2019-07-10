请判断一个链表是否为回文链表。

示例 1:

```
输入: 1->2
输出: false
```
示例 2:
```
输入: 1->2->2->1
输出: true
```
你能否用 O(n) 时间复杂度和 O(1) 空间复杂度解决此题？

#### 利用数组存储节点

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
 * @return {boolean}
 */
var isPalindrome = function(head) {
    if (head === null) return true
    let arr = []
    while(head !== null) {
        arr.push(head)
        head = head.next
    }
    for (let i = 0; i < arr.length / 2; i++) {
        if (arr[i].val !== arr[arr.length - 1 - i].val) {
            return false
        }
    }
    return true
};
```

#### 进阶
// TODO
