Given an array of integers, return indices of the two numbers such that they add up to a specific target.  
You may assume that each input would have exactly one solution, and you may not use the same element twice.  

**Example:**
```
Given nums = [2, 7, 11, 15], target = 9,
Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

JavaScript:
```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */

// Version 1
var twoSum = function(nums, target) {
    for (let i = 0; i < nums.length; i++) {
        for (let j = i + 1; j < nums.length; j++) {
            if (nums[i] + nums[j] === target) {
                return [i, j];
            }
        }
    }
};

// Version 2, use map to reduce time complexity
var twoSum = function(nums, target) {
    let map = {}, complement;
    for (let i = 0; i < nums.length; i++) {
        map[nums[i]] = i;
    }
    for (let i = 0; i < nums.length; i++) {
        complement = target - nums[i];
        if (map.hasOwnProperty(complement) && map[complement] !== i) {
            return [i, map[complement]];
        }
    }
};

// Version 3, one-pass loop
var twoSum = function(nums, target) {
    let map = {}, complement;
    for (let i = 0; i < nums.length; i++) {
        complement = target - nums[i];
        if (map.hasOwnProperty(complement)) {
            return [i, map[complement]];
        }
        map[nums[i]] = i;
    }
};
```
