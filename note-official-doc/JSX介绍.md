# JSX介绍

* `JSX`是JS的语法扩展

```javascript
// jsx示例
const element = <h1>Hello, world!</h1>;
```


## 在JSX中嵌入表达式

* 使用大括号`{}`可以将js表达式嵌入JSX中

```javascript
// js表达式嵌入jsx
function formatName(user) {
  return user.firstName + ' ' + user.lastName;
}

const user = {
  firstName: 'Harper',
  lastName: 'Perez'
};

const element = (
  <h1>
    Hello, {formatName(user)}!    // 此处使用{}包裹了JS语句
  </h1>
);

ReactDOM.render(
  element,
  document.getElementById('root')
);
```

## JSX也是一种表达式

* JSX表达式会被编译为普通的JS对象, 所以可以在`if`和`for`中使用JSX

```javascript
function getGreeting(user) {
  if (user) {
    return <h1>Hello, {formatName(user)}!</h1>;  // 返回的JSX表达式
  }
  return <h1>Hello, Stranger.</h1>;              // 返回的JSX表达式
}
```


## 使用JSX指定属性

* `""`引号可以指定属性
* `{}`大括号可以在属性中嵌入JS表达式

```javascript
// 引号指定属性
const element = <div tabIndex="0"></div>;

// 大括号在属性中嵌入表达式
const element = <img src={user.avatarUrl}></img>;
```

## 使用JSX指定子元素

* 如果一个标签没有子元素, 则可以使用自封闭标签`/>`
* JSX标签可以有内部子元素
* React DOM使用`驼峰式`命名属性, 所以html中的属性名在JSX中使用时需要写为驼峰式
    - 如html标签中的`tabindex`属性要写为`tabIndex`

```javascript
// 自封闭标签
const element = <img src={user.avatarUrl} />;

// 包含子元素的JSX标签
const element = {
    <div>
        <h1>Hello!</h1>
        <h2>Good to see you hear.</h2>
    <div>
);
```


## JSX可以阻止注入攻击

* 默认情况下, React DOM会在渲染前排除嵌入JSX的所有值, 这可以确保无法在程序中注入没有显式写明的任何代码. 所有内容都会在渲染前被转换为一个字符串

```javascript
const title = response.potentiallMaliciousInput;
// 以下是安全的
const element = <h1>{title}</h1>;
```


## 使用JSX来表示对象

* Babel会将JSX编译为`React.createElement()`方法的调用
    - 该方法会执行一系列的检查, 帮助编写没有bug的代码
    - 最重要的是, 该方法会创建一个对象
    - 这些对象称作`React元素`

```javascript
// JSX的写法
const element = {
    <h1 className="greeting">
        Hello, world!
    </h1>
);

// 上面的JSX经过Babel编译后实际上是转换为React.createElement()方法进行调用
const element = React.createElement(
    'h1',
    {className:'greeting'},
    'Hello, world!'
);

// React.createElement()创建的对象如下
const element = {
    type:'h1',
    props:{
        className:'greeting',
        children:'Hello, world'
    }
};
```
