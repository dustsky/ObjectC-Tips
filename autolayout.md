### 官方文档直达车[AutoLayout](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/AutolayoutPG/Introduction/Introduction.html)

#### 参考资料：
##### [iOS7 Autolayout 瞬间入门！](http://bigbelldev.com/blog/2013/10/23/ios7-auto-layout/)
##### [为iPhone6设计自适应布局](http://www.devtalking.com/articles/adaptive-layout-for-iphone6-1/)

#### 知识点梳理：
----
###### 约束基本知识点：

1. 将约束(constraint)看作数学表达式：一个视图view包含一个button,在这对视图中，假定“视图view的左边缘具其所包含button左边缘距离为20points”,则可以翻译为：button.left = view.left +20，转换成数学表达：y = m*x + b;其中：
	
	（1). x,y 均是视图的属性。 基本属性值包括：left, right, top, bottom, leading, trailing, width, height, centerX, centerY, and baseline.
	
	（2). m,b 均是浮点型值。
	
2. 约束可设置的其他属性：

    (1). 常量(constant value)
    (2). 关系
    (3). 优先级
----    
###### 
	 
	
	