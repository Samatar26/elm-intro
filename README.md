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

### Lesson 2 - Why Bother?
In the JavaScript example above for the function pluralize, if we returned `singula` instead of `singular` our code would still reach the end user and is perfectly valid JS code and unless you invoke the function, there won't be any runtime error.
Whereas in Elm, the compiler gets run ahead of time, before the code's executed, before it reaches your _**your end user**__. Things therefore tend not to crash, you tend not to get runtime exceptions.  You can't compare something of a different type to something else of a different type, e.g. a number and a string. You should therefore bother with Elm because of reliability.

### Lesson 3 - HTML and the virtual DOM   

A single-line comment in Elm is a `--` and a multi-line comment is `{- this is a block comment - }`.
![dom](https://cloud.githubusercontent.com/assets/22747985/26787457/f51980a0-4a01-11e7-8d61-317f2ba7112c.png)
When you give the html to the browser, it translates to a DOM structure. We have a DOM node, the ul at the top and inside of it we have two child-nodes and inside of each of these we have text-nodes. Text-nodes don't have classes/attributes, etc.

In elm you would write the above HTML as so:
```js
ul [ class "highway"]
     [ li [] [text "danger"]
     , li [] [text "zone"]
     ]
```

Instead of writing HTML, we're using Elm function calls. Lists in Elm use square brackets. So we call ul, a function and pass in two arguments. The first argument is a list which contains the class highway. Class is another function btw, and we're passing in the string "highway". The second argument, the second list, has two more function calls. One to `li` and the other to another `li`. We're passing in a list of `text "danger"`. As you might have guessed text is another function and we're passing in "danger". In Elm, we tend to write commas at the front, not at the end.

Questions:
- Why are we passing in a list?
- What's the first argument in the `li` function call?

The first argument in li is for any attributes we want to add to the HTML element, since we don't want to add any it is empty.
