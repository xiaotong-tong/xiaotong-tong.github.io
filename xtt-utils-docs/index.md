# xtt-utils

## navList

- random
  - [random](#random)
  - [nonDuplicateRandomList](#nonDuplicateRandomList)
  - [randomList](#randomList)
  - [weightedRandom](#weightedRandom)
- string
  - [reverse](#reverse)
  - [strToNum](#strToNum)
  - [charToCodePoint](#charToCodePoint)
  - [startsWith](#startsWith)
  - [endsWith](#endsWith)
  - [getTermLeft](#getTermLeft)
  - [getTermRight](#getTermRight)
  - [getRangeByTerm](#getRangeByTerm)
- array
  - [shuffle](#shuffle)
- number
  - [conversionBase](#conversionBase)
  - [thousandth](#thousandth)
- file
  - [b64ToBlob](#b64ToBlob)
  - [fileToB64](#fileToB64)
- function
  - [chain](#chain)
  - [throttle](#throttle)

## random Methods

### random

返回一个介于 min 和 max 之间的整数 (包含 min 和 max)。

#### params

- [min=1] (number) (可选)：最小值
- [max=100] (number) (可选)：最大值

如果不传递参数，返回一个介于 1 和 100 之间的整数 (包含 0 和 100)。

如果包含一个参数，则返回一个介于 1 和参数之间的整数 (包含 1 和 max)。

如果包含两个参数，则返回一个介于 min 和 max 之间的整数 (包含 min 和 max)。

#### returns

- (number)：介于 min 和 max 之间的随机整数 (包含 min 和 max)。

#### note

如果 max 大于 Number.MAX_SAFE_INTEGER，会返回一个介于 min 和 Number.MAX_SAFE_INTEGER 之间的整数

如果 min 小于 Number.MIN_SAFE_INTEGER，会返回一个介于 Number.MIN_SAFE_INTEGER 和 max 之间的整数

> Number.MAX_SAFE_INTEGER = 9007199254740991 = 2^53 - 1
>
> Number.MIN_SAFE_INTEGER = -9007199254740991 = -(2^53 - 1)

#### example

```javascript
random(1, 10); // 1 - 10
random(10); // 1 - 10
random(); // 1 - 100
random(-Infinity, Infinity); // -9007199254740991 - 9007199254740991
```

### nonDuplicateRandomList

生成一个没有重复值的随机数列表

#### params

- [min=0] (number)：最小值
- [max=9] (number)：最大值
- [count=max-min+1] (number)：生成的随机数的个数

#### returns

- (number[])：随机数列表

#### example

```javascript
nonDuplicateRandomList(1, 10, 5); // [4, 5, 6, 7, 8]
nonDuplicateRandomList(1, 10, 10); // [8, 7, 10, 4, 3, 5, 2, 1, 9, 6]
nonDuplicateRandomList(1, 10); // [2, 1, 4, 7, 3, 10, 5, 9, 6, 8]
```

### randomList

生成一个随机数列表

#### params

- [min=1] (number)：最小值
- [max=100] (number)：最大值
- [count=1] (number)：列表个数

#### returns

- (number[])：每项均介于 min 和 max 之间的 length 为 count 的随机数列表

#### example

```javascript
randomList(1, 10, 5); // [8, 9, 10, 8, 10]
randomList(1, 10, 10); // [3, 5, 4, 1, 10, 7, 6, 9, 4, 10]
```

### weightedRandom

获取权重随机数

#### params

- randomList (any[] | Object<string,number>)：随机数列表。
  当 randomList 为 Object 时，权重列表将被忽略，Object 的 key 为随机数列表，value 为权重列表
- [weightList] (number[])：权重列表

#### returns

- (any)：随机数列表中的某一项

#### example

```javascript
weightedRandom([1, 2, 3], [4, 5, 6]); // 4/15 的概率返回 1，5/15 的概率返回 2，6/15 的概率返回 3
weightedRandom({ 1: 4, 2: 5, 3: 6 }); // 同上
```

## string Methods

### reverse

返回一个字符串的反转字符串。

#### params

- str (string)：要反转的字符串

#### returns

- (string)：反转后的字符串

#### example

```javascript
reverse("hello"); // 'olleh'
reverse(""); // ''
```

### strToNum

将字符串转换为数字。

#### params

- text (string)：要转换的字符串

#### returns

- (number)：转换后的数字

#### example

```javascript
strToNum("123"); // 123
strToNum("123.456"); // 123.456
strToNum("123.456.789"); // 123.456789
```

### charToCodePoint

返回一个字符串的 Unicode 编码点。

#### params

- str (string)：要转换的字符串
- [options] (Object)：可选参数
  - [separator=""] (string)：分隔符
  - [base=16] (2 | 8 | 10 | 16)：进制

#### returns

- (string)：Unicode 编码点

#### example

```javascript
charToCodePoint("Hello"); // "0x480x650x6c0x6c0x6f"
charToCodePoint("Hello World!", { base: 2, separator: " " }); // "0b1001000 0b1100101 0b1101100 0b1101100 0b1101111 0b100000 0b1010111 0b1101111 0b1110010 0b1101100 0b1100100 0b100001"
```

### startsWith

判断字符串是否以指定的字符串或正则表达式匹配的字符串开头

#### params

- str (string)：要判断的字符串

- prefix (string | RegExp)：要判断的字符串或正则表达式

- [position] (number)：开始判断的位置

#### returns

- (boolean)：如果字符串以指定的字符串或正则表达式匹配的字符串开头，则返回 `true`，否则返回 `false`

#### example

```javascript
startsWith("Hello World!", "Hello"); // true
startsWith("Hello World!", "World", 6); // true
startsWith("Hello World!", /Hello/); // true
startsWith("Hello World!", /World/, 6); // true
```

### endsWith

判断字符串是否以指定的字符串或正则表达式匹配的字符串结尾

#### params

- str (string)：要判断的字符串

- suffix (string | RegExp)：要判断的字符串或正则表达式

- [endPosition] (number)：结束判断的位置

#### returns

- (boolean)：如果字符串以指定的字符串或正则表达式匹配的字符串结尾，则返回 `true`，否则返回 `false`

#### example

```javascript
endsWith("Hello World!", "World!"); // true
endsWith("Hello World!", "Hello", 5); // true
endsWith("Hello World!", /World!/); // true
endsWith("Hello World!", /Hello/, 5); // true
```

### getTermLeft

获取字符串中匹配项左侧的字符串

#### params

- str (string)：要获取的字符串

- searchTerm (string | RegExp)：要匹配的字符串或正则表达式

- [beforeWhichTimes=1] (number)：匹配到几次后停止，默认为 1, 如果数字大于匹配到的次数，则返回最后一个匹配项左侧的字符串

#### returns

- (string)：返回匹配项左侧的字符串

#### example

```js
getTermLeft("abcde", "c"); // "ab"
getTermLeft("abcde", "c", 2); // "ab"
getTermLeft("abcdec", "c", 2); // "abcde"
getTermLeft("abc1de2", /\d/); // "abc"
getTermLeft("abc1de2", /\d/, 2); // "abc1de"
getTermLeft("abc1de2", /\d/, 3); // "abc1de"
```

### getTermRight

获取字符串中匹配项右侧的字符串

#### params

- str (string)：要获取的字符串

- searchTerm (string | RegExp)：要匹配的字符串或正则表达式

- [beforeWhichTimes] (number)：匹配到几次后停止，默认为 1, 如果数字大于匹配到的次数，则返回最后一个匹配项右侧的字符串，如果想取右侧开始第一个匹配项，可以传入 -1

#### returns

- (string)：返回匹配项右侧的字符串

#### example

```js
getTermRight("abcde", "c"); // "de"
getTermRight("abcde", "c", 2); // "de"
getTermRight("abcdec", "c", 2); // ""
getTermRight("abc1de2", /\d/); // "de2"
getTermRight("abc1de2", /\d/, 2); // ""
getTermRight("abc1de2", /\d/, 3); // ""
```

### getRangeByTerm

获取字符串中某个范围内的字符串

#### params

- str (string)：要处理的字符串
- term ([string | RegExp, string | RegExp])：要匹配的字符串或正则表达式范围

#### returns

- (string)：返回匹配范围内的字符串

#### example

```js
getRangeByTerm("abcde", ["b", "d"]); // "c"
getRangeByTerm("abcde", ["d", "b"]); // "c"
getRangeByTerm("a1bcd2e", [/\d/, /\d/]); // "bcd"
```

## array Methods

### shuffle

乱序数组

#### params

- list (array)：需要打乱的数组

#### returns

- (array)：乱序后的数组

#### emample

```js
shuffle([1, 2, 3, 4, 5]); // [2, 4, 1, 3, 5]
```

## number Methods

### conversionBase

将数字转换为指定进制的字符串。

#### params

- num (number)：要转换的数字
- [base=10] (2 | 8 | 10 | 16)：进制

#### returns

- (string)：转换后的字符串，除十进制外, 其他进制会添加字符串前缀 0x, 0o, 0b

#### example

```javascript
conversionBase(10, 2); // '0b1010'
conversionBase(10, 8); // '0o12'
conversionBase(10, 16); // '0xa'
conversionBase(0xa, 10); // '10'
```

### thousandth

将数字转换为千分位格式。

#### params

- num (number): The number to convert
- - [maximumFractionDigits=20] (number): The maximum number of digits after the decimal point

#### returns

- (string): The converted string with thousandth format

#### example

```javascript
thousandth(1000000); // "1,000,000"
thousandth(1000000.1234); // "1,000,000.1234"
thousandth(1000000.1234, 2); // "1,000,000.12"
```

## file Methods

### b64ToBlob

将 base64 字符串转换为 Blob 对象。

#### params

- b64Data (string)：base64 字符串

#### returns

- (Promise<Blob>)：promise of Blob object

#### notes

使用了 `fetch` API，因此在 node.js 环境中使用需要考虑兼容性， node.js v18.0.0 以上版本才支持 `fetch` API。

详见: https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API

### fileToB64

Converts a file Object to a base64 string.

> warning
>
> This functino is supported in browser environment only.
> Not supported in node.js environment. Because `File` and `FileReader` is not a global object in node.js.

#### params

- file (File): File object

#### returns

- (Promise<string>): promise of the base64 string

## function Methods

### chain

创建一个链式调用规则，之后可以使用链式调用的方式来操作数据。最后可以通过 value() 方法来获取最终的值。

#### params

- [self=this] (object): 需要链式调用的对象, 默认为 this 对象。
- [?initValue] (\*): 初始值, 在下一次调用链式调用的方法时会作为第一个参数传入

如果仅传入一个参数, 且该参数不是对象, 则该参数会作为 initValue 值，如果传入的是对象，则该对象会作为 self 值

#### returns

- (Proxy): 代理对象

#### example

```js
chain(xttUtils, "Hello World!")
	.reverse()
	.reverse()
	.getTermRight(" ")
	.endsWith("World")
	.value(); // true

xttUtils
	.chain("Hello World!")
	.reverse()
	.reverse()
	.getTermRight(" ")
	.endsWith("World")
	.value(); // true
```

### throttle

节流函数, 在调用函数时, 如果处于空闲状态, 则立即执行函数, 并进入等待状态,
在等待时间内, 如果再次调用函数, 则保存当前调用值, 直到等待时间结束,
如果多次调用函数,最后一次调用值会覆盖前面的调用值,
等待时间结束后, 如果有保存的调用值, 则执行函数, 并进入等待状态，如果没有保存的调用值, 则进入空闲状态，等待下一次调用。

#### params

- func (function)：要节流的函数
- delay (number)：等待时间

#### returns

- (function)：节流后的函数

#### example

```js
// 1 2 3 4 5 6 7 8 9 10
throttle((a) => console.log(a), 3000);
// 假如每隔 0.9 秒触发一次
// 1 4 7 10
// 0.9 秒时触发1, 立即执行;
// 1.8 秒后触发 2, 等待;
// 2.7 秒后触发 3, 等待;
// 3.6 秒后触发 4, 等待;
// 3.9 秒时等待时间结束，运行最后一次的调用，输出 4;
// 4.5 秒后触发 5, 等待
// ...
```
