<h1 align="center">Asynchronous JavaScript</h1>

As JavaScript is Asynchronous by default it does not wait 
to end task and continue reading.

```js
console.log('----------Start----------')

setTimeout(() => {
    console.log('Reading a database which takes 2sec');
}, 2000);

console.log('----------End----------');
```

This could be issue 

```js
console.log('----------Start----------');

const user = getUser(1);
console.log(user);

console.log('----------End----------');

function getUser(id) {
    setTimeout(() => {
        console.log('Reading a database which takes 2sec');
        return { id: id, gitHubUsername: 'mosh' };
    }, 2000);
}
```


To avoid this we use 
- Callbacks 
- Promises 
- Async/Await 

1. Callbacks

```js
console.log('----------Start----------');

getUser(1, (user) => {
    console.log('User Object from Database ',user);
});

console.log('----------End----------');

function getUser(id, callback) {
    setTimeout(() => {
        console.log('Reading a database which takes 2sec');
        callback({ id: id, gitHubUsername: 'mosh' });
    }, 2000);
}
```

But it can lead to Callback Hell issue.
As we have many nested function it's hard to read 
That's where Promises come under picture
