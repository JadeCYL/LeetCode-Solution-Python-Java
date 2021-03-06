# 16 - 最接近的三数之和

## 题目描述
![problem](images/16.png)

>审题：
看到题目的我，悄悄点开了旁边的相关话题，恩又有双指针，大概知道怎么做了hiahia＼＼\٩('ω')و//／／
[三数之和-传送门](https://rosevil1874.github.io/2018/04/05/1.%E4%B8%A4%E6%95%B0%E4%B9%8B%E5%92%8C/#more)

## 方法[类似三数之和]
1. 将数组排序；
2. 第一层循环遍历元素；
3. 第二层循环使用双指针向中间靠拢检查；
4. 遇到更符合条件的更新结果。

```python
class Solution:
    def threeSumClosest(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        nums.sort()
        closest = nums[0] + nums[1] + nums[2]
        for i in range(len(nums)):
            j, k = i + 1, len(nums) - 1
            while j < k:
                value = nums[i] + nums[j] + nums[k]
                closest = value if abs(target - value) < abs(target - closest) else closest
                if value == target:
                    return target
                elif value > target:
                    k -= 1
                else:
                    j += 1
        return closest
```
