# Algorithm

## 1. 数组

### 1.1 二分查找

#### 经典二分查找

[力扣题目链接](https://leetcode.cn/problems/binary-search/)

​		给定一个 n 个元素有序的（升序）整型数组 nums 和一个目标值 target  ，写一个函数搜索 nums 中的 target，如果目标值存在返回下标，否则返回 -1。

示例 1:        

```
输入: nums = [-1,0,3,5,9,12], target = 9     
输出: 4       
解释: 9 出现在 nums 中并且下标为 4     
```

示例 2:    

```
输入: nums = [-2,0,3,5,9,12], target = -1     
输出: -1        
解释: 2 不存在 nums 中因此返回 -1        
```

提示：    

* 你可以假设 nums 中的所有元素是不重复的。
* n 将在 [1, 10000]之间。
* nums 的每个元素都将在 [-9999, 9999]之间。

思路：数组第一个元素的下标设为left，最后一个元素的下标设为right，取`mid = (right - left) / 2 + left;`   mid为left与right中间的那个元素（如果元素个数为偶数个，那么mid为中间的左边那个元素），如果mid＞target，那么[mid,right]都不用看了，更新right为mid左边的那个元素，如果mid小于target，那么[left,mid]都不用看了，更新left为mid右边的那个元素。

```c++
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int left = 0, right = nums.size() - 1;
        while(left <= right){
            int mid = (right - left) / 2 + left;
            int num = nums[mid];
            if (num == target) {
                return mid;
            } else if (num > target) {
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        }
        return -1;
    }
};
```

* 时间复杂度：O(log n)
* 空间复杂度：O(1)



#### 搜索插入位置

[力扣题目链接](https://leetcode.cn/problems/search-insert-position/)

​		给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。

你可以假设数组中无重复元素。

```c++
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        int left = 0, right = nums.size()-1;
		while (left <= right) {
			int mid = (right - left) / 2 + left;
			int num = nums[mid];
			if (num == target)
				return mid;
			if (num > target)
				right = mid - 1;
			else
				left = mid + 1;
		}
        return left;
    }
};
```



#### 在排序数组中查找元素的第一个和最后一个位置

[力扣题目链接](https://leetcode.cn/problems/find-first-and-last-position-of-element-in-sorted-array/description/)

![image-20231111201040110](Algorithm.assets/image-20231111201040110.png)

```c++
class Solution {
public:
	vector<int> searchRange(vector<int>& nums, int target) {
		int left = 0, right = nums.size() - 1;
		int mid = 0;
		while (left <= right) {
			mid = (right - left) / 2 + left;
			int num = nums[mid];
			if (num == target) {
				int leftRange = mid;
				int rightRange = mid;
				while (leftRange > 0 && nums[leftRange - 1] == nums[mid])
					leftRange--;
				while (rightRange < nums.size() - 1 && nums[rightRange + 1] == nums[mid])
					rightRange++;
				return { leftRange, rightRange };
			}
			if (num > target)
				right = mid - 1;
			else
				left = mid + 1;
		}
		return { -1,-1 };
	}
};
```

> 注意内层while不要越界



#### x的平方根

[69.x 的平方根](https://leetcode.cn/problems/sqrtx/)

给你一个非负整数 `x` ，计算并返回 `x` 的 **算术平方根** 。

由于返回类型是整数，结果只保留 **整数部分** ，小数部分将被 **舍去 。**

**注意：**不允许使用任何内置指数函数和算符，例如 `pow(x, 0.5)` 或者 `x ** 0.5` 。

**示例 1：**

```
输入：x = 4
输出：2
```

**示例 2：**

```
输入：x = 8
输出：2
解释：8 的算术平方根是 2.82842..., 由于返回类型是整数，小数部分将被舍去。
```

**提示：**

- `0 <= x <= 231 - 1`

​	

​	本题的关键在于二分搜索范围的确定。

- 如果a*a>x，那么a一定不是x的平方根
- 如果a*a<x，那么a可能是x的平方根

​		所以，在更新搜索范围时，如果mid * mid的值小于x，那么left更新为mid而不是mid+1，因为mid有可能是x的平方根，要把mid也考虑进去；如果mid * mid的值大于x，那么right更新为mid-1，因为这个mid肯定不是x的平方根。

​		其次，起始搜索范围的确定，起始搜索范围可以设定为0到x/2，或1到x/2。x/2右边的肯定不是的

>  (x/2+1)^2=(x/2)^2+x+1>x

​		再其次，特殊值的处理：0与1要特殊处理

​		再其次，while循环结束时会得到一个长度为1的区间，区间的左右均可能为要得的答案，所以要判断区间的左边为解还是右边为解。

​		最后，防止溢出mid*mid与x比较大小由 if (mid *  mid > x)改为if(mid>x/mid)

```c++
class Solution {
public:
    int mySqrt(int x) {
        if (x == 0)return 0;
        if (x == 1)return 1;
        int left = 0;
        int right = x/2;
        int mid = 0;
        while (left+1<right) {
            int mid = (left + right) / 2;
            if (mid > x/mid)
                right = mid - 1;
            else if (mid <= x/mid)
                left = mid;
        }
        if (right  <= x/right)return right;
        else return left;
    }
};
```



#### 有效的完全平方数

[367.有效的完全平方数](https://leetcode.cn/problems/valid-perfect-square/)

​		给你一个正整数 `num` 。如果 `num` 是一个完全平方数，则返回 `true` ，否则返回 `false` 。

​		**完全平方数** 是一个可以写成某个整数的平方的整数。换句话说，它可以写成某个整数和自身的乘积。

不能使用任何内置的库函数，如 `sqrt` 。

 

**示例 1：**

```
输入：num = 16
输出：true
解释：返回 true ，因为 4 * 4 = 16 且 4 是一个整数。
```

**示例 2：**

```
输入：num = 14
输出：false
解释：返回 false ，因为 3.742 * 3.742 = 14 但 3.742 不是一个整数。
```

 

**提示：**

- 1 <= num <= 2^31^ - 1



题解：

```c++
class Solution {
public:
    bool isPerfectSquare(int num) {
        if (num == 1 || num == 4)return 1;
        else if (num == 2 || num == 3)return 0;
        else {
            //初始范围是1到这个数的一半
            long long int left = 1;
            long long int right = num / 2;
            long long int mid = (left + right) / 2;
            //为防止溢出，可以这样写
            // int middle = left + ((right - left) / 2);// 防止溢出 等同于(left + right)/2
            while (left <= right) {
                mid = (left + right) / 2;
                if (mid * mid == num)return 1;
                else if (mid * mid < num)left = mid + 1;
                else if (mid * mid > num)right = mid - 1;
            }
        }
        return 0;
    }
};
```





### 1.2 移除元素

#### 移除元素

[27 移除元素](https://leetcode.cn/problems/remove-element/)

给你一个数组 `nums` 和一个值 `val`，你需要 **[原地](https://baike.baidu.com/item/原地算法)** 移除所有数值等于 `val` 的元素，并返回移除后数组的新长度。

不要使用额外的数组空间，你必须仅使用 `O(1)` 额外空间并 **[原地 ](https://baike.baidu.com/item/原地算法)修改输入数组**。

元素的顺序可以改变。你不需要考虑数组中超出新长度后面的元素。

**说明:**

为什么返回数值是整数，但输出的答案是数组呢?

请注意，输入数组是以**「引用」**方式传递的，这意味着在函数里修改输入数组对于调用者是可见的。

你可以想象内部操作如下:

```
// nums 是以“引用”方式传递的。也就是说，不对实参作任何拷贝
int len = removeElement(nums, val);

// 在函数里修改输入数组对于调用者是可见的。
// 根据你的函数返回的长度, 它会打印出数组中 该长度范围内 的所有元素。
for (int i = 0; i < len; i++) {
    print(nums[i]);
}
```

**示例 1：**

```
输入：nums = [3,2,2,3], val = 3
输出：2, nums = [2,2]
解释：函数应该返回新的长度 2, 并且 nums 中的前两个元素均为 2。你不需要考虑数组中超出新长度后面的元素。例如，函数返回的新长度为 2 ，而 nums = [2,2,3,3] 或 nums = [2,2,0,0]，也会被视作正确答案。
```

**示例 2：**

```
输入：nums = [0,1,2,2,3,0,4,2], val = 2
输出：5, nums = [0,1,3,0,4]
解释：函数应该返回新的长度 5, 并且 nums 中的前五个元素为 0, 1, 3, 0, 4。注意这五个元素可为任意顺序。你不需要考虑数组中超出新长度后面的元素。
```

**提示：**

- `0 <= nums.length <= 100`
- `0 <= nums[i] <= 50`
- `0 <= val <= 100`

题解：

- 暴力解法

```cpp
// 时间复杂度：O(n^2)
// 空间复杂度：O(1)
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int size = nums.size();
        for (int i = 0; i < size; i++) {
            if (nums[i] == val) { // 发现需要移除的元素，就将数组集体向前移动一位
                for (int j = i + 1; j < size; j++) {
                    nums[j - 1] = nums[j];
                }
                i--; // 因为下标i以后的数值都向前移动了一位，所以i也向前移动一位，从而在下一个for循环的时候可以检查i位置上的元素
                size--; // 更新size，此时数组的大小-1
            }
        }
        return size;
    }
};
```

- 双指针法

[代码随想录 (programmercarl.com)](https://www.programmercarl.com/0027.移除元素.html#思路)

```cpp
// 时间复杂度：O(n)
// 空间复杂度：O(1)
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int slowIndex = 0;
        for (int fastIndex = 0; fastIndex < nums.size(); fastIndex++) {
            if (val != nums[fastIndex]) {
                nums[slowIndex] = nums[fastIndex];
                slowIndex++;
            }
        }
        return slowIndex;
    }
};
```

> 快指针fast用于**寻找新数组的元素**，慢指针用于**更新新数组，给新数组赋值**。
>
> 快指针找到新数组需要的元素后，就把它赋值给慢指针，然后快慢指针都++
>
> 当快指针指向的元素不是新数组的元素，快指针++，去寻找下一个元素，慢指针不动。



#### 删除有序数组中的重复项

[26.删除排序数组中的重复项](https://leetcode.cn/problems/remove-duplicates-from-sorted-array/)

给你一个 **非严格递增排列** 的数组 `nums` ，请你**[ 原地](http://baike.baidu.com/item/原地算法)** 删除重复出现的元素，使每个元素 **只出现一次** ，返回删除后数组的新长度。元素的 **相对顺序** 应该保持 **一致** 。然后返回 `nums` 中唯一元素的个数。

考虑 `nums` 的唯一元素的数量为 `k` ，你需要做以下事情确保你的题解可以被通过：

- 更改数组 `nums` ，使 `nums` 的前 `k` 个元素包含唯一元素，并按照它们最初在 `nums` 中出现的顺序排列。`nums` 的其余元素与 `nums` 的大小不重要。
- 返回 `k` 。

**判题标准:**

系统会用下面的代码来测试你的题解:

```
int[] nums = [...]; // 输入数组
int[] expectedNums = [...]; // 长度正确的期望答案

int k = removeDuplicates(nums); // 调用

assert k == expectedNums.length;
for (int i = 0; i < k; i++) {
    assert nums[i] == expectedNums[i];
}
```

如果所有断言都通过，那么您的题解将被 **通过**。

**示例 1：**

```
输入：nums = [1,1,2]
输出：2, nums = [1,2,_]
解释：函数应该返回新的长度 2 ，并且原数组 nums 的前两个元素被修改为 1, 2 。不需要考虑数组中超出新长度后面的元素。
```

**示例 2：**

```
输入：nums = [0,0,1,1,1,2,2,3,3,4]
输出：5, nums = [0,1,2,3,4]
解释：函数应该返回新的长度 5 ， 并且原数组 nums 的前五个元素被修改为 0, 1, 2, 3, 4 。不需要考虑数组中超出新长度后面的元素。
```

**提示：**

- `1 <= nums.length <= 3 * 104`
- `-104 <= nums[i] <= 104`
- `nums` 已按 **非严格递增** 排列

题解：

```c++
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if (nums.size() == 0) {
            return 0;
        }
        //定义快慢指针
        int slowIndex = 0;     
        for(int fastIndex=1;fastIndex<nums.size();){
            if(nums[slowIndex]!=nums[fastIndex]){
                nums[slowIndex+1]=nums[fastIndex];
                slowIndex++;
                fastIndex++;
            }
            else fastIndex++;
        }       
        return slowIndex+1;
    }
};
```

算法核心：

首先注意数组是有序的，那么重复的元素一定会相邻。

要求删除重复元素，实际上就是将不重复的元素移到数组的左侧。

考虑用 2 个指针，一个在前记作 fast，一个在后记作 slow，算法流程如下：

比较 p 和 q 位置的元素是否相等：

- 如果相等，q 后移 1 位

- 如果不相等，将 q 位置的元素复制到 p+1 位置上，p 后移一位，q 后移 1 位
- 重复上述过程，直到 q 等于数组长度。

​	返回 p + 1，即为新数组长度。

> `nums.size()==0`时做特殊处理



































































