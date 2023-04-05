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
- array
  - [shuffle](#shuffle)
- number
  - [conversionBase](#conversionBase)
  - [thousandth](#thousandth)

## random Methods

### random

返回一个介于 min 和 max 之间的整数 (包含 min 和 max)。

#### params

- `min` (number) (可选)：最小值
- `max` (number) (可选)：最大值

#### returns

- `number`：介于 min 和 max 之间的整数 (包含 min 和 max)。

#### example

```javascript
random(1, 10); // 1 - 10
random(10); // 1 - 10
random(); // 1 - 100
random(-Infinity, Infinity); // -9007199254740991 - 9007199254740991
```

### nonDuplicateRandomList

返回一个不重复的随机数列表。

#### params

- `min` (number)：最小值
- `max` (number)：最大值
- `count` (?number)：随机数个数

#### returns

- `number[]`：随机数列表

#### example

```javascript
nonDuplicateRandomList(1, 10, 5); // [4, 5, 6, 7, 8]
```

### randomList

返回一个随机数列表。

#### params

- `min` (number)：最小值
- `max` (number)：最大值
- `count` (number)：随机数个数

#### returns

- `number[]`：随机数列表

#### example

```javascript
randomList(1, 10, 5); // [8, 9, 10, 8, 10]
```

### weightedRandom

返回一个带权重的随机数。

#### params

- `randomList` (number[])：随机数列表

- `weightList` (number[])：权重列表

或者

- `randomList` ({random: weight})：随机数与权重的键值对

#### returns

- `any`：随机数列表中的某一项

#### example

```javascript
weightedRandom([4, 2, 5, 1, 3], [1, 2, 3, 4, 5]);
// 返回 4 的概率为 1/15
// 返回 2 的概率为 2/15
// 返回 5 的概率为 3/15
// 返回 1 的概率为 4/15
// 返回 3 的概率为 5/15
```

## string Methods

### reverse

返回一个字符串的反转字符串。

#### params

- `str` (string)：要反转的字符串

#### returns

- `string`：反转后的字符串

#### example

```javascript
reverse("hello"); // 'olleh'
reverse(""); // ''
```

### strToNum

将字符串转换为数字。

#### params

- `text` (string)：要转换的字符串

#### returns

- `number`：转换后的数字

#### example

```javascript
strToNum("123"); // 123
strToNum("123.456"); // 123.456
strToNum("123.456.789"); // 123.456789
```

### charToCodePoint

将字符转换为 Unicode 编码。

#### params

- `str` (string)：要转换的字符串
- `options` (object)：可选参数
  - `separator` (string)：分隔符，默认为 `""`
  - `base` (2 | 8 | 10 | 16)：进制，默认为 `16`

#### returns

- `string`：Unicode 编码点

#### example

```javascript
charToCodePoint("Hello"); // "0x480x650x6c0x6c0x6f"
charToCodePoint("Hello World!", { base: 2, separator: " " }); // "0b1001000 0b1100101 0b1101100 0b1101100 0b1101111 0b100000 0b1010111 0b1101111 0b1110010 0b1101100 0b1100100 0b100001"
```

### startsWith

判断字符串是否以指定字符串开头。

#### params

- `str` (string)：要判断的字符串

- `prefix` (string | RegExp)：要判断的字符串或正则表达式

- `position` (number)：开始判断的位置

#### returns

- `boolean`：如果字符串以指定的字符串或正则表达式开头，则返回 `true`，否则返回 `false`

#### example

```javascript
startsWith("Hello World!", "Hello"); // true
startsWith("Hello World!", "World", 6); // true
startsWith("Hello World!", /Hello/); // true
startsWith("Hello World!", /World/, 6); // true
```

### endsWith

判断字符串是否以指定字符串结尾。

#### params

- `str` (string)：要判断的字符串

- `suffix` (string | RegExp)：要判断的字符串或正则表达式

- `endPosition` (number)：结束判断的位置

#### returns

- `boolean`：如果字符串以指定的字符串或正则表达式结尾，则返回 `true`，否则返回 `false`

#### example

```javascript
endsWith("Hello World!", "World!"); // true
endsWith("Hello World!", "Hello", 5); // true
endsWith("Hello World!", /World!/); // true
endsWith("Hello World!", /Hello/, 5); // true
```

## array Methods

### shuffle

返回一个数组的随机排序。

#### params

- `list` (array)：要随机排序的数组

#### returns

- `array`：随机排序后的数组

#### emample

```js
shuffle([1, 2, 3, 4, 5]); // [2, 4, 1, 3, 5]
shuffle([]); // []
```

## number Methods

### conversionBase

将数字转换为指定进制的字符串。

#### params

- `num` (number)：要转换的数字
- `base` (number)：进制

#### returns

- `string`：转换后的字符串

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

- `num` (number): The number to convert

#### returns

- `string`: The converted string

#### example

```javascript
thousandth(123456789); // '123,456,789'
```
