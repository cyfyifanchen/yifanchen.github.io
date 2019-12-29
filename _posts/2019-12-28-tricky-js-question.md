---
title: "Tricky JS Question"
layout: post
date: 2019-12-28
tag:
- dev
blog: true
star: false
---

<span class='fl'>S</span>aw this JavaScript interview question, it seems quite straightforward at the beginning, but it gets quite tricky along the way. Here is the question:

```javascript
/*
  1. Convert the following code to ES6 syntax
  2. Return the value after 2 seconds
*/
var john = {
  name: "John Doe",
  balance: 1500,
  deduct: function(amount){
    this.balance = this.balance - amount
    return this.name + ' has a balance of ' + this.amount
  }
}

console.log(john.deduct(200)) // John Doe has a balance of 1300
```
By looking at the question, on the last line of code, it should log out `John Doe has a blance of 1300`. Now let's go ahead to rewrite it with ES6 syntax.

### 1. Convert to ES6

```javascript
const john = {
  name: 'John Doe',
  balance: 1500,
  deduct: amount => {
    this.balance = this.balance - amount
    return this.name + ' has balance of ' + this.amount
  }
}

console.log(john.deduct(200))
```

Now, if we run the code, what we got, assuming without any linters, from the console would be `undefined has a balance of NaN`. Note we changed the `function` keyword to `=>` syntax on line 4(I wish Markdown has line number feature :cry:), and it's not working as expected. What caused this? :thinking: Becuase when using `=>` function, it created a lexcial scope, thus, keyword `this` is only referring to the inner scope, and the values, which we needed, were only avilable in the outer scope.

`this` is a tricky JavaScript concpet, let's take a look at what MDN has to say:
<div class="message">
  In most cases, the value of this is determined by how a function is called (runtime binding). It can't be set by assignment during execution, and it may be different each time the function is called. ES5 introduced the bind() method to set the value of a function's this regardless of how it's called, and ES2015 introduced arrow functions which don't provide their own this binding (it retains the this value of the enclosing lexical context).
</div>

So, to make it work, we have to use `this` to refer its value from outer scope, we can do it by eliminate `=>`, and short the line of code like follow:

```javascript
const john = {
  name: 'John Doe',
  balance: 1500,
  deduct(amount) {
    this.balance = this.balance - amount
    return `${this.name} has a balance of ${this.balance}`
  }
}

console.log(john.deduct(200))
```

Question 1 solved. Let's look at the second question.

### 2. Return the value after 2s

I could simply wrap the entire `console.log` into a `setTimeout` function, that, however, is probabbly not what an interviewer wants to hear.

```javascript
const john = {
  name: 'John Doe',
  balance: 1500,
  deduct(amount) {
    this.balance = this.balance - amount
    return `${this.name} has a balance of ${this.balance}`
  }
}

setTimeout(() => {
  console.log(john.deduct(200))
}, 2000)
```

What if I move the `setTimeout` function inside the `deduct` function?

```javascript
const john = {
  name: 'John Doe',
  balance: 1500,
  deduct(amount) {
    setTimeout(() => {
      this.balance = this.balance - amount
      return `${this.name} has a balance of ${this.balance}`
    })
  }
}

console.log(john.deduct(200))
```

Now, the console says `undefined`. I am now pretty sure this is what the interviewer wants to see. Why it's showing `undefined` then? :thinking: Becuase the `return` statement on line 7 is returning the value of the `setTimeout` function not the `deduct` function. By understanding this, we shall move the `return` statement outside of the `setTimeout` function.

Let's take a look at the MDN `return` statment description:
<div class="message">
  The return statement ends function execution and specifies a value to be returned to the function caller.
</div>

To make it happen, we could move `return` statement outside of setTimeout function and have it `return` a new `Promise`:

```javascript
const john = {
  name: 'John Doe',
  balance: 1500,
  deduct(amount) {
    return new Promise((res) => {
      setTimeout(() => {
        this.balance = this.balance - amount
        res(`${this.name} has a balance of ${this.balance}`)
      })
    })
  }
}

john.deduct(200).then(message => console.log(message))
```

Let's push the code a bit further, regardless the `sleep` function, the `john{}` itself is a lot more readable comparing the code above. And the `sleep` function just takes a `time` as an argument, and return a `Promise` which resloves on `setTimeout`. Addtionally, sleep function can be a misc function that seperated out from this file, that makes this code file even cleaner.

```javascript
const sleep = time => new Promise(res => setTimeout(res, time))

const john = {
  name: 'John Doe',
  balance: 1500,
  async deduct(amount) {
    await sleep(2000)
    this.balance = this.balance - amount
    return `${this.name} has a balance of ${this.balance}`
  }
}

john.deduct(200).then(console.log)
```

### Conclusion

Have a solid understanding of lexcial scope, `this` keyword and `Promises` are quite curcial.