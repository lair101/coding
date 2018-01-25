## 3Sum Closet


### 题目:

Given an array S of n integers, find three integers in S such that the sum is closest to a given number, target. Return the sum of the three integers. You may assume that each input would have exactly one solution.


### 例子:

For example, given array S = {-1 2 1 -4}, and target = 1.

The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).

### 思路:

这道题和3Sum非常相似，也用 双指针扫描加一个首元素 的形式处理。不同的是多加了一步。之前是要相等。这就意思是三个数加起来和目标数的差值是0.现在是要去的这个差值最小的。同样的方法扫描只是多一步不断更新一个最小值。这段题如果是要返回组合，那就还要记录组合。


想法如下：
```
1. 对目标数组排序
2. 从首元素开始扫描作A指针， 至倒数第二个元素位置（因为可以重复出现）
  1. 选A之后的元素为B，倒数第一的元素为C
  2. 开始将B C向中间移动扫描
    1 每次向后滑动，要计算出差值，如果比现最小值小则更新。
    2 如果有相等关系，则肯定是最小则，直接返回。
    3 看三个数子的合于目标数的关系， 如果B+C>Target-A,则说明B C 取值过大，则尾部指针需要向前移动以减小。
      这里每次挪动完成之后，需要去指针的前一个指向值。因为前一个指向值才是符合条件的
    4 反之，则移动B 指针以增大
```


### 代码(JAVA):

```
 public int threeSumClosest(int[] ns, int target) {
		// sort the array
		Arrays.sort(ns);
		// corner case
		if (ns.length == 0 || ns.length < 2)
			return 0;
        int res = ns[0]+ns[1]+ns[2];
		for (int a = 0; a < ns.length - 1; a++) {
			int b = a + 1;
			int c = ns.length - 1;
			while (b < c) {
				if (ns[a] + ns[b] + ns[c] == target) {
                    return target;
				} else if (ns[a] + ns[b] + ns[c] > target) {
					while (b < c && ns[a] + ns[b] + ns[c] > target)
					c--;
                    if(Math.abs(ns[a]+ns[b]+ns[c+1]-target)<Math.abs(res-target))
                    res=ns[a]+ns[b]+ns[c+1];
				} else {
					while (b < c &&  ns[a] + ns[b] + ns[c] < target)
					b++;
                    if(Math.abs(ns[a]+ns[b-1]+ns[c]-target)<Math.abs(res-target))
                    res=ns[a]+ns[b-1]+ns[c];
				}
			}
		}
		return res;
    }
    ```
