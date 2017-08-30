# 数组

* Array.isArray(element)  

  > 用来判断一个对象是不是数组

* Array.indexOf(e,i) / .lastIndexOf(e,i) 

  > 使用“严格等”来获取元素`e`在数组中的索引号。一个可选的搜索起点`i`
  >
  > 使用“严格等”来获取元素`e`在数组中最后出现的位置。起始位置`i`为可选

* **之后介绍的所有数组遍历方法，都支持一个可选的上下文对象`c`，可以灵活设置回调函数的执行上下文**

* Array.every(t,c)  

  > 测试数组中的每个元素都满足测试`t`。全部匹配为true  否则为false

* Array.forEach(element,index,array)   

  > 遍历数组

* Array.some(t,c)  

  > 返回布尔值  匹配一项为true  全部不匹配为false

* Array.map() 

  > 遍历数组，组回调函数返回值组成一个新数组返回，新数组索引结构和原数组一致，原数组不变

* filter(function(element))  

  > 返回数组的一个子集，回调函数用于逻辑判断是否返回，返回true则把当前元素加入到返回数组中，false则不加，新数组只包含返回true的值，索引缺失的不包括，原数组保持不变

* reduce(r,v) / .reduceRight(r,v)

  > 从左向右，使用函数`r`聚集数组的每个元素。可选的制定一个初始值`v`
  >
  > 从右向左，使用函数`r`聚集数组的每个元素。可选的制定一个初始值`v`

