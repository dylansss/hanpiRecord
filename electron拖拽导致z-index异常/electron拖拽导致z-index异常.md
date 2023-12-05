### 问题
如图，i图标z-index设为2，下面的div设为1，图标悬浮在背景颜色之上，但是点击不到，div设为2，就正确盖着图标了
<image src=./1.jpg />
<image src=./2.jpg />
### 原因
-webkit-app-region: drag，区域支持拖动的属性，会让dom在交互上优先z-index
### 解决方案
调整设置-webkit-app-region: drag属性的dom的尺寸，不重叠
