(数组嵌套)[https://leetcode.cn/problems/array-nesting/]

索引从0开始长度为N的数组A，包含0到N - 1的所有整数。找到最大的集合S并返回其大小，
其中 S[i] = {A[i], A[A[i]], A[A[A[i]]], ... }且遵守以下的规则。

假设选择索引为i的元素A[i]为S的第一个元素，S的下一个元素应该是A[A[i]]，
之后是A[A[A[i]]]... 以此类推，不断添加直到S出现重复的元素。

```java
class Solution {
    public int arrayNesting(int[] nums) {
        int ans = 0, n = nums.length;
        // 记录是否经过该点
        boolean[] via = new boolean[n];
        for (int i = 0; i < n; ++i) {
            int cnt = 0;
            // 对于每一组都形成一个环
            // 各个环都不相交叉
            // 从环中任意一点进入环，都会遍历全环
            while (!via[i]) {
                cnt++;
                via[i] = true;
                i = nums[i]; 
            }
            ans = Math.max(ans, cnt);
        }
        return ans;
    }
}
```
