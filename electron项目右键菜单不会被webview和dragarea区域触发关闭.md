### 问题
electron项目右键菜单不会被webview和dragarea区域触发关闭，因为 您无法将键盘、鼠标和滚动事件侦听器添加到 webview。 
### 解决方案
右键时给webview添加pointer-events: none; dragarea直接移除对应属性或类名，隐藏右键菜单时恢复