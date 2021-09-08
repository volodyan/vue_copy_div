# vue_copy

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).


```
https://blog.csdn.net/qq_40776187/article/details/85341363   h5复制粘贴文字到剪切板

https://www.cnblogs.com/ww01/p/11950734.html

https://www.cnblogs.com/brucelau/p/10761309.html

需求：点击按钮时复制某段文字，转发时可以直接粘贴

<div id="copy-txt">
    前方高能预警，朋友圈文案在这里哦：**放大招，一分坐公交，还能领红包！
</div>
<button onclick="copyTXT()">复制</button>

HTML5 提供了复制功能的如下API：

document.createRange(): 创建选中容器，返回一个 range Object，支持移动端和 PC 端。
selectNode(DOM): 返回 range Object 上挂载的方法，用来添加选中元素，只能添加一个。
window.getSelection()：用来获得当前选中的元素的内容。一般而言就是用鼠标选中页面上的内容。
addRange(range): 这个方法是挂载到 getSelection()方法下的，用来执行元素的选中。
function copyTXT(){
    var copyDOM = document.querySelector('#copy-txt'); //指定的DOM元素
    var range = document.createRange(); // 创建容器
    range.selectNode(copyDOM); // 选中需要复制的节点
    window.getSelection().addRange(range); // 执行选中元素
    var successful = document.execCommand('copy');// 执行 copy 操作
    try {
        var msg = successful ? 'successful' : 'unsuccessful';
        console.log('Copy was ' + msg);
    } catch(err) {
        console.log('unable to copy');
    }
    window.getSelection().removeAllRanges(); // 移除选中的元素
}

值得注意的是：以上复制的方法是不能自主执行的，也就是说需要某个事件去触发，比如点击，长按等。

```
