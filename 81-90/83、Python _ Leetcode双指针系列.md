
@Author：Runsen
@Date：2020/7/7


> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾 （作者：Runsen ）



作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。


前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)

今天高考，当年我就是一个辣鸡，现在还是一个辣鸡，祝高考的个个清华北大
。辣鸡的我决定继续更新Python教程，今天就开始了八十三、Python | Leetcode双指针系列。

@[toc]

# 双指针

双指针是一种解决问题的技巧或者思维方式，指在访问一个序列中的数据时使用两个指针进行扫描，两个指针可以是同向的，也可以是反向的；我们的关注点可以是这两个指针指向的两个元素本身，也可以是两个指针中间的区域。二分法的思想基于这种左右指针的实现



#  LeetCode 第 15题：三数之和


```csharp
#给你一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a，b，c ，使得 a + b + c = 0 ？请你找出所有满足条件且不重复的三元组。
# 注意：答案中不可以包含重复的三元组。 
# 示例： 
# 给定数组 nums = [-1, 0, 1, 2, -1, -4]，
#
#满足要求的三元组集合为：
#[
#  [-1, 0, 1],
#  [-1, -1, 2]
#]
# 
# Related Topics 数组 双指针
#leetcode submit region begin(Prohibit modification and deletion)
```


使用排序 + 双指针方法解决;

- 首先进行数组排序，时间复杂度 O(nlogn)
- 对数组nums进行遍历，每遍历一个值利用其下标 i，形成一个固定值 nums[i]
- 如果 nums[i] 大于0， 则三数之和必然无法等于0，直接结束循环
- 如果 nums[i] == nums[i-1]，则说明该数字重复，会导致结果重复，所以应该跳过
- 再使用前指针指向 start = i + 1处，后指针指向end = nums.length - 1，也就是结尾处
- 根据 sum = nums[i] + nums[start] + nums[end]结果，判断 sum 与 0 的大小关系，满足则添加进入结果，此时 start++; end-- 如果 sum < 0，则start++, 如果 sum > 0, 则 end--
- sum === 0 的时候还要考虑结果重复的情况
- nums[start] == nums[start+1] 则会导致结果重复，应该跳过，start++
- nums[end] == nums[end-1] 则会导致结果重复，应该跳过，end--










```csharp
class Solution:
    def threeSum(nums):
    nums.sort()
    # [-4, -1, -1, 0, 1, 2]
    res_list = []
    # 头部循环查找
    for i in range(len(nums)):
        if i == 0 or nums[i] > nums[i - 1]:
            # 最左端
            l = i + 1
            # 最右端
            r = len(nums) - 1
            while l < r:  # 正在查找
                three_sum = nums[i] + nums[l] + nums[r]
                if three_sum == 0:
                    res_list.append([nums[i], nums[l], nums[r]])
                    l += 1  # 右移一位
                    r -= 1  # 左移一位
                    while l < r and nums[l] == nums[l - 1]:
                        # 从左往右，相同数值直接跳过
                        l += 1
                    while r > l and nums[r] == nums[r + 1]:
                        # 从右往左，相同数值直接跳过
                        r -= 1
                elif three_sum > 0:
                    # 大于零，右边数值大，左移
                    r -= 1
                else:
                    # 小于零，左边数值小，右移
                    l += 1
    return res_list
```







#  LeetCode 第 16题：三数最近相加

```csharp
#给定一个包括 n 个整数的数组 nums 和 一个目标值 target。找出 nums 中的三个整数，使得它们的和与 target 最接近。返回这三个数的和。假定每组输入只存在唯一答案。 
# 示例： 
# 输入：nums = [-1,2,1,-4], target = 1
#输出：2
#解释：与 target 最接近的和是 2 (-1 + 2 + 1 = 2) 。
# 提示： 
# 3 <= nums.length <= 10^3 
# -10^3 <= nums[i] <= 10^3 
# -10^4 <= target <= 10^4 
# Related Topics 数组 双指针
```


本题目因为要计算三个数，如果靠暴力枚举的话时间复杂度会到O(n^3)，需要降低时间复杂度
- 首先进行数组排序，时间复杂度O(nlogn)
- 在数组nums中，进行遍历，每遍历一个值利用其下标i，形成一个固定值nums[i]
- 再使用前指针指向`j= i + 1`处，后指针指向`k= nums.length - 1`处，也就是结尾处
- 根据 `sum = nums[i] + nums[start] + nums[end] `的结果，判断sum与目标target的距离，如果更近则更新结果ans
- 同时判断sum与target的大小关系，因为数组有序，如果sum > target 则` k--`，如果sum < target 则 `j++`，如果sum == target 则说明距离为0直接返回结果
- 整个遍历过程，固定值为n次，双指针为n次，时间复杂度为O(n^2)
- 总时间复杂度：$O(nlogn) + O(n^2) = O(n^2)$


```csharp
class Solution:
    def threeSumClosest(self, nums: List[int], target: int) -> int:
        if not nums: return 0
        if len(nums) < 3: return sum(nums)

        ans = float('inf')
        nums.sort()
        for i in range(len(nums)):
            # 优化点 1
            if i > 0 and nums[i] == nums[i-1]: continue
            
            # 新的 t
            t = target - nums[i]
            j, k = i + 1, len(nums) - 1
            while j < k:
                # 优化点 2
                if t == nums[j] + nums[k]: return target

                # 当前 j、k更接近target
                if abs(t - nums[j] - nums[k]) < abs(target - ans):
                    ans = nums[i] + nums[j] + nums[k]
                # 移动j | k
                if t > nums[j] + nums[k]:
                    j += 1
                else:
                    k -= 1
        return ans
```
#  LeetCode 第 27题：移除元素





```csharp
#给你一个数组 nums 和一个值 val，你需要 原地 移除所有数值等于 val 的元素，并返回移除后数组的新长度。
# 不要使用额外的数组空间，你必须仅使用 O(1) 额外空间并 原地 修改输入数组。
# 元素的顺序可以改变。你不需要考虑数组中超出新长度后面的元素。
# 示例 1:
# 给定 nums = [3,2,2,3], val = 3,
#函数应该返回新的长度 2, 并且 nums 中的前两个元素均为 2。
#你不需要考虑数组中超出新长度后面的元素。
# 示例 2:
# 给定 nums = [0,1,2,2,3,0,4,2], val = 2,
#函数应该返回新的长度 5, 并且 nums 中的前五个元素为 0, 1, 3, 0, 4。
#注意这五个元素可为任意顺序。
#你不需要考虑数组中超出新长度后面的元素。
# 说明:
# 为什么返回数值是整数，但输出的答案是数组呢?
# 请注意，输入数组是以「引用」方式传递的，这意味着在函数里修改输入数组对于调用者是可见的。
# 你可以想象内部操作如下:
# // nums 是以“引用”方式传递的。也就是说，不对实参作任何拷贝
#int len = removeElement(nums, val);
#// 在函数里修改输入数组对于调用者是可见的。
#// 根据你的函数返回的长度, 它会打印出数组中 该长度范围内 的所有元素。
#for (int i = 0; i < len; i++) {
#    print(nums[i]);
#}
# 
# Related Topics 数组 双指针
```



首先讲讲自己做题的思路，用Python做比较简单，遍历数组，如果当前值不等于val，就赋值给数组的第i个位置，i+1。



```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        i = 0
        for num in nums:
            if num != val:
                nums[i] = num
                i += 1
        return i
```



官方的解法二就是双指针，在数组需要剔除的元素很少的情况下，上述方法显得有些没必要。比如数组为[1,2,3,5,4],要剔除的数是4时，没必要将前面4个数字遍历一遍。





- i, j 分别指向数组的首尾下标。
- 从 i 开始往后扫描，如果遇到 nums[i] == val 就把它跟 j 交换，j左移一位。直到 i <= j 表示扫描完毕退出



```csharp
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        i, j = 0, len(nums)-1
        while i <= j:
            if nums[i] == val:
                nums[i], nums[j] = nums[j], nums[i]
                j -= 1
            else:
                i += 1
        return i
```

