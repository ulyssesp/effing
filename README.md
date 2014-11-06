[![Build Status](https://travis-ci.org/ianthehenry/effing.svg)](https://travis-ci.org/ianthehenry/effing)

# effing.js

Some handy function functions for JavaScript, minus the docs and examples and such.

# Functionoids

The following things are coerced into functions by effing.js:

- `null` becomes a no-op function
- `undefined` becomes a no-op function
- `[fn, args...]` returns a partially applied function
- `[context, method, args...]` returns a partially applied function with a bound context
- `[context, 'methodName', args...]` looks up the function on the context and returns it bound to the context with partially applied arguments

Anywhere effing.js expects a function argument, it will be happy with a functionoid instead.

# Curried binary operators

In Haskell you can say:

    isMinor = (< 18)

In f'ing JavaScript, you have to say:

    var isMinor = f.lt(18);

This is important: the relational operators all curry backwards. This means that `f.lt(foo)` is the same as `function(x) { return x < foo; }`, not `function(x) { foo < x; }`.

This *tends* to be a lot more useful, and hopefully is expected.

    var isEven = f.comp(f.eq(0), f.mod(2));

This isn't implemented even a little bit yet.
