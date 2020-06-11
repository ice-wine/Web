#### 转Boolean类型

```javascript
!!'a'//true
```

#### 转Number类型

```js
+'45'//45  
+new Date//13位时间戳
```

#### 向下取整

```js
~~3.14159//3  
~~'5.678'//5  
-2.33 | 0 //-2  
2.33 >> 0 //2
```

#### 短路表达式

```js
let a = b || 1;//b为真，a=b;b为假，a=1;  
let c = b && 1;//b为真，c=1;b为假，c=b;  
// 使用!!符号  
let isValid = !!(value && value !== 'error');
```

#### 保留指定位数的小数点

```js
let num = 2.443242342;  
num = num.toFixed(4); //"2.4432"  toFixed() 方法返回的是字符串而不是一个数字。
```

#### 单行写一个评级组件

```js
let rate = 3;  
"★★★★★☆☆☆☆☆".slice(5 - rate, 10 - rate);//"★★★☆☆"
```

#### 金钱格式化

```js
//正则  
let cash = '1234567890'  
cash.replace(/\B(?=(\d{3})+(?!\d))/g, ',');//"1,234,567,890"  
//非正则的优雅实现  
function formatCash(str) {  
 return str.split('').reverse().reduce((prev, next, index) => {  
 return ((index % 3) ? next : (next + ',')) + prev  
 })  
}  
formatCash(cash);//"1,234,567,890"  
```

// 非正则的方法，先把字符串转成了数组，反转了一下变成了[0,9,8,7,6,5,4,3,2,1]。再对新的数组进行reduce操作，数组元素位置除3取余，是3的倍数的位置就增加’,’，最后返回累加的字符串。

#### 标准JSON的深拷贝

```js
let a = {  
 a1: 1,  
 b1: { c: 1, d: 2 }  
};  
let b = JSON.parse(JSON.stringify(a));  
b;//{a1: 1, b1: {…}}
```

#### 数组去重

```js
let array=[1, "1", 2, 1, 1, 3];  
//拓展运算符(...)内部使用for...of循环  
[...new Set(array)];//[1, "1", 2, 3\]  
//利用Array.from将Set结构转换成数组  
Array.from(new Set(array));//[1, "1", 2, 3\]
```