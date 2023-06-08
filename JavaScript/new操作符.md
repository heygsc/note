### 步骤
1.先创建一个空对象
2.把空对象 和 构造函数 通过原型链 进行链接
3.把构造函数的 this 绑定到 新的空对象身上
4.根据构建函数返回的类型判断
如果是值类型，则返回对象
如果是引用类型，就要返回这个引用类型
```js
function newFun(Fun,...args){
    //1.先创建一个空对象
    let newObj={}
	//2.把空对象 和 构造函数 通过原型链 进行链接
    newObj.__proto__=Fun.prototype
	//3.把构造函数的 this 绑定到 新的空对象身上
    const result=Fun.apply(newObj,args)
	//4.根据构建函数返回的类型判断
    //如果是值类型，则返回对象
    //如果是引用类型，就要返回这个引用类型
    return result instanceof Object ? result : newObj
}

function Person(name){
    this.name=name
}
Person.prototype.say=function(){
    console.log('hhh')
}

const p1=newFun(Person,'hey')
p1.say() //hhh
console.log(p1) //name是hey
```
