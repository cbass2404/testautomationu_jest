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

3. In your root directory create a file named 'jsconfig.json' and add the following:

```json
{
    "typeAcquisition": {
        "include": ["jest"]
    }
}
```

4. In root directory run the following:

```
$ npm install @types/jest
```

5. Jest will test any file with a name.test.js or name.spec.js format.

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
        expect(multiply(3, 2)).toBeGreaterThan(5);
        expect(multiply(3, 2)).toBeLessThan(7);
        expect(multiply(3, 2)).toBeLessThanOrEqual(6);
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

## null values

---

```javascript
test('null', () => {
    const n = null;
    expect(n).toBeNull();
    expect(n).toBeDefined();
    expect(n).not.toBeUndefined();
    expect(n).not.toBeTruthy();
    expect(n).toBeFalsy();
});
```

## Arrays

---

```javascript
const carStock = ['BMW', 'Mercedes', 'Ferrari', 'Toyota'];

test('that the car stock list has a ferrari', () => {
    expect(carStock).toContain('Ferrari');
});
```

## Before and After // Setup and Teardown

---

-   beforeEach() && afterEach()
    -   Runs before/after each test

```javascript
const setupFirst = () => console.log('Setting up before tests run');
const tearDownNow = () => console.log('Finishing up after tests run');

describe('new account creation checks', () => {
    beforeEach(() => setupFirst());
    afterEach(() => tearDownNow());

    test('new account 1 created', () => {
        const account = 'account1';
        expect(account).toEqual('account1');
    });

    test('new account 2 created', () => {
        const account = 'account2';
        expect(account).toEqual('account2');
    });
});
```

-   beforeAll() && afterAll()
    -   runs before all tests run and after all tests finish

```javascript
const setup = () => console.log('Setting up before tests run');
const tearDown = () => console.log('Finishing up after tests run');

describe('new account creation checks', () => {
    beforeAll(() => setup());
    afterAll(() => tearDown());

    test('new account 1 created', () => {
        const account = 'account1';
        expect(account).toEqual('account1');
    });

    test('new account 2 created', () => {
        const account = 'account2';
        expect(account).toEqual('account2');
    });
});
```
