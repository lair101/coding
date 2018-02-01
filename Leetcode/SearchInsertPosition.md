## Search Insert Position


### 题目:

Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

### 例子:

Example 1:
```
Input: [1,3,5,6], 5
Output: 2
```
Example 2:
```
Input: [1,3,5,6], 2
Output: 1
```
Example 3:
```
Input: [1,3,5,6], 7
Output: 4
```
Example 1:
```
Input: [1,3,5,6], 0
Output: 0
```

### 思路:

没啥说的，标准的binary search。 注意要找插入的数就是 left


### 代码（JAVA）

```
public int searchInsert(int[] nums, int target) {
       //Binary Search and Insert
       int left = 0;
       int right = nums.length -1;
       while(left<=right){
          int mid = (right - left)/2 + left;
           if(nums[mid] == target) return mid;
           else if(nums[mid] > target ) right = mid -1;
           else left = mid +1;
       }
       return left;
   }

   
```
