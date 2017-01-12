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
