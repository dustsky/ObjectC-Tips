1.内容绘制，动画操作

* a.当视图内容发生改变，该通知控制器重新绘制视图：
`setNeedsDisplay   setNeedsDisplayInRect:`
* b.动画属性:
`frame, bouns, center, transform, alpha, backgroundColor` contentStretch
* c.在主线程中操作UIView对象
方法重载:
a.初始化UIView对象
initWithFrame:代码初始化
initWithCoder:xib文件初始化
layerClass:
绘制打印:
a.drawRect:若自己不绘制内容，则不要重载该方法。
b.drawRect:forViewPrintForamtter:
约束:约束一般发生在多视图中
requiresConstraintBaseLayout:基础约束
updateConstraints:更新约束
alignmentRectForFrame:与其他视图对齐关系

2.布局管理，子视图管理
布局:


sizeThatFits:让父对象适应所包含的子对象的最佳尺寸，参数：子对象size. 返回，父对象应该适应的参数
layoutSubviews:约束跟自动布局更加精细。可以重载此方法设置控制器中所有视图初始化中的相应布局
didAddSubview:,willRemoveSubview:在增加子视图动作发生之前，移除子视图将要发生时调用的方法
willMoveToSuperview:,didMoveToSuperview:
willMoveToWindow:,didMoveToWindow:涉及到至少两个window 
3.事件控制

事件操作：
touchesBegan:withEvent:, touchesMoved:withEvent:, touchesEnded:withEvent:, touchesCancelled:withEvent: