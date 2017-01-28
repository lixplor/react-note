# 使用React进行思考

* React适合构建大型, 快速的web应用


## 示例

* 想象我们与一个JSON API接口和一个原型图, 样子如下:

![mock](https://facebook.github.io/react/img/blog/thinking-in-react-mock.png)

JSON API接口返回的数据如下:

```javascript
[
  {category: "Sporting Goods", price: "$49.99", stocked: true, name: "Football"},
  {category: "Sporting Goods", price: "$9.99", stocked: true, name: "Baseball"},
  {category: "Sporting Goods", price: "$29.99", stocked: false, name: "Basketball"},
  {category: "Electronics", price: "$99.99", stocked: true, name: "iPod Touch"},
  {category: "Electronics", price: "$399.99", stocked: false, name: "iPhone 5"},
  {category: "Electronics", price: "$199.99", stocked: true, name: "Nexus 7"}
];
```

## 步骤一: 将UI拆分为组件树

* 首先为每个组件和子组件绘制外边框, 并命名
* 那些部分定义为一个组件? 使用单一职责原则, 即一个组件只处理一件事

![box](https://facebook.github.io/react/img/blog/thinking-in-react-components.png)


