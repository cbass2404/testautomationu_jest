# Jest

What is Jest?

A facebook all inclusive framework for client and server side test automation. Open-sourced javascript library.

Why use Jest?

-   Ease of setup
-   Super fast execution
-   Does snapshots
-   All built in one (matchers, spies, runner & mocking library)

When to use Jest?

-   Unit testing
-   API Testing ( with other JS libraries like supertest, request-promise)
-   UI Testing ( with other JW libraries like puppeteer)
-   DB Testing ( against mongodb and dynamodb)

## Setting up the environment

---

1. In your main directory input the following into your terminal:

```
$ npm install --save-dev jest
```

2. In your package.json file add the following to your scripts section:

```json
 "scripts": {
    "test": "jest"
  }
```

3. Jest will test any file with a name.test.js or name.spec.js format.

# Functions

## toBe()

---

```javascript
//function
const multiply = (a, b) => {
    return a * b;
};

module.exports = multiply;
//test
const multiply = require('./multiply');

describe('test multiply positive scenarios', () => {
    test('multiply 3*2 should equal to 6', () => {
        expect(multiply(3, 2)).toBe(6);
    });
});
```

_toBe() is used when you are expected a value_

## not.toBe()

---

```javascript
describe('test multiply positive scenarios', () => {
    test('multiply 4*3 should not equal 11', () => {
        expect(multiply(4, 3)).not.toBe(11);
    });
});
```

## Common Matchers

---

```javascript
test('object example', () => {
    const data = { first: 1 };
    data['second'] = 2;
    expect(data).toEqual({ first: 1, second: 2 });
});
```

_toEqual is used for value checking_

## toMatch

---

```javascript
test('there is pool in liverpool', () => {
    expect('Liverpool').toMatch(/pool/);
});
```

_checks if a value includes the match argument_
