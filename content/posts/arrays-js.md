---
title: "Arrays Js"
date: 2023-02-19T14:40:07+05:30
draft: true
---

# Arrays

| Keyword                                                          |
| :--------------------------------------------------------------- |
| **const** variables can't be reintialized. But we can modify it. |
| For adding `array.push()` method.                                |
| For adding `array.push()` method.                                |

---

| Summary |
| :------ |
| TBD     |
| TBD     |

---

| Notes |
| :---: |

```javascript
const numbers = [3, 4];
```

We can't reassign an initialized constant array. If we try, we get following error.

```javascript
numbers = [];
```

_TypeError: Assignment to constant variable._

**NOTE:** _But const won't stop us form modifying an array._

## 1. Adding elements to an array

### 1.1 End

- New elements of the Array.
- Appends new elements to an array, and returns the new length of the array.

```js
numbers.push(5, 6); // 4
console.log(numbers); // [3, 4, 5, 6]
```

### 1.2 Begining

- Elements to insert at the start of the Array.
- Inserts new elements at the start of an array.

```js
numbers.unshift(1, 2); // 6
console.log(numbers); // [1, 2, 3, 4, 5, 6]
```

### 1.3 Middle

```js
numbers.splice(2, 0, 'a', 'b'); // [1, 2, 'a', 'b', 3, 4, 5, 6]
```

## 2. Remove elements from an array

```javascript
const numbers = [3, 4];
```

We can't reassign data to initialized constant object. If we try, we get following error.

```javascript
numbers = [];
```

_TypeError: Assignment to constant variable._

**NOTE:** _But const won't stop us form modifying an object._

## Exercise

```shell
npm test
```

### 1. Sum

#### Code

```javascript
/**
 * sum() function that:
 * 1. Can accept any number of arguments.
 * 2. Requires all arguments to be numbers and throws an error if any is not a number.
 * 3. Computes and returns the sum of its arguments provided all are numbers.
 * 4. Returns 0 if no argument is passed.
 */
module.exports = function () {
  // Convert arguments object to an array
  var args = Array.prototype.slice.call(arguments);

  // Throw error if arguments contain non-finite number values
  if (!args.every(Number.isFinite)) {
    throw new TypeError('sum() expects only numbers.');
  }

  // Return the sum of the arguments
  return args.reduce(function (a, b) {
    return a + b;
  }, 0);
};
```

#### Test

```javascript
var sum = require('../src/sum');
var expect = require('chai').expect;

describe('#sum()', function () {
  context('without arguments', function () {
    it('should return 0', function () {
      expect(sum()).to.equal(0);
    });
  });

  context('with number arguments', function () {
    it('should return sum of arguments', function () {
      expect(sum(1, 2, 3, 4, 5)).to.equal(15);
    });

    it('should return argument when only one argument is passed', function () {
      expect(sum(5)).to.equal(5);
    });
  });

  context('with non-number arguments', function () {
    it('should throw error', function () {
      expect(function () {
        sum(1, 2, '3', [4], 5);
      }).to.throw(TypeError, 'sum() expects only numbers.');
    });
  });
});
```

#### Result

```Shell
#sum()
    without arguments
      √ should return 0
    with number arguments
      √ should return sum of arguments
      √ should return argument when only one argument is passed
    with non-number arguments
      √ should throw error

  4 passing (20ms)
```

### 2. Create an array of numbers from range.

#### Code

```javascript
/**
 * Returns an array of numbers within in specified range.
 * 1. Create an empty result array.
 * 2. Start from min number, loop through till max number.
 * 3. In each iteration, store item to result array.
 * 4. Return updated result array.
 */

function arrayFromRange(min, max) {
  let resultArray = [];
  for (let number = min; number <= max; number++) {
    resultArray.push(number);
  }
  return resultArray;
}

module.exports = arrayFromRange;
```

#### Test

```javascript
var arrayFromRange = require('../src');
var expect = require('chai').expect;

describe('#arrayFromRange()', function () {
  context('with valid arguments', function () {
    it('should return range from 1 to 4', function () {
      expect(arrayFromRange(1, 4)).deep.equal([1, 2, 3, 4]);
    });

    it('should return range from -1 to 4', function () {
      expect(arrayFromRange(-1, 4)).deep.equal([-1, 0, 1, 2, 3, 4]);
    });

    it('should return range from -4 to 4', function () {
      expect(arrayFromRange(-4, 4)).deep.equal([-4, -3, -2, -1, 0, 1, 2, 3, 4]);
    });

    it('should return range from -4 to -2', function () {
      expect(arrayFromRange(-4, -2)).deep.equal([-4, -3, -2]);
    });
  });

  context('with invalid arguments', function () {
    it('should return an empty array', function () {
      expect(arrayFromRange(4, 1)).deep.equal([]);
    });
  });
});
```

#### Result

```Shell
#arrayFromRange()
    with valid arguments
      √ should return range from 1 to 4
      √ should return range from -1 to 4
      √ should return range from -4 to 4
      √ should return range from -4 to -2
    with invalid arguments
      √ should return an empty array

  5 passing (18ms)
```

### 3. Replicate includes() function.

#### Code

```javascript
/**
 * includes() should return 'true' if searchElement is present. Otherwise returns 'false'.
 * 1. Loop through the array.
 * 2. If searching element present, return true. Otherwise returns 'false'.
 */

function includes(array, searchElement) {
  for (let item = 0; item <= array.length; item++) {
    if (item === searchElement) return true;
  }
  return false;
}

module.exports = includes;
```

#### Test

```javascript
let includes = require('../src');
let expect = require('chai').expect;

describe('#includes()', () => {
  context('with valid arguments', () => {
    it('should return true', () => {
      expect(includes([1, 2, 3, 4], 3)).equal(true);
    });

    it('should return false', () => {
      expect(includes([1, 2, 3, 4], 40)).equal(false);
    });
  });
});
```

#### Result

```Shell
 #includes()
    with valid arguments
      √ should return true
      √ should return false

  2 passing (8ms)
```

### N. TBD

#### Code

```javascript
tbd;
```

#### Test

```javascript
tbd;
```

#### Result

```Shell
tbd
```

## Reference

- [Top 85 JavaScript Interview Questions & Answers](https://www.guru99.com/javascript-interview-questions-answers.html)
- [TOP 45 JavaScript Interview Questions](https://www.softwaretestinghelp.com/javascript-interview-questions/)
- [Coderslang: Become a Software Engineer](https://learn.coderslang.com/tags/js-test)
- [coderslang](https://js.coderslang.com/lecture)
- [TypeScript Deep Dive](https://basarat.gitbook.io/typescript/getting-started)
- [Mocha.js, the JavaScript test framework: A tutorial](https://blog.logrocket.com/a-quick-and-complete-guide-to-mocha-testing-d0e0ea09f09d/)
- [4 Ways to Swap Variables in JavaScript](https://dmitripavlutin.com/swap-variables-javascript/)
