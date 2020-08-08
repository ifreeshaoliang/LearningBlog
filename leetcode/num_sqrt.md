## 整数开方
**1. 解法一：二分查找不断逼近**

~~~
void mySqrt_er_fen(){
    if ( num < 0 ) {
        System.out.println("error! This Number is not positive number.");
        return;
    }
    double left = 0, right = num;
    double x = left + (right - left)/2.0;
    double accuracy = 1e-5;//精度
    while (Math.abs(x*x - num) > accuracy) {
        if ( x*x > num)
            right = x;
        else
            left = x;
        x = left + (right - left)/2.0;
    }
}
~~~

**2. 解法二：牛顿迭代法**

![image](https://github.com/ifreeshaoliang/LearningBlog/blob/master/imges/lcode1.png)

>设f(x)=x^2 - a，其中a是我们要开方的数。画出上图的抛物线，然后随机取一个点(x0，f(x0))，以这个点做切线，交x轴与x1。以同样的方法以点(x1，f(x1))处做切线，不断做切线逼近零点。最后就可以求得一个近似的结果了。

取(x0，f(x0))，切线为：$y - f(x_0) = f`(x_0)(x - x_0)$；

令y=0，就可以求得x1了。$0 - f(x_0) = f`(x_0)(x - x_0)$，

得 $x_1 = x_0 - \frac{f(x_0)}{f`(x_0)}$

不断迭代求下去有 
$$x_{n+1} = x_n - \frac{f(x_n)}{f`(x_n)}$$

~~~
//牛顿迭代法
void mySqrt_niu_dun(){
    if ( num < 0 ) {
        System.out.println("error! This Number is not positive number.");
        return;
    }
    double x = 1; //选取的初始点(不能为0)，不断做切线接近零点
    double accuracy = 1e-5;//精度
    while ( Math.abs(num - x * x) > accuracy ) {
        x = ( x + (num / x) ) / 2;
    }
}
~~~

**ps:这两个方法适用于开三次方、四次方等等**
