将两个有序链表合并为一个新的有序链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。 

示例：

> 输入：1->2->4, 1->3->4
> 
> 输出：1->1->2->3->4->4

```
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var mergeTwoLists = function(l1, l2) {
    // 先定义 l4 后定义 l3 是因为本来准备用数组输出的，但是 LeetCode 好像必须是链表，只能重新加了一个链表结构
    var l4 = new ListNode(null)
    
    var insert = function(value) {
        var p = l4
        while(p.next !== null) {
            p = p.next
        }
        p.next = new ListNode(value);
    }
    
    let l3 = []

    while(l1 !== null && l2 !== null) {
        if (l1.val < l2.val) {
            l3.push(l1.val)
            l1 = l1.next
        } else {
           l3.push(l2.val)
            l2 = l2.next
        }
    }
    
    while (l1 !== null) {
		l3.push(l1.val)
		l1 = l1.next
	}
    
 	while (l2 !== null) {
		l3.push(l2.val)
		l2 = l2.next
	}

    for (let i = 0; i < l3.length; i++) {
        insert(l3[i]) 
    }
    l4 = l4.next
    return l4
};
```

以前写过链表：
```
 var Node =  function(value){
        this.value = value;
        this.next = null;
    }
    var myList =  function(){

        this.head = new Node(null);    //设头结点为空

        this.insert = function(value){    //插入节点
            var p = this.head;
            while(p.next!=null){
                p = p.next;
            }
            p.next = new Node(value);
        }

        this.print = function(){    //打印节点
            var p = this.head;
            while(p.next!=null){
                p = p.next;
                document.write(p.value+" ");
            }

        }

        this.findNode = function(position){    //寻找某个位置的节点
            if(position<0) return;
            var p = this.head;
            var i = 0;
            while(p.next!=null && i<position){
                i++;
                p = p.next;
            }
            return p;    //若position大于链表长度返回最后一个
        }

        this.remove = function(position){    //移除第position个节点
            this.findNode(position-1).next=this.findNode(position).next;

        }

        this.length=function(){    //链表长度
            var len = 0;
            var p = this.head;
            while(p.next!=null){
                len++;
                p = p.next;
            }
            document.write(len);
        }
    }
    var list = new myList();
    list.insert("a");
    list.insert("b");
    list.insert("c");
    list.insert("d");
    list.print();    //a b c d
    list.remove(2);    
    list.print();    //a c d
    list.length();    //3
```
