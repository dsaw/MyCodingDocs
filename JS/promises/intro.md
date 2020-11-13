## Promise

* A promise is an object that may produce a single value in the future. It can be in one of three states - fullfilled, rejected and pending.
* It is eagerly executed - starts of in pending state and will execute a *resolve* or *reject* function when either it is resolved or rejected.
* Eg: `const wait = (timeout) => new Promise((resolve,reject) => {setTimeout(resolve,timeout)}); wait(2000).then(() => {console.log("gergerg@@@!")}`
* `.then` method will take a resolve & rejected handler. It can return another promise also - composition and chaining is possible.

