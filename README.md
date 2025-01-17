# alls (All Settled) - wait till all the promises are settled
[![License](https://img.shields.io/github/license/rpgeeganage/alls.svg)](https://github.com/rpgeeganage/alls)
[![Version](https://img.shields.io/npm/v/alls.svg)](https://img.shields.io/npm/v/alls.svg)
[![Language grade: JavaScript](https://img.shields.io/lgtm/grade/javascript/g/rpgeeganage/alls.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/rpgeeganage/alls/context:javascript)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/e8fc6d45ba07412a975fb823379cdbdf)](https://www.codacy.com/app/rpgeeganage/alls?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=rpgeeganage/alls&amp;utm_campaign=Badge_Grade)
[![Codacy Badge](https://api.codacy.com/project/badge/Coverage/e8fc6d45ba07412a975fb823379cdbdf)](https://www.codacy.com/app/rpgeeganage/alls?utm_source=github.com&utm_medium=referral&utm_content=rpgeeganage/alls&utm_campaign=Badge_Coverage)
[![Build Status](https://travis-ci.org/rpgeeganage/alls.svg?branch=master)](https://travis-ci.org/rpgeeganage/alls)
[![Known Vulnerabilities](https://snyk.io/test/github/rpgeeganage/alls/badge.svg?targetFile=package.json)](https://snyk.io/test/github/rpgeeganage/alls?targetFile=package.json)
[![Maintainability](https://api.codeclimate.com/v1/badges/66cd49a28da26d6f51f1/maintainability)](https://codeclimate.com/github/rpgeeganage/alls/maintainability)
### Just another library with the sole purpose of waiting till all the promises are fulfilled. Nothing more, Nothing less.

#### (The [```Promise.all()```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/all) method returns a single promise that resolves when all of the promises passed as an iterable have been resolved or when the iterable contains no promises. Also, it rejects with the reason of the first promise that rejects.)

### TypeScript Doc: [https://rpgeeganage.github.io/alls/doc/](https://rpgeeganage.github.io/alls/doc/)

### Basic Usage:
```js
const { alls } = require('alls');

const results = await alls([promise1, promise2, .....promiseN]);
// structure of results
[
  {
    status: 'fulfilled',
    value: promise1-value
  },
  {
    status: 'rejected',
    reason: error-from-promise2
  }
...
  {
    status: 'fulfilled',
    value: promiseN-value
  }
]
```

#### Return value for ```Resolve```
```js
{
    status: 'fulfilled',
    value: <promise return value>
}
```

#### Return value for ```Reject```
```js
{
    status: 'rejected',
    reason: <Error thrown by promise>
}
```

### final output

```js
const error1 = new Error('error 1');
const error2 = new Error('error 2');
const error3 = new Error('error 3');

const results = await alls([
  Promise.resolve(1),
  Promise.reject(error1),
  Promise.resolve(2),
  Promise.reject(error2),
  Promise.resolve(3),
  Promise.reject(error3)
]);

/**
* content of the 'result'
*/
[
  { state: 'fulfilled', value: 1 },
  { state: 'rejected', reason: error1 },
  { state: 'fulfilled', value: 2 },
  { state: 'rejected', reason: error2 },
  { state: 'fulfilled', value: 3 },
  { state: 'rejected', reason: error3 }
]
```
