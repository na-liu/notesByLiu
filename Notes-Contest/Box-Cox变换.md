​	Box-Cox变换是统计建模中常用的一种数据变换，用于**连续**的响应变量不满足正态分布的情况。比如线性回归的时候，由于残差epsilon不符合正态分布而不满足建模的条件，这时候要对响应变量Y进行变换，把数据变成正态的。Box-Cox变换之后，可以在一定程度上减小残差和预测变量的相关性。

​	Box-Cox变换的主要特点是引入一个参数，通过数据本身估计该参数进而确定应采取的数据变换形式，Box-Cox变换可以明显地改善数据的正态性、对称性和方差相等性，对许多实际数据都是行之有效的。

​	Box-Cox变换的一般形式为：![img](https://gss0.bdstatic.com/94o3dSag_xI4khGkpoWK1HF6hhy/baike/s%3D156/sign=de90e3cad6b44aed5d4ebae1851d876a/b3fb43166d224f4a782c939305f790529922d1fd.jpg)式中![img](https://gss3.bdstatic.com/7Po3dSag_xI4khGkpoWK1HF6hhy/baike/s%3D32/sign=350792a0b512c8fcb0f3f0cffd03616f/63d9f2d3572c11dfee605fa36f2762d0f603c2f9.jpg)经Box-Cox变换后得到的新变量，![img](https://gss0.bdstatic.com/94o3dSag_xI4khGkpoWK1HF6hhy/baike/s%3D13/sign=b3ba791f22dda3cc0fe4bc2300e9d26d/ac6eddc451da81cbc157634d5e66d016082431f9.jpg)为原始连续因变量，![img](https://gss3.bdstatic.com/7Po3dSag_xI4khGkpoWK1HF6hhy/baike/s%3D12/sign=946062f54fa98226bcc12f258b82ab06/3b87e950352ac65c6f9c86f3f7f2b21192138a91.jpg)为变换参数。以上变换要求原始变量![img](https://gss0.bdstatic.com/94o3dSag_xI4khGkpoWK1HF6hhy/baike/s%3D13/sign=b3ba791f22dda3cc0fe4bc2300e9d26d/ac6eddc451da81cbc157634d5e66d016082431f9.jpg)取值为正，若取值为负时，可先对所有原始数据同加一个常数![img](https://gss3.bdstatic.com/-Po3dSag_xI4khGkpoWK1HF6hhy/baike/s%3D8/sign=32dee09aca5c1038207ec3f3b2904b/d0c8a786c9177f3ebc871c8d7ccf3bc79e3d56fb.jpg)使其![img](https://gss3.bdstatic.com/7Po3dSag_xI4khGkpoWK1HF6hhy/baike/s%3D43/sign=5d7c051200f431adb8d2423a4a36d82e/9345d688d43f87944b09a8aede1b0ef41ad53ab8.jpg)为正值，然后再进行以上的变换。对不同的![img](https://gss3.bdstatic.com/7Po3dSag_xI4khGkpoWK1HF6hhy/baike/s%3D12/sign=946062f54fa98226bcc12f258b82ab06/3b87e950352ac65c6f9c86f3f7f2b21192138a91.jpg)所作的变换不同。在![img](https://gss0.bdstatic.com/94o3dSag_xI4khGkpoWK1HF6hhy/baike/s%3D37/sign=ebad9ce40523dd542573a16fd0090820/42a98226cffc1e17aa3c6cb14690f603728de9ab.jpg)时该变换为对数变换，![img](https://gss2.bdstatic.com/9fo3dSag_xI4khGkpoWK1HF6hhy/baike/s%3D46/sign=4dd53e48164c510faac4e31c6159fd75/d058ccbf6c81800ad349698ebd3533fa838b4786.jpg)时为倒数变换，而在![img](https://gss3.bdstatic.com/-Po3dSag_xI4khGkpoWK1HF6hhy/baike/s%3D50/sign=a96eb769fed3572c62e29cdc8b13831d/37d12f2eb9389b50ec7d00d28935e5dde6116eb4.jpg)时为平方根变换。

​	通过以下几种变换方式可以将非正态数据转换为正态：

- 对数变换
- 平方根变换
- 倒数变换
- 平方根后取倒数
- 平方根后取反正弦
- 幂变换
- 平方变换

[https://baike.baidu.com/item/box-cox%E5%8F%98%E6%8D%A2/10278422?fr=aladdin](https://baike.baidu.com/item/box-cox变换/10278422?fr=aladdin)

http://www.360doc.com/content/19/0124/20/52645714_811083039.shtml

#变换过程中涉及到数学的推导，暂时看不懂~~

极大似然函数、贝叶斯、Jacobi行列式

雅可比行列式：![1568080477679](C:\Users\娜\AppData\Roaming\Typora\typora-user-images\1568080477679.png)