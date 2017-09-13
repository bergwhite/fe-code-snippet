## 冒泡排序（Bubble）

```

Array.prototype.sort.bubble = function (arr) {
  var len = arr.length
  var temp = null  // 交换值的中间变量
  // 长得为0或者为1直接返回原数组
  if (len === 1 || len === 0) {
    return arr
  }
  // 第一层循环从0到最后一个值的下标减1
  for (var i = 0; i < len - 1; i++) {
    // 第二层循环从第一层循环的值加1到最后一个值的下标
	for (var j = i + 1; j < len; j++) {
      // 左边的值较大则交换（从小到大排序）
      if(arr[i] > arr[j]) {
        temp = arr[i]
        arr[i] = arr[j]
        arr[j] = temp
      }
    }
  }
  // 返回结果
  return arr
}
var arr = [3,1,3,7,5,8,9,0,3,9,09,0,9,7,55,3,4,224,2]
Array.prototype.sort.bubble(arr)  // [0, 0, 1, 2, 3, 3, 3, 3, 4, 5, 7, 7, 8, 9, 9, 9, 9, 55, 224]

```

## 快速排序

```

Array.prototype.sort.quick = function (arr) {
  var base = null
  function go(arr) {
    var len = arr.length
    var left = []
    var right = []
    if (len === 1 || len === 0) {
      return arr
    }
    base = arr[0]
    for (var i = 1; i < len; i++) {
      arr[i] <= arr[0] ? left.push(arr[i]) : right.push(arr[i])
    }
    return go(left).concat([arr[0]],go(right))
  }
  var newArr = go(arr)
  console.log(newArr)
}
Array.prototype.sort.quick([3,5,74,3,6,3,8,29,3,5,8])

```

## 二分查找

```

Array.prototype.search = {
  binary: function (arr,val) {
    var len = arr.length
    var binary = null
    function go(arr) {
      len = arr.length
      binary = Math.floor(len/2)
      if (binary === 0) {
        return false
      }
      else if (arr[binary] === val) {
        return true
      }
      else if(arr[binary] > val) {
        go(arr.slice(0,binary))
      }
      else if(arr[binary] < val) {
        go(arr.slice(binary,len))
      }
    }
    return go(arr)
  }
}
var newArr = [3,5,74,3,6,3,8,29,3,5,8]
var bin = Array.prototype.search.binary(newArr,8)
console.log(bin)

```

> ing

```

Q:1,2,4,8...30, count total
https://segmentfault.com/q/1010000010053216

```

> 1. Two Sum

```

E:
Given nums = [2, 7, 11, 15], target = 9,
Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].

/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
  var result
  nums.map(function(el,index,arr) {
    var nextEl = target - el
    var nextIndex = arr.indexOf(nextEl)
    if(nextIndex !== -1 && index !== nextIndex) {
      result =  [index, nextIndex]
    }
  })
  return result.sort()
};

```

> 7. Reverse Integer7

```

E:
Example1: x = 123, return 321
Example2: x = -123, return -321

/**
 * @param {number} x
 * @return {number}
 */
var reverse = function(x) {
    if (x === 0) {
        return x
    }
    if (x < -2147483648 || x > 2147483647) {
        return 0
    }
    var flag = 1, result = null
    if (x < 0) {
        flag = -1
        x = x * flag
    }
    result = String(x).split('').reverse().join('')
    result = parseInt(result) * flag
    if (result < -2147483648 || result > 2147483647) {
        return 0
    }
    return result
};

```

> 8. String to Integer (atoi)

```

/**
 * @param {string} str
 * @return {number}
 */
var myAtoi = function(str) {
    var num = parseInt(str)
    if (typeof num === 'number' && !isNaN(num)) {
        if (num > 2147483647) {
            num = 2147483647
        }
        if (num < -2147483648) {
            num = -2147483648
        }
        return num
    }
    return 0
};

```

> devide

```

function p(from, to, step) {
  from = from || 1
  return (from-Math.pow(step, to))/(1-step)
}

```

> plus

```

function dev(num) {
  if(num===1)return 1
  return num * dev(num-1)
}

```