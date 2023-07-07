```js
function instanceOf(left,right){
	let proto=left.__proto__;//获取对象的原型

	//判断构造函数的prototype对象，是否在对象的原型链上
	while(true){
		if(proto===null)
			return false;
		if(proto===right.prototype)//获取构造函数的prototype对象
			return true;

		proto=proto.__proto__;
	}
}
```