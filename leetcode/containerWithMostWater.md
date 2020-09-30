[盛最多水的容器](https://leetcode-cn.com/problems/container-with-most-water/)

给你 n 个非负整数 a1，a2，...，an，每个数代表坐标中的一个点 (i, ai) 。在坐标内画 n 条垂直线，垂直线 i 的两个端点分别为 (i, ai) 和 (i, 0)。找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水。

说明：你不能倾斜容器，且 n 的值至少为 2。

![](https://aliyun-lc-upload.oss-cn-hangzhou.aliyuncs.com/aliyun-lc-upload/uploads/2018/07/25/question_11.jpg)

~~~
/*
    对撞指针，头尾两指针，每次移动就计算一次面积
    最低的是容器的边界，假如左边的是边界，右边的无论如何往左移都是不会比原来大的
*/

class Solution {
    public int maxArea(int[] height) {
        int max = 0;
        int start = 0, end = height.length - 1;
        int width = 0, high = 0;
        while (start != end) {
            width = end - start;
            if (height[start] < height[end]) {
                high = height[start];
                start++;
            }
            else {
                high = height[end];
                end--;
            }
            if ( max < high * width)
                max = high * width;
        }
        return max;
    }
}
~~~