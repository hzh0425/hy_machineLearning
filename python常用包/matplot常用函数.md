# matplotlib中常用函数

- **散点图**

- **柱状图**

- **等高线**

- **matplotlib绘制3D图**

- **子图像**

- 动态图

  ## 常见设置

  ### 一、设置坐标轴

  ```python
  # x轴和y轴的值域
  
  
  
  plt.xlim((-1,2))
  
  
  
  plt.ylim((-2,3))
  
  
  
   
  
  
  
  # color为线的颜色，linewidth为线宽度，linestyle为样式（-为实线，--为虚线）
  
  
  
  plt.plot(x,y,color='red',linewidth=1.0,linestyle='—')
  
  
  
   
  
  
  
  plt.figure #绘制一个新画布
  
  
  
  plt.figsize #花布尺寸
  
  
  
   
  
  
  
  # x和y轴
  
  
  
  plt.xtick()
  
  
  
  plt.ytick()
  
  
  
  例如：
  
  
  
  plt.xticks(new_ticks) #new_ticks 为-2，2分成十一等份
  
  
  
  plt.yticks([-1,0,1,2,3],
  
  
  
            ['level2','level2','level3','level4','level5'])
  ```

   

![这里写图片描述](https://img-blog.csdn.net/20171104104033057?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMzg1NDIwODU=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

二、

- ```python
  plt.gca #获取当前的坐标轴
  
  
  
  spines['right'].set_color('red’) #右边框为红色
  
  
  
  # 分别把x轴与y轴的刻度设置为bottom与left
  
  
  
  xaxis.set_ticks_position('bottom')
  
  
  
  yaxis.set_ticks_position('left’)
  
  
  
  # 分别v把bottom和left类型设置为data，交点为（0，0）
  
  
  
  spines['bottom'].set_position(('data',0))
  
  
  
  spines['left'].set_position(('data',0))
  
  
  
   
  
  
  
   
  
  
  
  例如：
  
  
  
  ax = plt.gca()
  
  
  
  ax.spines['right'].set_color(‘red')
  
  
  
  ax.spines['top'].set_color(‘red’)
  ```

  ![这里写图片描述](https://img-blog.csdn.net/20171104104429257?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMzg1NDIwODU=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

  三、

  ```python
  l1, = plt.plot(x,y1,color='red',linewidth=1.0,linestyle='—') #设置两条线为l1,l2    注：应该在后面加上，
  
  
  
  l2, = plt.plot(x,y2,color="blue",linewidth=5.0,linestyle="-")
  
  
  
  plt.legend(handles=[l1,l2],labels=['test1','test2'],loc='best’) #将l1，l2绘制于一张图中，其中名字分别是l1，l2，位置自动取在最佳位置
  ```

  ![这里写图片描述](https://img-blog.csdn.net/20171104104606041?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMzg1NDIwODU=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

  ### 设置备注

  ```python
  x0 = 0.5
  
  
  
  y0 = 2*x0 + 1
  
  
  
  # 画点
  
  
  
  plt.scatter(x0,y0,s=50,color='blue')
  
  
  
  # 画虚线
  
  
  
  plt.plot([x0,x0],[y0,0],'k--',lw=2)#[x0,x0],[y0,0]代表x0，y0点作虚线交于x0，0  k--代表颜色的虚线,lw代表宽度
  
  
  
  plt.annotate(r'$2x+1=%s$' % y0,xy=(x0,y0),xytext=(+30,-30),textcoords='offset points',fontsize=16,arrowprops=dict(arrowstyle='->',connectionstyle='arc3,rad=.2'))
  
  
  
  #xy=(x0,y0)指在x0，y0点，xytext=(+30,-30)指在点向右移动30，向下移动30,textcoords='offset points'指以点为起点
  
  
  
  #arrowprops=dict(arrowstyle='->',connectionstyle='arc3,rad=.2')指弧度曲线，  .2指弧度
  
  
  
  plt.text(-2,2,r'$This\ is\ the\ text$',fontsize=16,color='red’) #-2,2指从-2，2开始写
  ```

  ![这里写图片描述](https://img-blog.csdn.net/20171104104632825?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMzg1NDIwODU=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

  ------

  ## 散点图

  ```python
  x = np.random.normal(0,1,500)
  
  
  
  y = np.random.normal(0,1,500)
  
  
  
  plt.scatter(x,y,s=50,color='blue',alpha=0.5) #s指点大小，alpha指透明度
  
  
  
  plt.show()
  ```

  ![这里写图片描述](https://img-blog.csdn.net/20171104104726421?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMzg1NDIwODU=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

  ------

  ## 柱状图

  ```python
  x = np.arange(10)
  
  
  
  y = 2**x + 10
  
  
  
  plt.bar(x,y,facecolor='#9999ff',edgecolor='white')#柱颜色，柱边框颜色
  
  
  
  for x,y in zip(x,y):#zip指把x，y结合为一个整体，一次可以读取一个x和一个y
  
  
  
      plt.text(x,y,'%.2f' % y,ha='center',va='bottom')#指字体在中间和柱最顶的顶部
  
  
  
  plt.show()
  ```

  ![这里写图片描述](https://img-blog.csdn.net/20171104104942460?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMzg1NDIwODU=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

  ------

  ## 等高图

  ```python
  def f(x,y):
  
  
  
      #用来生成高度
  
  
  
      return (1-x/2+x**5+y**3)*np.exp(-x**2-y**2)
  
  
  
   
  
  
  
  x = np.linspace(-3,3,100)
  
  
  
  y = np.linspace(-3,3,100)
  
  
  
   
  
  
  
  X,Y = np.meshgrid(x,y)#将x，y指传入网格中
  
  
  
  plt.contourf(X,Y,f(X,Y),8,alpha=0.75,cmap=plt.cm.hot)#8指图中的8+1根线，绘制等温线，其中cmap指颜色
  
  
  
   
  
  
  
  C = plt.contour(X,Y,f(X,Y),8,colors='black',linewidth=.5)#colors指等高线颜色
  
  
  
  plt.clabel(C,inline=True,fontsize=10)#inline=True指字体在等高线中
  
  
  
   
  
  
  
  plt.xticks(())
  
  
  
  plt.yticks(())
  
  
  
  plt.show()
  ```

  ![这里写图片描述](https://img-blog.csdn.net/20171104104959658?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMzg1NDIwODU=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

  ------

  ## matplotlib绘制3D图

  ```python
  from mpl_toolkits.mplot3d import Axes3D#动态图所需要的包
  
  
  
  fig = plt.figure()
  
  
  
  ax = Axes3D(fig)
  
  
  
   
  
  
  
  x = np.arange(-4,4,0.25)#0.25指-4至4间隔为0.25
  
  
  
  y = np.arange(-4,4,0.25)
  
  
  
  X,Y = np.meshgrid(x,y)#x，y放入网格
  
  
  
  R = np.sqrt(X**2 + Y**2)
  
  
  
  Z = np.sin(R)
  
  
  
   
  
  
  
  ax.plot_surface(X,Y,Z,rstride=1,cstride=1,cmap=plt.get_cmap('rainbow'))#rstride=1指x方向和y方向的色块大小
  
  
  
  ax.contourf(X,Y,Z,zdir='z',offset=-2,cmap='rainbow')#zdir指映射到z方向，-2代表映射到了z=-2
  
  
  
  ax.set_zlim(-2,-2)
  
  
  
   
  
  
  
  plt.show()
  ```

  ![这里写图片描述](https://img-blog.csdn.net/20171104105014196?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMzg1NDIwODU=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

  ------

  ## 子图像

  ```python
  plt.figure()
  
  
  
  plt.subplot(2,2,1)#建立一个两行两列的画布，第一个
  
  
  
  plt.plot([0,1],[0,1])
  
  
  
  plt.subplot(2,2,2)#第二个
  
  
  
  plt.plot([0,1],[0,1])
  
  
  
  plt.subplot(2,2,3)#第三个
  
  
  
  plt.plot([0,1],[0,1])
  
  
  
  plt.subplot(2,2,4)#第四个
  
  
  
  plt.plot([0,1],[0,1])
  
  
  
  plt.show()
  ```

  ![这里写图片描述](https://img-blog.csdn.net/20171104105921054?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMzg1NDIwODU=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

  ```python
  plt.figure()
  
  
  
  plt.subplot(2,1,1)#建立一个两行两列的画布，第一个
  
  
  
  plt.plot([0,1],[0,1])
  
  
  
  plt.subplot(2,3,4)#第二个
  
  
  
  plt.plot([0,1],[0,1])
  
  
  
  plt.subplot(2,3,5)#第三个
  
  
  
  plt.plot([0,1],[0,1])
  
  
  
  plt.subplot(2,3,6)#第四个
  
  
  
  plt.plot([0,1],[0,1])
  
  
  
  plt.show()
  ```

  ![这里写图片描述](https://img-blog.csdn.net/20171104105947745?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMzg1NDIwODU=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

  ------

  ## 动态图

  ```python
  from matplotlib import animation#动态图所需要的包
  
  
  
  fig,ax = plt.subplots()#子图像
  
  
  
  x = np.arange(0,2*np.pi,0.01)
  
  
  
  line, = ax.plot(x,np.sin(x))
  
  
  
   
  
  
  
  def animate(i):
  
  
  
      line.set_ydata(np.sin(x+i/10))#用来改变的y对应的值
  
  
  
      return line,
  
  
  
  def init():
  
  
  
      line.set_ydata(np.sin(x))#动态图初始图像
  
  
  
      return line,
  
  
  
   
  
  
  
  ani = animation.FuncAnimation(fig=fig,func=animate,init_func=init,interval=20)#动态作图的方法，func动态图函数，init_func初始化函数，interval指图像改变的时间间隔
  
  
  
  plt.show()
  ```

  ![这里写图片描述](https://img-blog.csdn.net/20171104105059995?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMzg1NDIwODU=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

  注：若想看动态效果请在ipython中使用

## 使用颜色映射

颜色映射（colormap）是一系列颜色，它们从起始颜色渐变到结束颜色。在可视化中，颜色映射用于突出数据的规律，例如，你可能用较浅的颜色来显示较小的值，并使用较深的颜色来显示较大的值。

```python
import matplotlib.pyplot as plt 



 



x_values = list(range(1001)) 



y_values = [x**2 for x in x_values] 



 



plt.scatter(x_values, y_values, c=y_values, cmap=plt.cm.Blues, edgecolor='none', s=40)
```

![img](https://pic1.zhimg.com/80/v2-3ac499ec3a77bd7b16cfac2d53c6b512_hd.jpg)

这些代码将y值较小的点显示为浅蓝色，并将y值较大的点显示为深蓝色。

 

## Matplotlib进阶-Seaborn

`Seaborn`其实是在`matplotlib`的基础上进行了更高级的`API`封装，从而使得作图更加容易，在大多数情况下使用`seaborn`就能做出很具有吸引力的图。

## 安装方式

安装方式类似于`matplotlib` , 在Windows下和Linux下面都可以采用`pip`安装方式。

## set_style( )

```
set_style( )`是用来设置主题的，`Seaborn`有五个预设好的主题： `darkgrid , whitegrid , dark , white` ,和 `ticks` 默认： `darkgrid
import matplotlib.pyplot as plt  



import seaborn as sns  



 



sns.set_style("whitegrid")  



plt.plot(range(10))  



 



plt.show()
```

![img](https://pic4.zhimg.com/80/v2-0511a89d1998a754315f6b21f5d909e5_hd.jpg)

## 直方图

直方图的绘制：

```python
import matplotlib.pyplot as plt  



import seaborn as sns



import pandas as pd



 



df_iris = pd.read_csv(r'D:\Windows 7 Documents\Desktop\iris.csv')  



 



sns.distplot(df_iris['petal_length'], kde = True)   # kde 密度曲线  rug 边际毛毯  



 



plt.show()
```

![img](https://pic1.zhimg.com/80/v2-f528abb38c710b1f9b481f472f309202_hd.jpg)

## 箱型图

箱形图（Box-plot）又称为盒须图、盒式图或箱线图，是一种用作显示一组数据分散情况资料的统计图。因形状如箱子而得名。

```python
import matplotlib.pyplot as plt  



import seaborn as sns



import pandas as pd



 



df_iris = pd.read_csv(r'D:\Windows 7 Documents\Desktop\iris.csv')  



 



sns.boxplot(x = df_iris['species'], y = df_iris['sepal_width'])  



 



plt.show()
```

![img](https://pic1.zhimg.com/80/v2-9eed6b9ef5d52994a1f976c7646c7c98_hd.jpg)

## 联合分布

两个变量的画图

```python
import matplotlib.pyplot as plt  



import seaborn as sns



import pandas as pd



 



df_iris = pd.read_csv(r'D:\Windows 7 Documents\Desktop\iris.csv')  



 



sns.jointplot(df_iris['petal_width'], df_iris['sepal_width']) 



 



plt.show()
```

![img](https://pic2.zhimg.com/80/v2-18d1d9cf2435b20e61ce5062d01eba37_hd.jpg)

不用圆点表示的话也是可以的，可以用其他方式来表示，比如六角形来表示：

```python
import matplotlib.pyplot as plt  



import seaborn as sns



import pandas as pd



 



df_iris = pd.read_csv(r'D:\Windows 7 Documents\Desktop\iris.csv')  



 



sns.jointplot(df_iris['petal_width'], df_iris['sepal_width'], kind='hex') 



 



plt.show()
```

![img](https://pic7.zhimg.com/80/v2-bdbf5e559c855e01c714f0aa88ec382c_hd.jpg)

## 热力图

相关系数是最早由统计学家卡尔·皮尔逊设计的统计指标，是研究变量之间线性相关程度的量，一般用字母 r 表示。由于研究对象的不同，相关系数有多种定义方式，较为常用的是皮尔逊相关系数。
相关系数是用以反映变量之间相关关系密切程度的统计指标。相关系数是按积差方法计算，同样以两变量与各自平均值的离差为基础，通过两个离差相乘来反映两变量之间相关程度；着重研究线性的单相关系数。公式：

![r(X,Y)=\frac{Cov(X,Y)}{\sqrt{Var[X]Var[Y]}}](https://www.zhihu.com/equation?tex=r(X%2CY)%3D\frac{Cov(X%2CY)}{\sqrt{Var[X]Var[Y]}})以上公式中：

![Cov(X,Y) = E[XY]-E[X]E[Y]](https://www.zhihu.com/equation?tex=Cov(X%2CY)+%3D+E[XY]-E[X]E[Y])

![Var(X)=E{[X-E(X)^2] }=E(X^2)-[E(X)]^2](https://www.zhihu.com/equation?tex=Var(X)%3DE{[X-E(X)^2]+}%3DE(X^2)-[E(X)]^2)

```python
import matplotlib.pyplot as plt  



import seaborn as sns



import pandas as pd



 



df_iris = pd.read_csv(r'D:\Windows 7 Documents\Desktop\iris.csv')  



 



corrmat = df_iris[df_iris.columns[:4]].corr()



 



sns.heatmap(corrmat, square=True, linewidths=.5, annot=True)



plt.show()
```

![img](https://pic3.zhimg.com/80/v2-8b9cd4d68c269c820e619d59e921878b_hd.jpg)

## 多变量图

关注数据框中各个特征之间的相关关系，呈现图形的展示，给人以直观的感受。而不是"冰冷"的数字。可以非常方便的找到各个特征之间呈现什么样的关系。比如线性，离散等关系。

```python
import pandas as pd



import matplotlib.pyplot as plt  



import seaborn as sns  



 



data = pd.read_csv(r"D:\Windows 7 Documents\Desktop\iris.csv")  



 



sns.set(style="ticks")    # 使用默认配色  



sns.pairplot(data,hue="species")   # hue 选择分类列  



 



plt.show()
```

![img](https://pic1.zhimg.com/80/v2-f7a510f5691ce0de180e73aed812a33d_hd.jpg)