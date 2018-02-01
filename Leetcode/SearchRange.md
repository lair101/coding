## Search for a Range


### 题目:

Given an array of integers sorted in ascending order, find the starting and ending position of a given target value.

Your algorithm's runtime complexity must be in the order of O(log n).

If the target is not found in the array, return [-1, -1].

### 例子:

```
Given [5, 7, 7, 8, 8, 10] and target value 8,
return [3, 4].
```

### 思路:

题目需要log（N），很自然的想到binary search。 这个题唯一多的一点就是需要在找到目标后，继续找范围。
还是left right 两指针来找到中间。

###代码 （JAVA）：

```
public int[] searchRange(int[] nums, int target) {
        if(nums.length ==0){
            return new int[]{-1,-1};
        }
        //Binary Search
        int left = 0;
        int right = nums.length-1;
        int mid = (right-left)/2+left;
        while(left<right){
            if(nums[mid] == target){
                //find the target
                break;
            }else if(nums[mid] < target){
                left = mid + 1;
                mid = (right-left)/2+left;
            }else if(nums[mid] > target){
                right = mid -1;
                mid = (right-left)/2+left;
            }
        }
        if(nums[mid] == target){
            //looking for the range
            left = mid;
            right =mid;
            while(left>=0 && nums[left]==target){ left --; }
            while(right<=nums.length-1 && nums[right]==target){ right ++; }
            left++;
            right--;
        }else{
            left=-1;
            right=-1;
        }

        return new int[]{left, right};
    }

```
