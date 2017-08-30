# ES6特性

常用

1、let命令,const 命令 

> const实际上保证的，并不是变量的值不得改动，而是变量指向的那个内存地址不得改动。

2、块级作用域

> 解决场景:1、内层变量可能会覆盖外层变量；2、循环变量泄露为全局变量3、可以在块级作用域内声明函数

    function f1() {
      let n = 5;
      if (true) {
        let n = 10;
      }
      console.log(n); // 5
    }

3、箭头函数

> 简化了函数的书写方法，解决this指向问题

    //es5写法：
    var item = data.map( function ( item, i ){
       return item;
    });
    //使用箭头函数
    var item = data.map( (item,i) => {
       return item
    });



4、Classes

    //首先定义一个类
    class Fruit {
     constructor( name ){
         this.name = name;
    }
    getName(){
        console.log(this.name)
    }
    }
    //创建子类继承上面的类
    class Banana extends Fruit{
    constructor(name){
       super(name);
    }
    testFunc(){
       console.log('who is my father');
    }
    }
    //测试
    var fruit =  new Fruit('fruit');
    var banana = new Banana('banana');
    fruit.getName();  //fruit
    banana.getName(); // banana



5、模板字符串

    //es5写法
    var dom = '<div>hello,'+username+'</div>';
    //es6语法
    var dom = `<div>hello, ${username}</div>`;

6、for...of 循环

> 每次循环提供的是不同索引的值

    var arr = [12,13,14,15,23];
    for (i of arr){
    	console.log(i);  //依次输出：12, 13, 14, 15, 23
    }



7、默认参数  

> es6中定义函数时可以给参数设置默认值

    //es5写法
    function getName(name){
    var myName = name || 'rose';
    console.log('my name is'+myName);
    }
    //es6
    function getName(name='rose'){
    console.log(`my name is ${name}`);
    }



8、拓展运算符

> 扩展运算符是三个点（...）。它好比 rest 参数的逆运算，将一个数组转为用逗号分隔的参数序列。

    // es5的写法
    function count(x, y, z) {
    console.log(x,y,z);
    }
    var arr = [0, 1, 2];
    count.apply(null, arr);
    // es6的写法
    function count(x, y, z) {
    console.log(x,y,z);
    }
    var arr = [0, 1, 2];
    count(...arr);

9、对象字面量

> es6可以在对象字面量里定义原型，可以不用function关键字来定义方法，也可以直接调用父类方法

    var meat = {
    cook(){
     console.log('cook meat');
    }
    };
    var human = {
    _proto_:meat,  //指定该对象原型为meat，继承了meat
    };
    meat.cook(); // cook meat
    human.cook(); // cook meat

10、Promise

> Promise是异步编程的一种解决方案，将异步操作以同步操作的流程表达出来，避免了层层嵌套的回调函数

    var promise = new Promise((resolve, reject)=>{
    if(/*if success*/){
     resolve('it completed');
    }else{
     reject(Error('it failed));
    }
    });
    //绑定处理程序
    promise.then(function(result){
    console.log(result); // 程序成功后会运行此处：it completed
    },function(err){
    console.log(err);  //程序失败会运行此处：it failed
    }

11、global 对象 

12、解构

> ES6 允许按照一定模式，从数组和对象中提取值，对变量进行赋值，这被称为解构（Destructuring）。

    let [a, b, c] = [1, 2, 3];  //a=1 b=2 c=3
    let [bar, foo] = [1];   // bar=1  foo=undefined
    let { foo, bar } = { foo: "aaa", bar: "bbb" };
    const [a, b, c, d, e] = 'hello';
    
    function add([x, y]){
      return x + y;
    }
    
    add([1, 2]); // 3
