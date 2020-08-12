# Can Place Flowers?
## Suppose you have a long flowerbed in which some of the plots are planted and some are not. However, flowers cannot be planted in adjacent plots - they would compete for water and both would die. Given a flowerbed (represented as an array containing 0 and 1, where 0 means empty and 1 means not empty), and a number n, return if n new flowers can be planted in it without violating the no-adjacent-flowers rule.
### Examples
```
Input: flowerbed = [1,0,0,0,1], n = 1
Output: True
```
```
Input: flowerbed = [1,0,0,0,1], n = 2
Output: False
```
### Note
```
The input array won't violate no-adjacent-flowers rule.
The input array size is in the range of [1, 20000].
n is a non-negative integer which won't exceed the input array size.
```
### Solutions
```
class Solution01:
    def canPlaceFlowers(self, flowerbed: List[int], n: int):
        if len(flowerbed) == flowerbed.count(0):
            return math.ceil(len(flowerbed) / 2) >= n  # 排除flowerbed全为0的情况

        count = 0
        index_1 = flowerbed.index(1)  # 确定首个1出现的位置
        if index_1 > 1:
            count += index_1 // 2  # 若首个1之前有0，确定可容纳花朵数
        # nums0表示两个1之间0的个数 
        nums0 = 0
        for i in flowerbed[index_1 + 1:]:  
            if i == 0:
                nums0 += 1
            else:
                count += (nums0 - 1) // 2  # 计算两个1之间0的个数并与2整除求得可容纳花朵数
                nums0 = 0
        if nums0 != 0:
            count += nums0 // 2  # 讨论以0结尾的情况
        return count >= n
```
```
class Solution:
    def canPlaceFlowers(self, flowerbed: List[int], n: int) -> bool:
        flowerbed = [0]+ flowerbed
        flowerbed = flowerbed+[0]  # 前后加0应对首尾有两个0的情况
        for i in range(1,len(flowerbed)-1):
            if  flowerbed[i-1] == 0 and flowerbed[i] == 0 and flowerbed[i+1] == 0:
                n = n-1
                flowerbed[i] = 1  #当i左右皆为0的时候插入1
        return n<=0
```
