## 对象

> 所有对象操作中，如果`o`不是`Object`类型，将会抛出`TypeError`异常

- Object.create(prototype[,descriptors]) 

  > 返回以对象`o`为`prototype`创建的新的对象。如果对象描述`p`存在，就使用其定义刚创建的对象。

  ```javascript
  var o = Object.create({ 
    "say": function () {
      alert(this.name)
    },            
    "name":"Byron"        
  });
  ```

* Object.getPrototypeOf(o)

  > 获取对象的`prototype`对象。等价于以前的`o.__proto__`


* Object.defineProperty(O,Prop,descriptor)

  > 根据规则`attrs`定义对象`o`上，属性名为`p`的属性

* Object.defineProperties(o,props)

  > 根据对象描述`props`来定义对象`o`，通常`props`包含多个属性的定义。


* Object.getOwnPropertyDescriptor(o,p)

  > 获取对象描述

* Object.getOwnPropertyNames

  > 获取自有属性名列表。结果列表将不包含原型链上的属性

* Object.keys()

  ```javascript
  function Person(){
    this.age = 18;
  }
  Person.prototype.name="s";
  var p1 = new Person();
  for(var i in p1){
     console.log(i)//age,name
  }
  console.log(p1.hasOwnProperty("age"));//实例属性
  console.log(p1);//打印{age: 18, __proto__:{name:"s"}}
  console.log(p1.name);//可以打印值
  console.log(Object.keys(p1));//只有age（实例）,可枚举的（是否可枚举是可以设置的）
  console.log(Object.getOwnPropertyNames(p1))//只有age（实例），包括不可枚举的
  ```

* Object.preventExtensions(o) / Object.isExtensible

  > 将对象置为不可扩展
  >
  > 判对一个对象是否可扩展。

* Object.seal(o)

  > 一个对象在默认状态下，

  1. extensible: 可以添加新的属性
  2. configurable: 可以修改已有属性的特性

  `Object.seal`会改变这两个特性，既不能扩展新属性，也不能修改已有属性的特性。

* Object.isSealed(o)

  > - 对象的每个自有属性：如果属性的`configurable`特性为`true`，则返回`false`
  > - 如果对象为`extensible`的，那么返回`false`
  > - 不满足以上两个条件，则返回`true`

* Object.freeze(o)

  > 将对象的每个自有自有属性(own property)做如下操作：
  >
  > - 属性的`writable`特性置为`false`
  > - 属性的`configurable`特性置为`false`
  >
  > 同时，该对象将不可扩展。可见，该方法比`Object.seal`更加严格的限制了对一个对象的未来改动。

* Object.isFrozen(o)

  > - 对每个自有属性，如果该属性的`configurable`或`writable`特性为`true`，则返回`false`
  > - 如果对象为`extensible`的，那么返回`false`
  > - 不满足以上两个条件，则返回`true`

* Object.prototype.isPrototypeOf(v)

  > 检查对象是否是位于给定对象`v`的原型链上。

* Object.prototype.propertyIsEnumerable(p)

  > 检查一个对象上的属性`p`是否可枚举。

