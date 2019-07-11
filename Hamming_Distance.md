两个整数之间的汉明距离指的是这两个数字对应二进制位不同的位置的数目。

给出两个整数 x 和 y，计算它们之间的汉明距离。

注意：
0 ≤ x, y < 231.

示例:

```
输入: x = 1, y = 4

输出: 2

解释:
1   (0 0 0 1)
4   (0 1 0 0)
       ↑   ↑

上面的箭头指出了对应二进制位不同的位置。
```

#### 转成二进制再判断
```
/**
 * @param {number} x
 * @param {number} y
 * @return {number}
 */
var hammingDistance = function(x, y) {
    let x1 = parseInt(x, 10).toString(2)
    let y1 = parseInt(y, 10).toString(2)
    let lenX1 = x1.length
    let lenY1 = y1.length
    if (lenX1 > lenY1) {
        y1 = '0'.repeat(lenX1 - lenY1) + y1
    } else {
        x1 = '0'.repeat(lenY1 - lenX1) + x1
    }
    let len =  x1.length
    let count = 0
    for (let i = 0; i < len; i++) {
        if (x1.charAt(i) !== y1.charAt(i)) {
            count += 1
        }
    }
    return count
};
```
