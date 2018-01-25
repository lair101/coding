## Two Sum



### 题目:


Given an array of integers, return **indices** of the two numbers such that they add up to a specific target.

You may assume that each input would have **exactly** one solution, and you may not use the same element twice.



### 例子:

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].

```



### 思路:

看到求两个数的和或者差。**一般用到hashmap**。因为查找的时间复杂度为O(1)。 这个题非常简单， 因为不用考虑数组的重复，数组是否有不合理数字，答案是否存在，答案是否唯一。

这个题想法就是：

```
顺序遍历数组，
  对每一个元素 看表中是否已经存在
    如果存在：
      如果 符合查找条件的值 --> 得到结果
      不符合 不予处理
    如果不存在
      将该元素加入表中
```

### 代码(JAVA):


```
class Solution {

    public int[] twoSum(int[] nums, int target) {
        int[] res = new int[2];
        HashMap<Integer, Integer> map = new HashMap<>();
        for(int index=0; index<nums.length;index++){
            if(map.containsKey(target-nums[index])){
                res[0] = map.get(target-nums[index]);
                res[1] = index;
                return res;
            }else{
                map.put(nums[index],index);
            }
        }

        return res; // never reached
    }
}


```


### 时间复杂度:

Worst case scenario 时间复杂度 O(N)

Average case is O(N)+O(1) = O(N)
