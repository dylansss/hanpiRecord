### 问题

同时使用 v-if 和自定义指令实现控制 dom(如按钮)的挂载(指的是实例挂载和卸载，非 v-show 的显隐功能)，会导致指令冲突，按钮可能会异常情况下展示出来（如自定义指令是静态指令，此时动态切换 v-if 可能导致 dom 在非期望情况下展示），连续使用多个此场景双指令进行 dom 渲染，可能导致 dom 渲染卡死；

### 实例代码

!e.treeNode.instType ||
0 != e.hasCampus ||
("4" !== e.treeNode.instType &&
"5" !== e.treeNode.instType)
? e.\_e()
:
t(
"el-button",
{
directives: [
{
name: "hasPermi",
rawName: "v-hasPermi",
value: [
"basic:schoolStaff:removeInSch",
],
expression:
"['basic:schoolStaff:removeInSch']",
},
],
attrs: {
type: "primary",
plain: "",
size: "mini",
},
on: {
click: e.handleRemoveInSch,
},
},
[
t("svg-icon", {
attrs: {
"icon-class": "g-callin",
scale: "1.2",
},
}),
e._v("调入本学校"),
],
1
),

### 解决方案

1、在需要使用 v-if 的场景下，不要使用该类型自定义指令；
2、若自定义指令必须使用，切勿和 v-if 搭配使用；
3、一定需要和 v-if 搭配，可以考虑对自定义指令添加封装参数，同时处理静态参数和动态参数；
