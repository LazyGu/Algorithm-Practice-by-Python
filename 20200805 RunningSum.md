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
        newnums = nums
        for i in range(1, len(nums)): #通过循环函数做叠加
            newnums[i] = newnums[i-1] + nums[i] #列表中第i个数等于前一个数与该数的和
        return newnums
    print(runningSum(nums,nums))
```

```
class Solution02:
    def runningSum(self, nums):
        if len(nums)==1: #首先讨论只有1个元素的情况
            return nums 
        cur = nums[0]
        res = [nums[0]] #新建列表res仅包含nums首元素
        for i in range(1,len(nums)):
            cur = res[-1] #cur设定为res最新导入的元素
            res.append(cur+nums[i]) #列表res添加cur与nums下一位的和
        return res
    print(nums)
    print(runningSum(nums, nums))
```

```
class Solution03:
    def runningSum(self, nums):
        for i in range(1, len(nums)):
            nums[i] = nums[i-1] + nums[i]
        return nums
    print(runningSum(nums,nums)) #这个就是Solution01，不知道是谁抄谁呢...
```

### Source
[LeetCode](https://leetcode-cn.com/)
