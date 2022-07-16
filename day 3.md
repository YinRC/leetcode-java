[滑动窗口的平均值](https://leetcode.cn/problems/qIsx9U/)

给定一个整数数据流和一个窗口大小，根据该滑动窗口的大小，计算滑动窗口里所有数字的平均值。

实现 MovingAverage 类：

MovingAverage(int size) 用窗口大小 size 初始化对象。
double next(int val) 成员函数 next 每次调用的时候都会往滑动窗口增加一个整数，
请计算并返回数据流中最后 size 个值的移动平均值，即滑动窗口里所有数字的平均值。

来源：力扣（LeetCode）

```java
class MovingAverage {

    /** Initialize your data structure here. */
    int[] arr = new int[10010];
    int n, sum, i, j;
    public MovingAverage(int size) {
        n = size;
    }
    
    // 双端队列
    public double next(int val) {
        sum += arr[i++] = val;
        if(i-j>n)
            sum -= arr[j++];
        return sum*1.0/(i-j);
    }
}

/**
 * Your MovingAverage object will be instantiated and called as such:
 * MovingAverage obj = new MovingAverage(size);
 * double param_1 = obj.next(val);
 */
```
