# 日期对象

Date

1、增加ISO类型

```javascript
new Date() //Date {Fri Aug 02 2013 16:50:33 GMT+0800 (China Standard Time)}
new Date(milliseconds) //Date {Fri Aug 02 2013 16:53:26 GMT+0800 (China Standard Time)}
new Date("2013/08/02") //Date {Fri Aug 02 2013 00:00:00 GMT+0800 (China Standard Time)}
new Date("08/02/2013") //Date {Fri Aug 02 2013 00:00:00 GMT+0800 (China Standard Time)}
//iso类型
new Date("1970-01-01T00:00:00.000Z")
```

2、Date.toISOString()

```javascript
console.log(new Date().toISOString()); // 2013-10-07T05:54:38.743Z
```

3、Date.prototype.toJSON()

```javascript
console.log((new Date).toJSON()); // 2013-10-07T06:06:29.288Z
ps:和toISOString() 区别是当invalid date   toJSON()输出 null,toISOString()抛异常
```

4、Date.now()

```javascript
console.log(Date.now()); // 1381125894410
```

​