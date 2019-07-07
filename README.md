2019/7/2
√1.去除重复值的方法 set,unique
√2.多任务，进程，并行，线程，并发
  华为张志峰：
  多任务意味着多进程，一个任务可能对应着多个进程，但一个任务至少有一个线程。多线程是处理并发的一种编程范式，多进程实际是一种并行（编辑word的时候听歌）。
  华为姚凯强：
  多任务就是多进程，一个任务就需要一个进程来处理，不确定一个任务是否用多进程处理。并发和多线程不是一回事，并发是一种系统状态，是业务决定的（抢红包）；而   多线程是一种处理任务的方法，多线程可以使得系统承受更高的并发状态。进程是并行的。
√3.行列式的几何意义
  二阶行列式的几何意义是向量张成的平行四边形的有向面积，三阶行列式的几何意义是向量张成的平行六面体的有向体积，以此类推。
√4.python伪多线程
  python多线程是单CPU意义上的多线程，与多CPU多线程有本质区别。
  多CPU多线程=并行（真正的同一时刻CPU独立承担任务）内部包含并发（时间片轮转）。
  单CPU多线程=并发（时间片轮转）。
  原因：全局解释器锁（GIL）使得同一时刻只能有一个线程对python对象进行操作，多线程变为了类似时间片轮转的操作。
 5.特征空间
√6.PCA投影（projection）方差最大，信息越多
  PCA本质上是在保持尽量多特征的前提下，将高维特征映射到低维特征。
  X（N,M）=Y（N,D）×W（D,M）其中N个样本没变，但每个样本中的特征维度从D降到M，本质上就是求变换矩阵W，或一个M维度的特征向量
  通过一系列推导，本质上方差越大，特征值越大，特征向量的“特征”越明显。
  
√7.jupyter的文件是在本地还是服务器
  本地，通过ipynb文件可以编辑。
8.奇异值分解的物理含义
  先了解特征值分解和奇异值分解的理论。
  总的来说，奇异值分解是将一个复杂的矩阵分解成若干子矩阵的相乘，子矩阵表征原矩阵的重要特征。
2019/7/3
√1.函数凹凸性对于优化问题的影响
一般将非凸函数转化为凸函数进行求解，因为在数学上证明了，如果一个问题可以转化为凸函数，那么这个问题就比较好解决。
如果更严格地，求解问题可转化为凸优化问题，那么局部最优解一定是全局最优解。
√2.loss函数的选定
  loss函数有非常多，需要根据具体的应用选定，对模型预测效果影响很大。
√3.学习速率的选择
  先大（精度丢失，震荡）后小（过拟合，收敛慢）
√4.过拟合
  拟合能力强，从而预测能力弱（泛化能力弱），lr动态调整，动量项，dropout等
√5.局部最优解

2019/7/4
√1.特征选择和PCA
  特征选择后的特征是原特征的一个子集
  PCA（特征提取）是原特征的一个高位映射，原特征几乎不存在了。
√2.线性回归，分类，logistics回归
  线性回归的输出是连续量，（-∞，+∞）。如果使用线性回归+阈值的方法来解决分类问题，容易受到离群值的影响。
  分类的输出是离散的
  logistics回归是一种特殊的分类（二分类），并不是回归。
  logistics是通过sigmoid函数将线性回归的输出映射到（0，1）区间的，具有概率意义。再通过阈值的设定来进行分类。
√3.SVM
  监督学习。
  以二分类问题为例，本质上是找到一个超平面，使得两类数据到超平面的距离最大。
√4.拉格朗日乘子法和KKT条件
  拉格朗日乘子法解决具有等式约束条件的最优化问题（椭圆内接立方体最大体积问题），构造拉格朗日函数L（x，y，z，λ）=f（x）+λfai（x，y，z）
  KKT条件解决具有不等式约束条件的最优化问题
√5.核函数
  核函数对应着一种从低维度向高纬度的非线性映射。作用是使得在低维空间中线性不可分的样本，在高维空间中线性可分。

2019/7/5
√1.核函数的选择
  核函数常见的有线性核，多项式核，高斯核，sigmoid核。
  在选用核函数的时候，如果我们对我们的数据有一定的先验知识，就利用先验来选择符合数据分布的核函数；如果不知道的话，通常使用交叉验证的方法，来试用不同   的核函数，误差最下的即为效果最好的核函数，或者也可以将多个核函数结合起来，形成混合核函数。在吴恩达的课上，也曾经给出过一系列的选择核函数的方法：
  如果特征的数量大到和样本数量差不多，则选用LR或者线性核的SVM；
  如果特征的数量小，样本的数量正常，则选用SVM+高斯核函数；
  如果特征的数量小，而样本的数量很大，则需要手工添加一些特征从而变成第一种情况。
√2.什么是一个好的聚类
  一个好的聚类要求类内部的相似性尽可能大，类之间的相似性尽可能小。
√3.sklearn的pipeline机制
  在机器学习中，pipeline机制实现了对机器学习全部过程的流程式封装和管理。
  如先标准化数据，然后PCA降维，接着使用算法得出模型（如logistics回归），最后测试模型。
  streaming work flow
4.模型评价metrics
√5.ROC曲线
  曲线下面积越大（越接近1），模型越好。

2019/7/6
√1.红绿蓝，红黄蓝
   光源三原色：红绿蓝（电脑，电视）
   反射三原色：红黄蓝（涂料）
√2.可见光波段
  400-760nm
√3.视频就是多幅图像
4.深拷贝和浅拷贝
