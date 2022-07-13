[行星碰撞](https://leetcode.cn/problems/asteroid-collision/)

给定一个整数数组 asteroids，表示在同一行的行星。
对于数组中的每一个元素，其绝对值表示行星的大小，正负表示行星的移动方向（正表示向右移动，负表示向左移动）。
每一颗行星以相同的速度移动。
找出碰撞后剩下的所有行星。碰撞规则：两个行星相互碰撞，较小的行星会爆炸。
如果两颗行星大小相同，则两颗行星都会爆炸。两颗移动方向相同的行星，永远不会发生碰撞。

来源：力扣（LeetCode）
```java
class Solution {
    public int[] asteroidCollision(int[] asteroids) {
        // 双端队列peekLast pollLast
        Deque<Integer> d = new ArrayDeque<>();
        for(int t : asteroids){
            boolean ok = true;
            // 栈中行星向右，后面行星向左，两颗行星才会相撞
            while(ok && !d.isEmpty() && d.peekLast()>0 && t<0){
                int a = Math.abs(d.peekLast());
                int b = Math.abs(t);
                if(a<=b)
                    d.pollLast();
                if(a>=b)
                    ok = false;     // ok指示下一颗行星是否存在
            }
            // 行星还存在就添加到栈里面
            if(ok)
                d.addLast(t);
        }
        int sz = d.size();
        int[] ans = new int[sz];
        while(!d.isEmpty()){
            ans[--sz] = d.pollLast();
        }
        return ans;
    }
}
```
