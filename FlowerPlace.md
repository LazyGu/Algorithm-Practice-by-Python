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
    def canPlaceFlowers(self, flowerbed: List[int], n: int) -> bool:
        # 第一步主要是为了防止flowerbed中全是0导致index(1)时出错， math.ceil用于向上取整
        if len(flowerbed) == flowerbed.count(0):
            return math.ceil(len(flowerbed) / 2) >= n

        count = 0
        index_1 = flowerbed.index(1)
        if index_1 > 1:
            count += index_1 // 2
        # nums0表示两个1之间0的个数
        nums0 = 0
        for i in flowerbed[index_1 + 1:]:
            if i == 0:
                nums0 += 1
            else:
                count += (nums0 - 1) // 2
                nums0 = 0
        if nums0 != 0:
            count += nums0 // 2
        return count >= n
```
