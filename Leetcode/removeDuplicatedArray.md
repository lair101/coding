## Remove Duplicates from Sorted Array


### 题目:

Given a sorted array, remove the duplicates in-place such that each element appear only once and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

### 例子:

```
Given nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.
It doesn't matter what you leave beyond the new length.

```

### 思路:

题目非常简单，就是去重。主要是要在O（1）的memory下完成。这样很多简单的办法就不行了。
比如全部放进HashSet，然后直接返回HashSet的大小
由于只有一个额外空间，很自然的我们想到了指针。

1. 首先将数组排序
2. 用一个指针开始扫描，遇到重复的跳过。用一个计数器来记录遇到的新数

### 代码(JAVA)

```
public int removeDuplicates(int[] nums) {
       Arrays.sort(nums);
       int p =0;

       for(int i=0;i<nums.length;i++){
           if(i>0&&nums[i]==nums[i-1]){
               continue;
           }else{
               p++;
           }

       }

       return p;
   }

```
