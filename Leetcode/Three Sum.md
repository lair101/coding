## Three Sum


### 题目:

Given an array S of n integers, are there elements a, b, c in S such that a + b + c = 0? Find all unique triplets in the array which gives the sum of zero.

Note: The solution set must not contain duplicate triplets.


### 例子:


For example, given array ```S = [-1, 0, 1, 2, -1, -4]```,

A solution set is:

```
[
  [-1, 0, 1],
  [-1, -1, 2]
]
```


### 思路:

这道题处看仅仅是比 Two sum 多了一个数字。 但是增加的还有条件，给的数组元素有可能重复，但是答案却不能有重复的数组元素。当多于两个变量在数组中寻找目标答案时。**应该尽可能的去用指针** ，在用指针扫描数组时，为了不取走相同的变量，我们需要把数组先排序。这样在指针扫描时，同样的元素就可以跳过。当然这道题也可以先选取一个变量，令两个转换成Two Sum问题。但是这样的代价有点高，速度比指针慢，而且空间也占用的大。当用两个指针处理已经排好顺序的数组时，一般要从两头向中间，这样就可以根据两个数的差值于目标数之间的关系来调节指针的移动。

想法如下：
```
1. 对目标数组排序
2. 从首元素开始扫描作A指针， 至倒数第三个元素位置
  1. 选A之后的元素为B，倒数第一的元素为C
  2. 开始将B C向中间移动扫描
    1 每次向后滑动，要看B C值是否于之前的值相同，如果相同要跳过
    2 看三个数子的合于目标数的关系， 如果B+C>Target-A,则说明B C 取值过大，则尾部指针需要向前移动以减小。
    3 反之，则移动B 指针以增大
```


### 代码(JAVA):

```
public List<List<Integer>> threeSum(int[] sum){
  List<List<Integer>> res = new ArrayList<List<Integer>>();
// sort the array
Arrays.sort(ns);
// corner case
if (ns.length == 0 || ns.length < 2)
  return res;

for (int a = 0; a < ns.length - 2; a++) {

  // skip duplicated for a pointer
  if (a > 0 && ns[a] == ns[a - 1]) {
    continue;
  }

  int b = a + 1;
  int c = ns.length - 1;
  while (b < c) {
    if (ns[a] + ns[b] + ns[c] == 0) {
      res.add(Arrays.asList(ns[a], ns[b], ns[c]));
      // move b and c same time while skipping the duplicated
      b++;
      c--;
      while (b < c && ns[b] == ns[b - 1])
        b++;
      while (b < c && ns[c] == ns[c + 1])
        c--;
    } else if (ns[a] + ns[b] + ns[c] > 0) {
      // move c
      c--;
      while (b < c && ns[c] == ns[c + 1])
        c--;
    } else {
      // move b
      b++;
      while (b < c && ns[b] == ns[b - 1])
        b++;
    }

  }
}

return res;
}
```

### 时间复杂度:

sorting is nlog(n)

searching two loop n^2

so it is nlog(n)+n^2 => n^2
