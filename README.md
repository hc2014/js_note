# js_note
js笔记
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
输出结果是#####tom今年18岁了#####。这样看来感觉还不错，那继续看例子:
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

而且with语句会改变当前对象的作用域(####见高性能js笔记第二章第二小节####)
###综合结论:with能不用就不要用
