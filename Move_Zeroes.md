给定一个数组 nums，编写一个函数将所有 0 移动到数组的末尾，同时保持非零元素的相对顺序。

示例:

```
输入: [0,1,0,3,12]
输出: [1,3,12,0,0]
```

说明:

必须在原数组上操作，不能拷贝额外的数组。
尽量减少操作次数。

#### 时间复杂度有点高

每次交换的时候看看后面是不是都是 0 ，有点蠢的做法 ：（

```
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var moveZeroes = function(nums) {
    for (let i = 0; i < nums.length; ) {
        if (nums[i] !== 0) {
            i++
        } else {
            nums.splice(i,1)
            nums.push(0)
            let flag
            for (let j = i; j < nums.length; j++) {
                if (nums[j] !== 0) {
                    flag = false
                    break;
                }
                if (j === nums.length -1) {
                    flag = true
                }
            }
            if (flag) return nums    
        }
    }   
    return nums
};
```
