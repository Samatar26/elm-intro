# elm-intro
Repository documenting learnings on Elm

Elm compiles to JavaScript. E.g. Babel compiles your ES6 JavaScript into browser-compatible ES3/5 JavaScript.


### Lesson 1 - Beginning Elm
Example of writing a function in JavaScript compared to Elm

### JavaScript function
```js
let pluralize = (singular, plural, quantity)=>{
  if ( quantity === 1 ) {
    return singular;
  } else {
    return plural;
  }
};
```

###Elm function
```js

pluralize singular plural quantity =
    if quantity == 1 then
        singular
    else
        plural

  ///Calling a function in Elm
  text (pluralize "leaf" "leaves" 1)
```

In Elm, the arguments go to the left of the equal sign and when you define a function it's as simple as the name of the function and any arguments seperated by white space.
In Elm, you don't need to put parentheses around your if statement and the double equal is equal to the triple equal in JavaScript. With Elm your if statement has to have a following else statement, _**it's required**_. This is because the if else statement is an expression. The if/else statement is more equal to the ternary operation in JavaScript. Calling a function in Elm, is done by calling the function's name followed by white space and your arguments, _**no commas between your arguments**_. The parentheses are used to disambiguate between your function calls. In the example above, we're passing the result of pluralize into text.
