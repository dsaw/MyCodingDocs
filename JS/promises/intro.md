## Promise

* A promise is an object that may produce a single value in the future. It can be in one of three states - fullfilled, rejected and pending.
* It is eagerly executed - starts of in pending state and will execute a *resolve* or *reject* function when either it is resolved or rejected.
* Eg: `const wait = (timeout) => new Promise((resolve,reject) => {setTimeout(resolve,timeout)}); wait(2000).then(() => {console.log("gergerg@@@!")}`
* `.then` method will take a resolve & rejected handler. It can return another promise also - composition and chaining is possible.

# Async/ Await

*  Async functions are instances of `AsyncFunction` that permit `await` statements in them. They allow more concise and 'synchronous' looking promise handling code to combat *Callback hell*.
* Eg: `const val = await somePromise();` - it will wait for the promise to resolve or reject with a value. The code will be suspended at the point and control returned to the caller of the `async` function. Once settled the value is set to val.
* Note - If the awaited promise rejects, then an error is thrown **after** which the rejection value is set. So it can be handled in a try/catch like this.
```
try {
    const v = await someP();
} catch() {
    return 'error';
}
```
* `return val;` - anything returned in async function is resolved in a promise if not already one.

* Async functions are a programmatic combination of promises and generators released in the ES7 spec. 