## Two Sum



### **题目：**

Given an array of integers, return **indices** of the two numbers such that they add up to a specific target.

You may assume that each input would have **exactly** one solution, and you may not use the same element twice.



### 例子：

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].

```



### 思路：



### 代码：



public class Solution {

    public int\[\] twoSum\(int\[\] nums, int target\) {

        HashMap&lt;Integer, Integer&gt; map = new HashMap&lt;&gt;\(\);

        int\[\] res = new int\[2\];

        for\(int i=0; i &lt;  nums.length; i++\){

            if\(map.containsKey\(target-nums\[i\]\)\){

                //there is result

                res\[0\]=map.get\(target-nums\[i\]\);

                res\[1\]=i;

            }

            else{

                map.put\(nums\[i\],i\);

            }

        }

        return res;

    }

}



