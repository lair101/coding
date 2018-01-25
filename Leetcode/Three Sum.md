## Three Sum


### ��Ŀ:

Given an array S of n integers, are there elements a, b, c in S such that a + b + c = 0? Find all unique triplets in the array which gives the sum of zero.

Note: The solution set must not contain duplicate triplets.


### ����:


For example, given array ```S = [-1, 0, 1, 2, -1, -4]```,

A solution set is:

```
[
  [-1, 0, 1],
  [-1, -1, 2]
]
```


### ˼·:

����⴦�������Ǳ� Two sum ����һ�����֡� �������ӵĻ�����������������Ԫ���п����ظ������Ǵ�ȴ�������ظ�������Ԫ�ء�����������������������Ѱ��Ŀ���ʱ��**Ӧ�þ����ܵ�ȥ��ָ��** ������ָ��ɨ������ʱ��Ϊ�˲�ȡ����ͬ�ı�����������Ҫ������������������ָ��ɨ��ʱ��ͬ����Ԫ�ؾͿ�����������Ȼ�����Ҳ������ѡȡһ��������������ת����Two Sum���⡣���������Ĵ����е�ߣ��ٶȱ�ָ���������ҿռ�Ҳռ�õĴ󡣵�������ָ�봦���Ѿ��ź�˳�������ʱ��һ��Ҫ����ͷ���м䣬�����Ϳ��Ը����������Ĳ�ֵ��Ŀ����֮��Ĺ�ϵ������ָ����ƶ���

�뷨���£�
```
1. ��Ŀ����������
2. ����Ԫ�ؿ�ʼɨ����Aָ�룬 ������������Ԫ��λ��
  1. ѡA֮���Ԫ��ΪB��������һ��Ԫ��ΪC
  2. ��ʼ��B C���м��ƶ�ɨ��
    1 ÿ����󻬶���Ҫ��B Cֵ�Ƿ���֮ǰ��ֵ��ͬ�������ͬҪ����
    2 ���������ӵĺ���Ŀ�����Ĺ�ϵ�� ���B+C>Target-A,��˵��B C ȡֵ������β��ָ����Ҫ��ǰ�ƶ��Լ�С��
    3 ��֮�����ƶ�B ָ��������
```


### ����(JAVA):

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

### ʱ�临�Ӷ�:

sorting is nlog(n)

searching two loop n^2

so it is nlog(n)+n^2 => n^2
