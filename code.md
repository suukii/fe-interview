# 编程题

- [编程题](#编程题)
  - [JavaScript](#javascript)
      - [实现一个 `useRetryable` 方法](#实现一个-useretryable-方法)
      - [实现一个日期格式化函数](#实现一个日期格式化函数)
      - [实现一个批量请求函数](#实现一个批量请求函数)

## JavaScript

<hr />

> 以下是各处整理的编程题面试题，没有固定来源。代码都是我自己写的，发现问题欢迎提 issue 哈。

<hr />

#### 实现一个 `useRetryable` 方法

> 来源：掘金上看到的

题目描述：

```js
function useRetryable(fn, times) {}

const retryableFn = useRetryable(fn, 3);

/**
 * 当调用 retryableFn 时，它的调用方式要与原始函数 (即 fn) 保持一致。同时还具备重试功能：
 * 1. 如果 n 次内执行失败，进行重试；
 * 2. 一旦执行成功，就不再执行多余的次数了；
 * 3. 如果 n 次全部失败，抛出最后一次的异常。
 */
```

同步递归版：

```js
function useRetryable(fn, times) {
    return function retryableFn(...arg) {
        try {
            return fn(...arg);
        } catch (error) {
            if (--times === 0) throw error;
            else return retryableFn(...arg);
        }
    };
}
```

同步循环版：

```js
function useRetryable(fn, times) {
    return function (...arg) {
        let res = null;

        while (times-- > 0) {
            res = callFnWithErrorHandling(fn, arg);
            if (res.status) return res.result;
        }

        throw res.error;
    };

    // *************************************

    function callFnWithErrorHandling(fn, arg) {
        try {
            return {
                result: fn(...arg),
                status: true,
            };
        } catch (error) {
            return {
                error,
                status: false,
            };
        }
    }
}

// test code
let count = 3;
const testFunc = function () {
    if (count > 0) {
        count--;
        throw Error('this is an error');
    } else return 'yeah~~suukii';
};

const fn = useRetryable(testFunc, 4);
console.log(fn());
```

异步版本(递归)：

```js
function useRetryableAsync(fn, times) {
    return function retryableFn(...arg) {
        times--;
        return fn(...arg)
            .then(data => data)
            .catch(error => {
                if (times === 0) throw error;
                // notes: 要把递归的结果 return 呀
                else return retryableFn(...arg);
            });
    };
}

// test code
let count = 3;
const testFunc = function () {
    return new Promise((res, rej) => {
        setTimeout(() => {
            count > 0 ? rej('this is an error') : res('yeah~~suukii');
            count--;
        }, 100);
    });
};

const fn = useRetryableAsync(testFunc, 4);
fn()
    .then(data => {
        console.log(data);
    })
    .catch(err => {
        console.log(err);
    });
```

#### 实现一个日期格式化函数

> 来源：虾皮校招一面

题目描述：

```js
/**
 * 输入：
 * dateFormat(new Date('2020-12-01'), 'yyy/MM/dd') // 2020/12/01
 * dateFormat(new Date('2020-04-01'), 'yyyy/MM/dd') // 2020/04/01
 * dateFormat(new Date('2020-04-01'), 'M/d/yyyy') // 4/1/2020
 * dateFormat(new Date('2020-04-01'), 'yyyy年MM月dd日') // 2020年04月01日
 */
const dateFormat = (date, reg) => {
    // code here
};
```

参考代码：

```js
const dateFormat = (date, reg) => {
    const o = {
        y: String(date.getFullYear()),
        M: String(date.getMonth() + 1),
        d: String(date.getDate()),
    };

    return reg.replace(/([yMd])+/g, ($1, key) =>
        o[key].padStart($1.length, '0').slice(-$1.length),
    );
};
```

#### 实现一个批量请求函数

> 来源：技术群里看到的面试题

题目描述：

```js
/**
 * 最大并发数 max
 * 每当有一个请求返回，就留下一个空位，可以增加新的请求
 * 所有请求完成之后，按照 urls 的顺序依次打印结果
 * @param {array} urls
 * @param {number} max
 */
const multipleRequest = (urls = [], max = 0) => {};
```

参考代码：

```js
/**
 * 最大并发数 max
 * 每当有一个请求返回，就留下一个空位，可以增加新的请求
 * 所有请求完成之后，按照 urls 的顺序依次打印结果
 * @param {array} urls
 * @param {number} max
 */
const multipleRequest = (urls = [], max = 0) => {
    return new Promise(resolve => {
        const len = urls.length;
        if (len === 0) resolve([]);

        const results = Array(len);

        let cur = 0; // 记录当前请求 url 的下标
        let fullfilled = 0; // 记录已经完成的请求数

        // 先并发请求 max 个 url
        while (cur < max && cur < len) {
            next(cur++);
        }

        // *********************************

        function next(index) {
            testFetch(urls[index])
                .then(data => {
                    results[index] = data;
                })
                .catch(err => {
                    results[index] = err;
                })
                .finally(() => {
                    // 完成一个请求后，进行下一个 url 请求
                    if (cur <= len - 1) next(cur++);

                    // 所有请求都 fullfilled 了，返回结果
                    if (++fullfilled === len) resolve(results);
                });
        }
    });
};

// ***********************************
// test code

/**
 * 模拟网络请求
 * @param url
 */
const testFetch = url => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (Math.random() > 0.5) {
                resolve(`success-${url}`);
            } else {
                reject(`error-${url}`);
            }
        }, Math.random() * 100);
    });
};

multipleRequest(
    Array(200)
        .fill(0)
        .map((n, i) => i),
    3,
).then(data => {
    console.log(data.every((s, i) => s.match(/\d+/)[0] == i));
    // console.log(data);
});
```
