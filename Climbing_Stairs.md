假设你正在爬楼梯。需要 n 阶你才能到达楼顶。

每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？

注意：给定 n 是一个正整数。

示例 1：
```
输入： 2
输出： 2
解释： 有两种方法可以爬到楼顶。
1.  1 阶 + 1 阶
2.  2 阶
```

#### 直接递归
```
/**
 * @param {number} n
 * @return {number}
 */
var climbStairs = function(n) {
    if (n === 1) return 1;
    if (n === 2) return 2;
    return climbStairs(n-1) + climbStairs(n-2)
};
```
这样会导致栈溢出，所以可以存储一下已知的减少计算。

#### 改进递归
```
/**
 * @param {number} n
 * @return {number}
 */
const map = new Map()
var climbStairs = function(n) {
    if (n === 1) return 1;
    if (n === 2) return 2;
    if (map.has(n)) {
        return map.get(n);
    }
    value = climbStairs(n-1) + climbStairs(n-2)
    map.set(n, value);
    return value;
};
```
