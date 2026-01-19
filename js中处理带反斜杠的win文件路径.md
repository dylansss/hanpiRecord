### 问题
electron中某个事件返回的'C:\Users\dylan\AppData\Roaming\wildfirechat\86fbf8eb88d34db48c6713864c7097dc'，需要替换其中的内容，但是\会丢
### 解决方案
1. 方法1
const str = electron中某个事件返回的'C:\Users\dylan\AppData\Roaming\wildfirechat\86fbf8eb88d34db48c6713864c7097dc'
const str2 = String.raw`C:\Users\dylan\AppData\Roaming\wildfirechat\86fbf8eb88d34db48c6713864c7097dc`
console.log(str2)
raw后可以跟`${methodName()}`
2. 方法2
const path = require('path')
const str3 = str.split(path.delimiter)
3. 方法3
const path = require('path');

const filePath = 'C:\\Users\\dylan\\AppData\\Local\\Temp\\tmp-18160wzgHtfAikpSu.png';

// 使用path.basename获取文件名
const fileName = path.basename(filePath);

console.log(fileName);