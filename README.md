# Javascript Functions

Functions are the main component of Javascript. It is so important that an entire chapter is devoted learning the intricacies of functions. Remember that functions are a block of code neatly packaged into a single unit.

## Defining a Functions

In the previous lesson we learned that you can define a function using the keyword `function`

for example: `function add(a, b) { return a + b }`

In Javascript you can also assign this function to a variable using the `var` keyword.

`var myAddFunc = function add(a, b) { return a + b }`

now you can invoke the add function using `myAddFunc(a, b);`

## Parameters and Scopes

we have been using parameters for a while now, but they are exactly like variables, but the important difference is that they are passed into the function rather than being created inside the function scope.

Scope is a very important topic,

When a function is created it creates it's own local environment and we define that as scope.

This means that variables that are defined inside of this scope is not available to the outside of this scope.

Lets go through some examples:

```
var x = 1;

var myInsideFunction = function() {
  // Notice that we have already used x above as a variable name

  var x = "5";
  console.log("I'm Inside", x);
}

myInsideFunction();
console.log("I'm Outside", x);

var changeOutSideVarFunc = function() {
  // we will grab the above scope x and change the value;
  x = 10;
}

// invoking the changeOutSideVarFunc will change the value of x from 5 to 10
changeOutSideVarFunc();
console.log("I'm Outside", x);

// However the x in the myInsideFunction will not be changed
myInsideFunction();
```

I would say that scopes are one of the main stumbling blocks for new programmers so please read through this example until it is crystal clear :)

## Nested Scopes

In Javascript you can also nest scopes as deep as you want.

```
function levelOne() {

  var canYouSeeMe = 'yes';

  function levelTwo() {
    console.log('levelTwo invokes me');
    function levelThree() {
      console.log('levelThree invokes me');

      console.log('i can see', canYouSeeMe);
    }
    levelThree();
  }
  console.log('levelOne invokes me');
  levelTwo();
}
levelOne();
```

Note that if you were to try and call the `levelTwo` function at the end of the code block, it would throw a undefined error because `levelTwo` is not in scope at that level.

However, if you were to try and access the variable `canYouSeeMe` from the `levelThree` function, you are able to do it.

This is because functions have access to variables and methods that the containing scopes have. This also propagates all the way up to the global scope.

## Declaration Notation

There is small caveat in Javascript when it comes to function declaration.

Lets take this example where I try to invoke a function that is defined at a later time in our code

```
willThisWork();

function willThisWork() {
  console.log("why does this work?");
}
```

This works because in Javascript functions declarations are not part of the regular top-to-bottom flow control instead they are hoisted up to the top of their scope.

Although this is possible I would advise against using this pattern. Instead make sure to try your best to declare you functions first and then invoke it at a later time.

## The Call Stack

I feel like the call stack is important enough to warrant its own section. For now I've linked a Youtube video that I believe is worth watching:

## Optional arguments

When you define a function with arguments, you are essentially creating a contract with the outside scope stating that this function takes X amount of arguments.

However, Javascript doesn't really care about your contract. In Javascript passing the correct amount of arguments is optional. If you pass in more arguments than the function takes, the function will simply assign the arguments as undefined and move on its merry way.

The upside to this odd behavior is that you can create default values for your arguments when no value is passed.

```
function rollDice(face = 6) {
  console.log(Math.floor(Math.random() * face) + 1)
}
```

The rollDice can now roll different face sided dices such as a D20, `rollDice(20);`,  but if you don't supply a argument it will just roll a D6 by default.

## Closure

Closure is a technique that is based on two interested behaviors of functions in Javascript

- functions can be values
- local variables are "re-created" every time a function is called

Let's see an example and go over it.

```
function mail(sender) {
  var name = sender;
  return function(recipient) {
    return recipient + ' received mail from ' + name
  }
}

var sendMailTo = mail('John');
var mailMsg = sendMailTo('Mike');
console.log(mailMsg);
```

There are few subtle things that you should notice from the example.

1. In the `mail` function we are returning a anonymous function that returns `recipient + ' received mail from ' + name`. Which is a string concatenating the `recipient` variable and the `name` variable.

2. when we assign the `sendMailTo` variable we invoke the `mail()` function, therefore, assigning the return value of `function(recipient) { return recipient + ' received mail from ' + name }` as the value;

3. This means that when we invoke assign `mailMsg` we are also invoking the `sendMailTo('Mike')` which holds a function as a value. Note we are also passing a string called `'Mike'` which the function will store as `recipient`

4. finally the end return value is a string: `Mike received mail from John`

The important concept here is that the variable `name` was accessible even after the `mail('John')` function was invoked during the assignment of `sendMailTo = mail('John')`. This is what closures are. It allows your to wrap local variables in a function to be used at another time outside of their scope.

This is a pretty long handed explanation of this, but closure is a very important topic that most beginning programs will not get the first time around.

## Recursion

Recursion is simply when a function calls itself. One thing to note is that in most cases problems you can solve with recursion you can also solve iteratively. However, both methods will have their trade offs. recursion usually offers elegant and also allows you to solve problems that require exploring or processing several branches. However, recursion is much more slower than it's counter part. e.a. loops.

//

## Growing Functions

## Functions and Side Effects

## Challenges

1. Variable Functions
2. My Scope Your Scope
3. Fibonacci
4. Refactor My Side Effect
