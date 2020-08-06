# Running Sum 
## Given an array nums. We define a running sum of an array as runningSum[i] = sum(nums[0]…nums[i]). Return the running sum of nums.
### Examples
```
Input: nums = [1,2,3,4] 
Output: [1,3,6,10]`
```
Explanation: Running sum is obtained as follows: [1, 1+2, 1+2+3, 1+2+3+4].

```
nput: nums = [1,1,1,1,1]
Output: [1,2,3,4,5]
```
Explanation: Running sum is obtained as follows: [1, 1+1, 1+1+1, 1+1+1+1, 1+1+1+1+1].

```
Input: nums = [3,1,2,10,1]
Output: [3,4,6,16,17]
```

### Constraints
```
1 <= nums.length <= 1000
-10^6 <= nums[i] <= 10^6
```

### Solutions
```
class Solution01:
    def runningSum(self, nums):
        newnums = nums[0]
        for i in range(1, len(nums)):
            nums[i]=newnums + nums[i]
            newnums = nums[i]
        return nums
    print(runningSum(nums, nums))
```
```
class Solution02:
    def runningSum(self, nums):
        if len(nums) == 1:
            newnums = nums
            return newnums
        else:
            newnums = [nums[0]]
            for i in range(1, len(nums)):
                newnums.append(newnums[i-1]+nums[i])
            return newnums
    print(runningSum(nums,nums))
```
 
### Source
[LeetCode](https://leetcode-cn.com/)
