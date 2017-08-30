# ES7特性

- Array.prototype.includes

  > 用来替代indexOf，检查数组中是否存在值

  ```javascript
  let arr = ['react', 'angular', 'vue']

  // WRONG
  if (arr.indexOf('react')) { // 0 == false
    console.log('Can use React') //  不会执行
  }

  // Correct
  if (arr.indexOf('react') !== -1) {
    console.log('Can use React')
  }

  if (arr.includes('react')) {
    console.log('Can use React')
  }
  ```

  ​

- Exponentiation Operator(求冥运算)

  ```javascript
  let a = 7 ** 12
  let b = 2 ** 7
  console.log(a === Math.pow(7,12)) // true
  console.log(b === Math.pow(2,7)) // true
  ```

​