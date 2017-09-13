# ES6 手册

## Set和Map

> Set（集合）

Set不会存储相同值的数据。

```

// 去重

const arr = [1,3,1,4]
let s = new Set()
arr.forEach(e=>s.add(e))
console.log(s)  // Set {1, 3, 4}
console.log([...s])  // [1, 3, 4]

[...new Set(arr)]  // [1, 3, 4] 这个也可以去重

// 遍历DOM

function divs () {
  return [...document.querySelectorAll('div')];
}
var set = new Set(divs());
console.log(set)  // Set {div#sidebar {}, div#content {}, div#disqus_thread {}, div#back_to_top {}, div#edit {}…}

divs().forEach(div => set.add(div));  // 效果和上面一样

```

**Set方法**

```

s.add(1).add(2).add(2);
// 注意2被加入了两次

s.size // 2

s.has(1) // true
s.has(2) // true
s.has(3) // false

s.delete(2);
s.has(2) // false

```

## 迭代

> Iterator（遍历器）

ES6中原生具备Iterator接口的有数组、某些类数组的对象、Set和Map。

```

// 模拟遍历器
var it = makeIterator(['a', 'b']);

it.next() // { value: "a", done: false }
it.next() // { value: "b", done: false }
it.next() // { value: undefined, done: true }

function makeIterator(array) {
  var nextIndex = 0;
  return {
    next: function() {
      return nextIndex < array.length ?
        {value: array[nextIndex++], done: false} :
        {value: undefined, done: true};
    }
  };
}

```

**解构赋值**

```

let val = new Set().add(1).add(2).add(3)
let [a,b,c] = val
console.log(a)  // 1
console.log(b)  // 2
console.log(c)  // 3

```

**扩展运算符**

```

let str = 'hello'
console.log([...str])  // ["h", "e", "l", "l", "o"]
let arr = ['a','b']
console.log(['c',...arr,'d'])  // ["c", "a", "b", "d"]

```

**字符串Iterator接口**

```

let str = 'try'
let show = str[Symbol.iterator]()
show.next()  // Object {value: "t", done: false}

```

**for...of循环**

for...of内部调用的是数据结构的Symbol.iterator方法。遍历对象需要使用for...in。

```

let arr = ['a','b','c']
arr.test = 'hello'  // 测试两种遍历是否会把这个也输出

// for...of（迭代出的是值）

for ( let x of arr) {
	console.log(x)  // a,b,c
}

// for...in（迭代出的是下标）

for ( let x in arr) {
	console.log(x)  // 0,1,2,test
}

// arr.forEach（ES5）

arr.forEach(function(e,i,arr){
	console.log(e)  // a,b,c
	console.log(i)  // 0,1,2
})

```

> Generator（迭代器）

```

function* gen(){
	yield 1+1
	yield 1
	yield {}
	yield ''
	yield []
	return 'zzz'
}
var tryGen = gen()
// 调用得逐次输入，否则会直接显示最后的结果
tryGen.next()  // Object {value: 2, done: false}
tryGen.next()  // Object {value: 1, done: false}
...
tryGen.next()  // Object {value: "zzz", done: true}
tryGen.next()  // Object {value: undefined, done: true}

```

参考

* [ECMAScript 6 入门 - 阮一峰](http://es6.ruanyifeng.com)