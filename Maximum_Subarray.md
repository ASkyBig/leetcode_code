给定一个整数数组 nums ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。

示例:
```
输入: [-2,1,-3,4,-1,2,1,-5,4],
输出: 6
解释: 连续子数组 [4,-1,2,1] 的和最大，为 6。
```

```
/**
 * @param {number[]} nums
 * @return {number}
 */
var maxSubArray = function(nums) {
    if (nums.length === 1) return nums[0]
    
    let sum = nums[0];
    let currentSum = 0;

    let s = 0
	  let e = 0

    for (let i = 0; i < nums.length; i++) {
        currentSum += nums[i];

        if (currentSum > sum) {
            sum = currentSum;
	    e = i;
        }
        if(currentSum < 0) {
            currentSum = 0;
	    s = i+1;
        }
    }
    if (sum < 0) {
        return Math.max(...nums);
	
    } else {
	for (let j = s; j < e+1; j++) {
	    console.log(nums[j]) // 具体的元素也可以拿出来，只写了正数的情况：
	}
        return sum;
    }
};
```
