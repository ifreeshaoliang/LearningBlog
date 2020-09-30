## 四因数
给你一个整数数组 nums，请你返回该数组中恰有四个因数的这些整数的各因数之和。

如果数组中不存在满足题意的整数，则返回 0 。
> 输入：nums = [21,4,7]
输出：32

> 解释：
21 有 4 个因数：1, 3, 7, 21；
4 有 3 个因数：1, 2, 4；
7 有 2 个因数：1, 7；
答案仅为 21 的所有因数的和。

~~~
/*
    算法复杂度：n*根号n

    有坑：java整数除法，得到的结果是舍弃小数后的整数

    漏了个边界，比如16，因数1，2，4，8，16。这里应该是有等号的 j * j <= nums[i]。
*/

class Solution {
    public int sumFourDivisors(int[] nums) {
        int res = 0;
        int currentFactorsSum, factors_cnt;
        for (int i = 0; i < nums.length; i++) {
            currentFactorsSum = 0;
            factors_cnt = 0;
            for (int j = 1; j * j <= nums[i]; j++) {
                if (nums[i] % j == 0) {
                    if (j * j == nums[i]) {
                        currentFactorsSum += j;
                        factors_cnt += 1;
                    }
                    else {
                        currentFactorsSum += j + (nums[i] / j);
                        factors_cnt += 2;
                    }
                }
            }
            if (factors_cnt == 4)
                res += currentFactorsSum;
        }
        return res;
    }
}
~~~