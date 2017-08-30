# ES8

* padStart 和 padEnd

  > 这俩函数的作用就是在字符串的头部和尾部增加新的字符串，并且返回一个具有指定长度的新的字符串。你可以使用指定的字符、字符串或者使用函数提供的默认值－空格来填充源字符串

  ```javascript
  str.padStart(targetLength [, padString])
  str.padEnd(targetLength [, padString])

  //demo
  'es8'.padStart(2);          // 'es8'
  'es8'.padStart(5);          // '  es8'
  'es8'.padStart(6, 'woof');  // 'wooes8'
  'es8'.padStart(14, 'wow');  // 'wowwowwowwoes8'
  'es8'.padStart(7, '0');     // '0000es8'

  'es8'.padEnd(2);          // 'es8'
  'es8'.padEnd(5);          // 'es8  '
  'es8'.padEnd(6, 'woof');  // 'es8woo'
  'es8'.padEnd(14, 'wow');  // 'es8wowwowwowwo'
  'es8'.padEnd(7, '6');     // 'es86666'
  ```

  ​

* Object.values 和 Object.entries

  > Object.values 函数将会返回一个数组，该数组的内容是函数参数（一个对象）可遍历属性的属性值
  >
  > Object.entries 函数与 Object.values 函数类似，也是返回一个数组，只不过这个数组是一个以源对象（参数）的可枚举属性的键值对为数组 [key, value] 的 n 行 2 列的数组

  ```javascript
  const obj = { x: 'xxx', y: 1 };
  Object.values(obj); // ['xxx', 1]
  Object.entries(obj); // [['x', 'xxx'], ['y', 1]]

  const obj = ['e', 's', '8'];
  Object.values(obj); // ['e', 's', '8']
  Object.entries(obj); // [['0', 'e'], ['1', 's'], ['2', '8']]

  const obj = { 10: 'xxx', 1: 'yyy', 3: 'zzz' };
  Object.values(obj); // ['yyy', 'zzz', 'xxx']
  Object.entries(obj); // [['1', 'yyy'], ['3', 'zzz'], ['10': 'xxx']]

  const obj = 'es8'
  Object.values(obj); // ['e', 's', '8']
  Object.entries(obj); // [['0', 'e'], ['1', 's'], ['2', '8']]
  ```

  ​

* Object.getOwnPropertyDescriptors

  > 返回指定对象（参数）的所有自身属性描述符。所谓自身属性描述符就是在对象自身内定义，不是通过原型链继承来的属性。

  ```javascript
  const obj = { 
    get es7() { return 777; },
    get es8() { return 888; }
  };
  Object.getOwnPropertyDescriptor(obj);
  // {
  //   es7: {
  //     configurable: true,
  //     enumerable: true,
  //     get: function es7(){}, //the getter function
  //     set: undefined
  //   },
  //   es8: {
  //     configurable: true,
  //     enumerable: true,
  //     get: function es8(){}, //the getter function
  //     set: undefined
  //   }
  // }
  ```

* 结尾逗号

  > 此处结尾逗号指的是在函数参数列表中最后一个参数之后的逗号以及函数调用时最后一个参数之后的逗号。ES8 允许在函数定义或者函数调用时，最后一个参数之后存在一个结尾逗号而不报 SyntaxError 的错误

  ```javascript
  function es8(var1, var2, var3,) {
    // ...
  }
  es8(10, 20, 30,);
  ```

  ​

* async异步函数

  > 由 async 关键字定义的函数声明定义了一个可以异步执行的函数，它返回一个 AsyncFunction 类型的对象

  ```javascript
  function fetchTextByPromise() {
    return new Promise(resolve => { 
      setTimeout(() => { 
        resolve("es8");
      }, 2000);
    });
  }
  async function sayHello() { 
    const externalFetchedText = await fetchTextByPromise();
    console.log(`Hello, ${externalFetchedText}`); // Hello, es8
  }
  sayHello();
  ```

* 共享内存与原子化

  > 当内存被共享时，多个线程可以在内存中读写相同的数据。原子操作确保预测值的可读和可写，在下一个线程开启前操作未结束，不会导致开启新的线程发生中断。这一部分介绍了一个新的构造器`ShareArrayBuffer`和带有静态方法的名称空间对象`Atomics`。`Atomic`对象是一个类似于有很多方法的`Math`对象，可以向一个构造器一样去使用。

  ```javascript
  add / sub---add / 在一个特定位置上减去一个值
  and/or/xor---与，或，异或
  load---获取特定位置的值
  ```

  ​

*  模板文字限制的改进（es9 确定）

  > 这项改进使得像模板文字一样嵌入替换的特定领域语言(Domain Specific Language) 变得更容易了。
  >
  > 下述代码返回值是 `ES 8 is awesome` 。但是我们在使用模版字符串的时候，有一个限制，那就是不能使用类似于 `\u 或者 \x` 的子字符串。

  ```javascript
  const esth = 8;
  helper`ES ${esth} is `;
  function helper(strs, ...keys) {
    const str1 = strs[0]; // ES
    const str2 = strs[1]; // is
    let additionalPart = '';
    if (keys[0] == 8) { // 8
      additionalPart = 'awesome';
    }
    else {
      additionalPart = 'good';
    }
    
    return `${str1} ${keys[0]} ${str2} ${additionalPart}.`;
  }
  ```

  ​