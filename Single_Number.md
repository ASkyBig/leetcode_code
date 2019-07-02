给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。

说明：

你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？

示例 1:

```
输入: [2,2,1]
输出: 1
```

#### indexOf 和 lastIndexOf
```
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
    for (let i = 0; i < nums.length; i++) {
        if (nums.indexOf(nums[i]) === nums.lastIndexOf(nums[i])) {
            return nums[i];
        }
    }
};
```

#### 利用 Set 结构

set 之和减去原数组：）
```
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
    let sum = [...new Set(nums)].reduce((a,b) => {
        return a + b;
    }, 0)
    sum *= 2;
    for (let v of nums) {
        sum -= v;
    }
    return sum;
    
};
```
