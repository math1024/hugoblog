# Matrix


#### 一起回忆下线性代数
* 斐波那契数列
* 矩阵主要概念


#### 从斐波那契数列开始
* 通项公式
  * F(1)=1，F(2)=1, F(n)=F(n-1)+F(n-2) n>=2，n∈N*
  
* 输出求数列前100项


```python
def fibonacc(n):
    if (n < 2):
        return n
    else:
        return(fibonacc(n-1) + fibonacc(n-2))

fibonacc(4)
```


```python
 def fibonacc(n):
    if (n < 2):
        return n
    else:
        return(fabionacc(n-1) + fabionacc(n-2))
    
def fibonacc_sum(number):
    for i in range(number):
        print(fibonacc(i), end=' ')
        if (i+1) % 10 == 0:
            print("\n") 
            
start = time.time()
fibonacc_sum(30)
end = time.time()
print('time cost',(end - start),'s')
```


```python
import time

def fibonacc_sum(n):
    list =[]
    for i in range(n):
        if i==0 or i==1:#第1,2项 都为1
            list.append(1)
        else:
            list.append(list[i-2]+list[i-1])#从第3项开始每项值为前两项值之和
    
    # 格式化输出
    for i in range(len(list)):
        print(list[i], end=' ')
        if (i+1) % 10 == 0:
            print("\n") 
            
start = time.time()
fibonacc_sum(100)
end = time.time()
print('time cost',(end - start),'s')
```

* **思考题** 上面的代码如果改写java需要注意什么？


```python
def fibonaccByMatrix():
    
    return 
```

* 构造矩阵解决问题
$$
F_0 = 0,\\
F_1 = 1,\\
F_{n+1} = F_{n} + F_{n-1}\\
F_{3} + F_{2} = F_{2} + F_{1} + F_{2}
$$

<br>
$$ \left[ \begin{array}{cccc}
F_3\\
F_2\\
\end{array} \right] =  \left[ \begin{array}{cccc}
1&1\\
1&0\\
\end{array} \right] \left[ \begin{array}{cccc}
F_{2}\\
F_{1}\\
\end{array} \right]$$

<br>
$$ \left[ \begin{array}{cccc}
F_4\\
F_3\\
\end{array} \right] =  \left[ \begin{array}{cccc}
1&1\\
1&0\\
\end{array} \right] \left[ \begin{array}{cccc}
F_{3}\\
F_{2}\\
\end{array} \right]  = \left[ \begin{array}{cccc}
1&1\\
1&0\\
\end{array} \right] ^2\left[ \begin{array}{cccc}
F_{2}\\
F_{1}\\
\end{array} \right] $$  

<br>
$$ \left[ \begin{array}{cccc}
F_{n+1}\\
F_n\\
\end{array} \right] =  \left[ \begin{array}{cccc}
1&1\\
1&0\\
\end{array} \right] \left[ \begin{array}{cccc}
F_{n}\\
F_{n-1}\\
\end{array} \right]$$

<br>
$$ \left[ \begin{array}{cccc}
F_{n+1}\\
F_n\\
\end{array} \right] =  \left[ \begin{array}{cccc}
1&1\\
1&0\\
\end{array} \right]^n \left[ \begin{array}{cccc}
F_{1}\\
F_{0}\\
\end{array} \right]$$    
<br>

```python
import numpy
import time

def fibonacci_tool(n):
    Matrix = numpy.matrix("1 1;1 0")
    # 返回是matrix类型
    return pow(Matrix, n)

def fibonaccByMatrix(n):
    result_list = []
    for i in range(0, n):
        result_list.append(numpy.array(fibonacci_tool(i))[0][0])
    return result_list

start = time.time()
list = fibonaccByMatrix(100)
end = time.time()
print('time cost',(end - start),'s')
```



#### 0 正确的顺序


name | 字面意思 |  实际意思
---|---|---
向量 | 排成一列或一行的数字 | 有方向的线段、空间内点 |
矩阵 | 排成方形、长方形的数字 | 空间到空间的映射|
行列式 | 麻烦的计算 | 体积的变化率 |

----



#### 1 向量、线性空间
* 向量
  * 当我们需要把几个数值放一起作为一个整体处理，就有了向量
  * 把数排成一列
  $$ \vec x =  \left( 3, 5, 7, 8 \right)^T $$

* 线性空间
  * 向量加减法, 向量与标量数乘, 
  * 满足交换律，结合律和分配律等
  * **不问答是什么，先看有什么性质** 
* 基底
  * 基是线性空间里的一组向量，使得任何一个向量都可以唯一的表示成这组基的线性组合
  * 线性代数的基本问题就是基组的选择问题
  
* 向量范数
  * 向量范数是具有“长度”概念的函数, 是向量空间到实数的映射
  * lp范数 $$ ||x||_p = (\sum_{i=1}^n (|x_i|)^p)^ \frac{1}{p}$$
  * 常见的向量范数
  
      * L0 范数:向量中非零元素的个数
      * L1 范数:向量元素绝对值之和
      * L2 范数:欧几里德距离 or 欧几里德范数(通常说的距离或者模)
      * L∞ 范数:所有向量元素绝对值中的最大值
      * L−∞ 范数:所有向量元素绝对值中的最小值
  

#### 2 矩阵
* 描述定义
    * 把数列排成长方形，为了描述矩阵的规模 行数\*列数， 如果行数=列数就是方阵
    * 由此加法、数乘运算、范数一些运算
* 线性空间的映射
    * 线性映射 V 和 W 是两个实线性空间，T : V → W 满足如下条件 
        * T(v1 + v2) = T(v1) + T(v2) ∀v1,v2 ∈ V 
        * T(cv)=cT(v) ∀c∈R, v∈V 

<br>
$$        
x = \begin{cases}
   a &\text{if } b \\
   c &\text{if } d
\end{cases}
$$
<br>
$$
\begin {cases} 
  x_1 + 2x_2 - x_3 = 2\\
  -5x_2 + 3x_3 = 1\\
\end{cases}
$$
<br>
$$ \left[ \begin{array}{cccc}
1&2&-1\\
0&-5&3\\
\end{array} \right] * \left[ \begin{array}{cccc}
x_1\\
x_2\\
x_3\\
\end{array} \right]  = \left[ \begin{array}{cccc}
4\\
1\\
\end{array} \right] $$ 
<br>

​		    **请把矩阵理解成函数f(x)**	

* 方阵的行列式值
    * $$ det(A) = \sum_{j=1}^n(-1)^{i+j}* a_{ij} * det(A_{ij}) $$
* 矩阵逆
    * ∀A ∈ Rn,n 为非奇异方阵 $$ det(A) = 0 $$ 
      矩阵的逆定义为存在并唯一的 n×n 矩阵满足 
    * $$ AA^{-1} = A^{-1}A = I_n $$
    * $$ (AB)^{-1} = B^{-1}A^{-1} $$
* 特征向量
    * λ∈C为方阵A∈Rn,n 的特征值，满足∃u∈Cn,u̸=0,并且 Au = λu，或者 (λI − A)u = 0, <br>
      u 为对应的特征向量。 <br>
      特征值为矩阵 A 的特征多项式的根 p(λ) = det(λI − A) = 0
    *  $$ A \vec p =  \lambda\vec p $$   $$ \lambda就是特征值、\vec p就是特征向量 $$
    * 特征向量乘以A后，只有长度会有变化，方向不会有变化，而长度变化的倍率就是特征值
    * 在变化的基底中寻找不变的东西
* 矩阵的秩
    * 矩阵的秩等于其非零特征值的个数
* 矩阵范数
    * L0范数：矩阵的非0元素的个数，通常用它来表示稀疏，L0范数越小0元素越多，也就越稀疏
    * L1范数：矩阵中的每个元素绝对值之和，它是L0范数的最优凸近似，因此它也可以表示稀疏
    * 矩阵的F范数：矩阵的各个元素平方之和再开平方根，它通常也叫做矩阵的L2范数，它的优点在于它是一个凸函数，可以求导求解
    

#### 网页排名


#### 3. 后面还有什么
* 相似变换
    * 设A,B都是n阶矩阵，若存在可逆矩阵P，使$$ B=P^{-1}AP $$
      则称B是A的相似矩阵, 并称矩阵A与B相似，记为A~B。
      对进行运算称为对进行相似变换，称可逆矩阵为相似变换矩阵
        * 两者的秩相等；
          两者的行列式值相等；
          两者的迹数相等；
          两者拥有同样的特征值，尽管相应的特征向量一般不同；
* 相合变换
    * 对两个n阶实矩阵A和B，若存在一个可逆实方阵P，
      使$$ B=P^TAP $$
      则称B和A为实相合的
* PCA、SVD分解
    * （Principal components analysis PCA）降维
    * （Singular Value Decomposition SVD） 非方阵也可以
* 协方差矩阵 
    * 协方差:用来度量两个随机变量关系的统计量
    * 多个协方差组成的矩阵

$$
\sum_{n=1}^{\infty} 2^{-n} = 1
$$


#### 参考资料


 1. 程序员的数学3 - 线性代数
 2. [陶哲轩的讲义](http://www.math.ucla.edu/~tao/resource/general/115a.3.02f/)
 3. 线性代数及其应用, 莱 (Lay D.C.) (作者), 刘深泉 (译者) 
 4. 线性代数，李炯生、查建国
 5. [数学基础QA,from github](https://github.com/scutan90/DeepLearning-500-questions/blob/master/ch01_数学基础/第一章_数学基础.md)
 6. [图说特征值](https://www.jianshu.com/p/c7c6481dbb51)
  7. [MIT线性代数](http://open.163.com/special/opencourse/daishu.html)

