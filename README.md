# js_note
#with用法
with的优点在于可以很便捷的使用对象的属性,例如:
```
var obj={
  name:"tom",
  age:18
}
with(obj){
  alert(name+"今年"+age+"岁了!")
}
```
输出结果是*tom今年18岁了*。这样看来感觉还不错，那继续看例子:
```
with(obj){
a=b;
}
```
光从此代码片段谁能够看出结果是什么？
以上代码和下面代码做的是同样的事情:
```
if(obj.a===undefined){
  a=obj.b===undefined?b:obj.b;
}else{
  obj.a=obj.b===undefined?b:obj.b;
}
```
而这样的话，却会得到这四种结果中 任意一种:
```
a=b;
a=obj.b;
obj.a=b;
obj.a=obj.b
```
所以对于对象obj包含的属性或者是否存在全局变量a和b都对其的运算结果又影响

而且with语句会改变当前对象的作用域(**见高性能js笔记第二章第二小节**)
###综合结论:with能不用就不要用


#"+"号的妙用和警惕
```
var a="1";
typeof(+a)
```
范围的将会是"number",所以这样就可以把一个数字类型的字符串转变成数字了

```
var a="1";
a+1//11
a-1//0
```
数字类型的字符串在跟数字做*+*运算的时候是拼接字符串,而做*-*运算的时候就是做算术减法
####如有其他内容后续补上
