How's it going guys, welcome to another Soul Encoded Tutorial.

Today we are going to go over Closures and Recursion in Javascript.
Let's do this!

[INTRO]

Last tutorial we left off talking about the various aspects of functions. I hope you guys
were able to complete the challenges and you're ready to learn about Closures and Recursion.

Now remember that Closures and Recursions are one of the most commonly miss understood topics

But don't worry we will break it down and hopefully it will be very straight forward after this tutorial.

Alright first lets dive into Closures

In the simplest form, closure is just when you wrap a function around another function. However there are few interesting things that happen when you do this.

I think for closures Kyle Simpson explained it the best. Kyle is the author of `You Don't Know Js`
it's one of the most popular javascript books series out there. I'll link it here

He states that "Closure is when a function is able to remember and access its
lexical scope even when that function is executing outside its lexical scope."

Yes I know it is a mouthful but it is a very complete explanation in my opinion.

so what is lexical scope?

Basically if you create a function it creates a parent scope. all the variables inside of the local scope is considered to be its lexical scope

example time.

```
var summation = function(total) {

  // the following function is returned
  // and assigned to adder
  var innerFunction = function(value) {
    total += value;
    console.log(total);
  }

  return innerFunction;

}(0); // we call the anonymous function
      // and assign the returned function to adder

var adder = summation(0);
adder(2); // 2
adder(3); // 5
```

Lets also briefly talk about IFFE immediately invoked function expression. in the above example summation was invoked and the return value assigned to adder. But you can also just invoke the function expression at the same time you are declaring it by adding the invoke parentheses after it.

IFFEs are very cool and handy. Hint you can use IFFEs for the first challenge of this section.

Alrighty moving on to the next section.

Recursion. I think the concept of recursion is pretty simple to understand. especially if you have a strong math background. All recursion is when a function calls itself over and over again until it meets a base condition to stop the recursion.

```
function factorial(n) {
  if (n === 1) {
    return 1;
  }
  return n * factorial(n - 1);
}

console.log(factorial(5));
```

Understanding the concept of recursion is pretty straight forward, but the solving problems with recursion is a lot harder in the beginning.

There are a few tricks though.

1. think about the base case first.
2. think about how to solve the problem for one recursive layer.

I will have a entire series where I solve different recursive problems as I believe practice makes perfect.

Hackerrank
