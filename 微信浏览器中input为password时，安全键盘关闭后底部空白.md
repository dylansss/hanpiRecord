### 问题

微信浏览器适配问题

### 解决

mounted() {
this.bodyHeight = document.documentElement.clientHeight
let timer = null
document.body.addEventListener('focusin', (e) => { // 软键盘弹起事件
if (timer && e.target.type !== 'button') {
clearTimeout(timer)
timer = null
}
})
document.body.addEventListener('focusout', (e) => { // 软键盘关闭事件
if (e.target.type === 'password') {
timer = setTimeout(() => {
clearTimeout(timer)
timer = null
const nowH = document.documentElement.clientHeight
if (nowH < this.bodyHeight) {
const oinput = document.createElement('input')
oinput.style.width = '0px'
document.body.appendChild(oinput)
oinput.focus()
oinput.blur()
document.body.removeChild(oinput)
}
}, 1000)
}
})
},
