## Container with most water


### 题目:

Given n non-negative integers a1, a2, ..., an, where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

Note: You may not slant the container and n is at least 2.


### 思路:

这是一个非常明显的双指针问题。


```
|                             |         |                 
|              |              |         |                    
|    |         |              |    |    |                    
|    |    |    |    |         |    |    |                     
|    |    |    |    |         |    |    |              |       
|    |    |    |    |    |    |    |    |              |       
|    |    |    |    |    |    |    |    |              |    |   
|    |    |    |    |    |    |    |    |    |         |    |   
|    |    |    |    |    |    |    |    |    |    |    |    |   
left                                                       right
```

如果这道题是求面积，则应为梯形的面积是 （上底+下底）X 高 /2 。

**但是注意到这道题要求的是成最多的水，这也就是按最低的竖线算的长方形**

我们就先把高设为最大，既整个数组的长度。然后让两个左右指针向中间移动。每次移动求取面积。为了能有更大的面积值。只能是左右的指针挪动到别之前所有都大的竖线才有可能得到更大的长方形面积

那么
  1. 初始化一个面积值
  2. 左指针向右移动至 比左边的最大值大的项， 计算面积，如果大怎更新
  3. 同理右指针

###代码 （JAVA）

```
public int maxArea(int[] height) {
       int left = 0, right = height.length - 1;
   int res = Math.min(height[left],height[right])*(right - left);

   while (left < right) {
     int tmpArea = Math.min(height[left],height[right])*(right - left);
     res = Math.max(res, tmpArea);
     if (height[left] < height[right])
       left++;
     else
       right--;
   }

   return res;
   }
}

```
### 时间复杂度:

时间复杂度为 O(N)
