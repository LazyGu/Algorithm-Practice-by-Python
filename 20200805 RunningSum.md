# Running Sum
## **Given an array nums. We define a running sum of an array as runningSum[i] = sum(nums[0]…nums[i]). Return the running sum of nums.**
### Example
#### Example 01:
```
Input: nums = [1,2,3,4] 
Output: [1,3,6,10]`
```
Explanation: Running sum is obtained as follows: [1, 1+2, 1+2+3, 1+2+3+4].

#### Example 02:
```
nput: nums = [1,1,1,1,1]
Output: [1,2,3,4,5]
```
Explanation: Running sum is obtained as follows: [1, 1+1, 1+1+1, 1+1+1+1, 1+1+1+1+1].

#### Example 03
```
Input: nums = [3,1,2,10,1]
Output: [3,4,6,16,17]
```

### Solution
#### Solution 01
```
class Solution01:
    def runningSum(self, nums):
        newnums = nums
        for i in range(1, len(nums)):
            newnums[i] = newnums[i-1] + nums[i]
        return newnums
    print(runningSum(nums,nums))
```

#### Solution 02
```
class Solution02:
    def runningSum(self, nums):
        if len(nums)==1:
            return nums
        cur = nums[0]
        res = [nums[0]]
        for i in range(1,len(nums)):
            cur = res[-1]
            res.append(cur+nums[i])
        return res
    print(nums)
    print(runningSum(nums, nums))
```

#### Solution 03
```
class Solution03:
    def runningSum(self, nums):
        for i in range(1, len(nums)):
            nums[i] = nums[i-1] + nums[i]
        return nums
    print(runningSum(nums,nums))
```
