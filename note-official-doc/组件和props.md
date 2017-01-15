# 组件和props

* `组件(Component)`可以将UI拆分成独立的, 可复用的部分
* 从概念上讲, 组件类似JS中的函数. 他们接收输入(即`props`), 然后返回React元素, 来描述屏幕上需要显示的内容
* 组件标签通常第一个字母大写, 以便与普通DOM标签区分: `<div />`, `<Welcome />`


## 函数组件和类组件

* `函数组件`是最简单的定义组件的方式: 写一个JS函数
    - 一个有效的React函数组件:
        - 是一个JS函数
        - 只接收一个`props`对象作为参数来传递数据
        - 返回一个React元素
* `类组件`使用ES6的`class`关键字来定义组件


```javascript
// 函数组件: 使用JS函数定义一个组件
function Welcome(props) {                   // 接收一个单独的props参数
    return <h1>Hello, {props.name}</h1>;    // 返回一个React元素
}

// 类组件: 使用ES6 class关键字定义一个组件
class Welcome extends React.Component {
    render() {
        return <h1>Hello, {this.props.name}</h1>;
    }
}
```

## 渲染一个组件

* React元素可以代表一个DOM标签, 也可以代表一个用户自定义的组件
* 当React遇到用户自定义组件时, 会将JSX属性作为一个单独的对象传入该组件, 传入的对象就称为`props`

```javascript
// React元素表示DOM标签
const element = <div />;

// React元素表示自定义组件
const element = <Welcome name="Sara" />;

// React将JSX属性name传入到自定义组件的props对象中
function Welcome(props) {                   // 自定义组件, 接收props对象
    return <h1>Hello, {props.name}</h1>;    // 获取props对象的name属性
}

const element = <Welcome name="Sara" />;    // JSX组件的name属性
ReactDOM.render(
    element,
    document.getElementById('root')
);
```


## 组合组件

* 组件可以引用其他组件作为输出, 这易于使用相同的组件实现抽象
    - 按钮, 表单, 对话框, 屏幕, 在React应用中都是通过组件表现的
* 组件必须返回一个单独的根元素, 所以组合组件可以用`<div />`来包裹
* 一般情况下, React应用在顶部有一个单独的`App`组件

```javascript
// 在App组件中使用Welcome组件
function Welcome(props) {
    return <h1>Hello, {props.name}</h1>;
}

function App() {
    return (
        <div>
            <Welcome name="Sara" />
            <Welcome name="Cahal" />
            <Welcome name="Edite" />
        </div>
    );
}

ReactDOM.render(
    <App />,
    document.getElementById('root')
);
```

## 抽取组件

* 组件可以拆分为更小的组件, 有利于复用


## props是只读的

* 无论通过函数还是类声明组件, 该组件不应该修改自己的props
* React对此有一条规则: **所有React组件必须是纯粹的函数, 并尊重他们的props**

```javascript
// 正确的写法, 传入的a和b的值并没有改变
function sum(a, b) {
    return a + b;
}

// 错误的写法, 传入的account被改变了
function withdraw(account, amount) {
    account.total -= amount;
}
```
