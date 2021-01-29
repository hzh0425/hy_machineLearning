## SVM简单实例

支持向量机的基本模型是定义在特征空间上的间隔最大的线性分类器，其中间隔最大使它有别于感知机。支持向量机旨在求一个分离超平面。这个超平面使得离它最近的点能够最远。

SVM用scikit-learn库实现起来比较简单，下面就是用svm算法分类鸢尾花的实例。

**导入鸢尾花数据集**

```的
from sklearn import datasets
iris = datasets.load_iris()
12
```

**数据集划分**

```s
from sklearn.model_selection import train_test_split
# 特征
iris_feature = iris.data
# 分类标签
iris_label = iris.target
# 划分
X_train, X_test, Y_train, Y_test = train_test_split(iris_feature, iris_label, test_size=0.3, random_state=42)
1234567
```

**训练SVM分类器**

```d
from sklearn import svm
svm_classifier = svm.SVC(C=1.0, kernel='rbf', decision_function_shape='ovr', gamma=0.01)
svm_classifier.fit(X_train, Y_train)
123
```

> 创建svm分类器并进行训练：首先，利用sklearn中的SVC（）创建分类器对象，其中常用的参数有C（惩罚力度）、kernel（核函数）、gamma（核函数的参数设置）、decision_function_shape（因变量的形式），再利用fit()用训练数据拟合分类器模型。
>
> ```python
> model=svm.SVC(C=2,kernel='rbf',gamma=10,decision_function_shape='ovo') 
> model.fit(train_data,train_label.ravel())    #ravel函数在降维时默认是行序优先
> ```
>
> - C越大代表惩罚程度越大，越不能容忍有点集交错的问题，但有可能会过拟合（defaul C=1）；
> - kernel常规的有‘linear’, ‘poly’, ‘rbf’, ‘sigmoid’, ‘precomputed’ ，默认的是rbf；
> - gamma是核函数为‘rbf’, ‘poly’ 和 ‘sigmoid’时的参数设置，其值越小，分类界面越连续，其值越大，分类界面越“散”，分类效果越好，但有可能会过拟合，默认的是特征个数的倒数；
> - decision_function_shape='ovr'时，为one v rest（一对多），即一个类别与其他类别进行划分，等于'ovo'时，为one v one（一对一），即将类别两两之间进行划分，用二分类的方法模拟多分类的结果。

**分类器分类效果**

```d
print("训练集:", svm_classifier.score(X_train, Y_train))
print("测试集:", svm_classifier.score(X_test, Y_test))
12
```

**结果**
![在这里插入图片描述](https://gitee.com/zisuu/picture/raw/master/img/20210128225508.png)