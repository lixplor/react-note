# Hello World

React渲染DOM的示例:
* 示例寻找id为`root`的标签, 然后将`h1`标签的内容放入root标签内
* 上面这个过程叫做`渲染`

```javascript
ReactDOM.render(
    <h1>Hello, world!</h1>,
    document.getElementById('root')
);
```
