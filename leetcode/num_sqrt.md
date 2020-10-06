## 整数开方
**1. 解法一：二分查找不断逼近**

~~~
//java
static double mySqrt_er_fen(int num){
   if ( num < 0 ) {
        System.out.println("error! This Number is not positive number.");
        return -1;
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
    return x;
}
~~~

**2. 解法二：牛顿迭代法**

![函数图像](https://raw.githubusercontent.com/ifreeshaoliang/LearningBlog/master/imges/lcode1.png)

设
<img src="https://latex.codecogs.com/gif.latex?\inline&space;f(x)=x^2&space;-&space;a" title="f(x)=x^2 - a" />
，其中a是我们要开方的数。画出上图的抛物线，然后随机取一个点(x0，f(x0))，以这个点做切线，交x轴于x1。以同样的方法以点(x1，f(x1))处做切线，不断做切线逼近零点。最后就可以求得一个近似的结果了。

>取 
<img src="https://latex.codecogs.com/gif.latex?\inline&space;(x_0,f(x_0))" title="(x_0,f(x_0))" />
，切线为：
<img src="https://latex.codecogs.com/gif.latex?y&space;-&space;f(x_0)&space;=&space;f{}'(x_0)(x&space;-&space;x_0)" title="y - f(x_0) = f{}'(x_0)(x - x_0)" />；

>令 y = 0，就可以求得 
<img src="https://latex.codecogs.com/gif.latex?\inline&space;x_1" title="x_1" /> 
了：
<img src="https://latex.codecogs.com/gif.latex?0&space;-&space;f(x_0)&space;=&space;f{}'(x_0)(x&space;-&space;x_0)" title="0 - f(x_0) = f{}'(x_0)(x - x_0)" />，

>得 ：
<img src="https://latex.codecogs.com/gif.latex?\inline&space;x_1&space;=&space;x_0&space;-&space;\frac{f(x_0)}{f`(x_0)}" title="x_1 = x_0 - \frac{f(x_0)}{f`(x_0)}" />

>然后继续求
<img src="https://latex.codecogs.com/gif.latex?\inline&space;x_2,&space;x_3,&space;x_4...x_n" title="x_2, x_3, x_4...x_n" />
一直不断逼近上图函数零点，即让f(x)=x^2 - a = 0 的 x 值，便可以求得a的开平方了。

>不断迭代求下去有
<img src="https://latex.codecogs.com/gif.latex?\inline&space;x_{n&plus;1}&space;=&space;x_n&space;-&space;\frac{f(x_n)}{f{}'(x_n)}" title="x_{n+1} = x_n - \frac{f(x_n)}{f{}'(x_n)}" />

**这
<img src="https://latex.codecogs.com/gif.latex?\inline&space;x_{n&plus;1}&space;=&space;x_n&space;-&space;\frac{f(x_n)}{f{}'(x_n)}" title="x_{n+1} = x_n - \frac{f(x_n)}{f{}'(x_n)}" />
便是牛顿迭代法的计算通式。**

现在我们要求一个数的平方，那么函数为：<img src="https://latex.codecogs.com/gif.latex?\inline&space;f(x)=x^2&space;-&space;a" title="f(x)=x^2 - a" />
，套入通式，得到
<img src="https://latex.codecogs.com/gif.latex?\inline&space;x_{n&plus;1}&space;=&space;x_n&space;-&space;\frac{x^2&space;-&space;a}{2x}" title="x_{n+1} = x_n - \frac{x^2 - a}{2x}" />

即
<img src="https://latex.codecogs.com/gif.latex?\inline&space;x_{n&plus;1}&space;=&space;x_n&space;-&space;(x&space;-&space;\frac{a}{x})/2" title="x_{n+1} = x_n - (x - \frac{a}{x})/2" />

这个公式在代码中的体现为：x = ( x + (num / x) ) / 2;

~~~
//java
//牛顿迭代法
static double mySqrt_niu_dun(int num){
    if ( num < 0 ) {
        System.out.println("error! This Number is not positive number.");
        return -1;
    }
    double x = 1; //选取的初始点(不能为0)，不断做切线接近零点
    double accuracy = 1e-5;//精度
    while ( Math.abs(num - x * x) > accuracy ) {
        x = ( x + (num / x) ) / 2;
    }
    return x;
}
~~~

**ps:这两个方法适用于开三次方、四次方等等**
