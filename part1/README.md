Part 1
======

## Installation

```bash
elm-package install
```

(Answer `y` when prompted.)


## Building

```bash
elm-live Main.elm --open --pushstate --output=elm.js
```

## References

* [**if-expressions**](http://elm-lang.org/docs/syntax#conditionals)
* [elm-html documentation](http://package.elm-lang.org/packages/elm-lang/html/latest)
* [html-to-elm](http://mbylstra.github.io/html-to-elm/) - paste in HTML, get elm-html code

When concatinating strings in Elm, you need to use two `+` signs, like so :
`"foo" ++ "bar"` which is equal to `"foobar"`

There are no methods in Elm, but there is a there is a tostring function, e.g.:
`toString 5 == "5"`

In our pluralize function, if we want to return the number of items, it can be done like this:

```elm
pluralize singular plural quantity =
  if quantity == 1 then
    toString quantity ++ " " ++ singular
  else
    toString quantity ++ " " ++ plural

```

Our code is a bit dry, so in order to refactor this we could use a let declared outside the statement like so:
```elm
pluralize singular plural quantity =
  let
      quantityStr =
            toString quantity

      prefix =
            quantityStr ++ " "
in

  if quantity == 1 then
    prefix ++ singular
  else
    prefix ++ plural

```

The entire expression above is a let-expression. ```quantityStr``` and ```prefix``` are inaccessible outside the scope of the let expression. You can't reassign the variables inside of a let expression, ```quantityStr``` and ```prefix``` are intermediary constants.


# Collections

### Records

```elm
record =
  { name = "thing", x = 1, y = 3}
```

They are similar to objects, one syntactic difference is that instead of creating key-value pairs with a `:`, you create them using an `=` sign.

Records have less features than objects, i.e. no concept of inheritance, no concept of methods, no concept of local state. They're just a flat immutable data structure that holds on to values.

Accessing stuff from records is similar to JavaScript objects:
E.g. `record.name == "thing"`

### Tuple
A tuple is shorthand for a record. If you don't want to name your fields, you can just put the data there without any further information.

```elm
tuple =
  ( "thing", 1, 3)

  -- typle destructuring
  ( name, x, y ) =
    ( "thing", 1, 3)

    name == "thing"
    x == 1
```

### Lists
All Lists must contain elements that share a common type. What's the benefits of this? It prevents NaN poisining. Let's say we loop through a list of elements and we have a mixture of elements of different types and we divide each element by 2, then if we encounter a string JavaScript will still return a value which is NaN and set up a wole host of debugging problems.

```elm
[ 1, 2, 3 ]
[[ "foo", "bar" ], [ "baz" ] ]

```

Records and tuples are fixed length, you can't dynamically add or remove elements from them.
