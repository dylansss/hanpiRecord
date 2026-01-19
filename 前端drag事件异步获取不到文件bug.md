### 问题

前端， drag 事件，当 drop 的时候 e.dataTransfer 中携带了一个文件，但是如果异步处理这个对象，文件就会消失，以下是例子代码，

```
<template>
    <div
        class="conversation-item-container"
        @dragover="dragEvent($event, 'dragover')"
        @dragleave="dragEvent($event, 'dragleave')"
        @dragenter="dragEvent($event, 'dragenter')"
        @drop="dragEvent($event, 'drop')"
    >
    </div>
</template>
async dragEvent(e, v) {
    console.log(e.dataTransfer.files, 'e.dataTransfer.files');
    setTimeout(() => {
        console.log(e.dataTransfer.files, 'e.dataTransfer.files');
    });
}
```

### 解决方案

通过使用 Array.from(e.dataTransfer.files) 来创建一个文件对象的副本，你就可以在异步处理中使用这个副本，而不会受到原始文件对象的变化影响。

```
async dragEvent(e, v) {
    console.log(e.dataTransfer.files, 'e.dataTransfer.files');

    // 保存文件对象的副本
    const filesCopy = Array.from(e.dataTransfer.files);

    // 在异步处理之前使用文件对象的副本
    setTimeout(() => {
    console.log(filesCopy, 'filesCopy');
    });
}

```


