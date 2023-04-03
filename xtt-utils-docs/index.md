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

#### example

```javascript
random(1, 10); // 1 - 10
random(10); // 1 - 10
random(); // 1 - 100
random(-Infinity, Infinity); // -9007199254740991 - 9007199254740991
```

### nonDuplicateRandomList

返回一个不重复的随机数列表。

#### example

```javascript
nonDuplicateRandomList(1, 10, 5); // [4, 5, 6, 7, 8]
```

### randomList

返回一个随机数列表。

#### example

```javascript
randomList(1, 10, 5); // [8, 9, 10, 8, 10]
```

### weightedRandom

返回一个带权重的随机数。

#### example

```javascript
weightedRandom([1, 2, 3, 4, 5], [1, 2, 3, 4, 5]); // 5
```

## string Methods

### reverse

返回一个字符串的反转字符串。

#### example

```javascript
reverse("hello"); // 'olleh'
reverse(""); // ''
```

### strToNum

将字符串转换为数字。

#### example

```javascript
strToNum("123"); // 123
strToNum("123.456"); // 123.456
strToNum("123.456.789"); // 123.456789
```

### charToCodePoint

将字符转换为 Unicode 编码。

#### example

```javascript
charToCodePoint("Hello"); // "0x480x650x6c0x6c0x6f"
charToCodePoint("Hello World!", { base: 2, separator: " " }); // "0b1001000 0b1100101 0b1101100 0b1101100 0b1101111 0b100000 0b1010111 0b1101111 0b1110010 0b1101100 0b1100100 0b100001"
```

### startsWith

判断字符串是否以指定字符串开头。

#### example

```javascript
startsWith("Hello World!", "Hello"); // true
startsWith("Hello World!", "World", 6); // true
startsWith("Hello World!", /Hello/); // true
startsWith("Hello World!", /World/, 6); // true
```

### endsWith

判断字符串是否以指定字符串结尾。

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

#### example

```javascript
shuffle([1, 2, 3, 4, 5]); // [2, 4, 1, 5, 3]
```

## number Methods

### conversionBase

将数字转换为指定进制的字符串。

#### example

```javascript
conversionBase(10, 2); // '0b1010'
conversionBase(10, 8); // '0o12'
conversionBase(10, 16); // '0xa'
conversionBase(0xa, 10); // '10'
```

### thousandth

将数字转换为千分位格式。

#### example

```javascript
thousandth(123456789); // '123,456,789'
```
