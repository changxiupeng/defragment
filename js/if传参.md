if 后的圆括号中是一个表达式，这个表达式经过计算后返回的结果是 true 或者 false。

## Syntax
```JavaScript
if (condition)
   statement1
[else
   statement2]
```

### condition
condition 是一个可以计算出一个布尔值的表达式。

condition 也可以是任意一个数值或者变量（判断的是变量所拥有的值），这个数值会被强制装换成布尔值。
1. 被强制装换成 false 的值为：
- false
- null
- undefined
- 0
- ""
- NaN

这六个数值会被强制装换成 false

2. 不会被强制装换成 false 的值就会被转换成 true


这样，如果我们可以确定一个变量所拥有的数值，我们可以直接在圆括号中传入变量，传入的变量一般有两种类型：
1. 对象的属性
如果对象中没有该属性的话，那么传入的就是 null，可以用来测试该对象中是否含有该属性。一般这种情况用 in 操作符是最保险的，因为该属性的值可能是 0 ，“” 等可以转成 false 的值。
2. 函数的形参
可以检测函数调用时，是否对该形参进行了赋值，没有的话，该形参的值为 undefined。
