## autoLoadMore v2.0
一款pc和移动端适用的滚动加载更多插件，监听滚动位置，在滚动到底部的时候自动请求加载数据

此插件中某些判断根据公司接口习惯去编写，若要使用可适当改变autoLoadMore.js中请求成功后的判断
## 开始使用
#### 加载插件

```
<script src="http://cdn.bootcss.com/jquery/2.2.1/jquery.min.js"></script>
<script src="autoLoadMore.js"></script> 
```
#### html内容
```
//scroller-wrapper为滚动元素，thelist为scroller-wrapper中的唯一子元素
<div id="scroller-wrapper">
    <ul class="thelist">
        <li style="padding: 20px 10px;border-bottom: 1px solid #ddd;">测试列表</li>
        <li style="padding: 20px 10px;border-bottom: 1px solid #ddd;">测试列表</li>
        <li style="padding: 20px 10px;border-bottom: 1px solid #ddd;">测试列表</li>
    </ul>   
</div>
```
#### 初始化autoLoadMore

```
<script type="text/javascript">
    var pageLoader = new autoLoadMore({
        ajax_url: 'abc.html'
    });
</script>
```

## 配置选项

| Option | 类型 | 默认值 | 说明 |
| ------------- |:-------------:|:-------------:| :-------------|
scrollerEle | string | #scroller-wrapper | 滚动元素的id |
listEle | string | .thelist | 滚动元素中包裹列表项的父元素 |
tipsPadding | number | 10 | 加载提示的上下padding |
tipsFontColor | string | #777 | 加载提示的文字颜色 |
tipsFontSize | number | 12 | 加载提示的文字大小 |
tipsBackground | string | transparent | 加载提示的背景颜色 |
start_page | number | 2 | 加载更多的初始请求页数 |
ajax_type | string | GET | 加载更多的请求类型（GET/POST）|
ajax_url | string | 空字符串 | 加载更多的请求链接（必填）|
ajax_data | object | 空对象 | 加载更多的请求参数 |
finishTips | string | 已没有更多数据 | 没有更多数据时的提示文字 |
extactHeight | number | 0 | thelist中内容列表以下的多余高度，如footer等，将其总高度传入 |
requestKey | string | data | 接口返回对象中放置数据内容的键 |
requestSuccess | function(res) |  | 请求成功时的回调函数，html字符串拼接、插入等处理应在此处执行 |


## 实例方法


```
/**
 * 更新请求参数
 * 如果在不刷新页面的情况下需要改变请求的参数，则使用此方法
 * @param  {String} key  参数的键名
 * @param  {String} val 参数的值名
 */
pageLoader.updateData(key,val);


/**
 * 重置页面请求状态
 * 执行后请求页数将重新回到start_page的初始值
 * @param  {String} key  参数的键名
 * @param  {String} val 参数的值名
 */
pageLoader.resetPage();

```

