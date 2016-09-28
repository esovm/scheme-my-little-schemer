#The little schemer

> While a decent citizen rests his feets at home,
> a brave warrior stands at the battleground willing to learn some Lisp

## About

This repo tries to follow [the clojure style guide](https://github.com/bbatsov/clojure-style-guide).


```clojure
(def atom?
  (fn [x]
   (not (seq? x))))

(def null?
  (fn [x]
   (or
    (nil? x)
    (= '() x))))
```
### The First Commandment
The first commandment is about the use of a 'base case' when defining a recursion, which is basically:
> When recurring on an element ask whether it is null or not.

Example when the base case returns an empty list:

```clojure
(if (empty? lat)
  '()
  ...)
```

However the equivalence in clojure for sequences may be using `seq` and `when`:

```clojure
;If lat is not 'seq' then is an empty list;
;When the condition is false, 'when' returns
;'nil' which is equivalent to and empty string.

(when (seq lat) ...)
```

### The Second Commandment

> Use cons to build lists

Here it just point out the basic operation to build lists.

### The Third Commandment

> When building a list, describe the first typical element, and then cons it onto the natural recursion.

For example in the [rember](3_ConsTheMagnificent/rember.clj) function, in the recursion call we build the new list
using `cons`, also the head element for the list is the first element of lst:

```clojure
(cons (first lst) (rember a (rest lst)))
```

### The Fourth Commandment

>Always change at least one argument while recurring. It
>must be changed to be closer to termination. The changing
>argument must be tested in the termination condition:
>when using cdr, test termination with null?

For example when calling `(rest lst)` will eventually lead us to an empty list:
```clojure
(rember a (rest lst))
```

Find the book
[here](https://www.amazon.com/Little-Schemer-Daniel-P-Friedman/dp/0262560992/ref=sr_1_1?ie=UTF8&qid=1473739422&sr=8-1&keywords=little+schemer)

![cover](/img/readimg.jpg)
