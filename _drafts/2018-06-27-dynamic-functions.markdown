---
title:  "Dynamic Functions"
mathjax: true
toc: true
toc_sticky: true
---

## How Machines Learn

To understand how machine learning happens, we need to know about functions.
In mathematics, a **function** is just a rule that accepts certain **inputs**
and assigns to each one a unique **output**. If that sounds a bit vague, it's
because functions are very general objects. The inputs and outputs can be
anything we like and the rule can be whatever we like, as long as each input
gets one and only one output. In this way, a function is like a machine: it
doesn't have to think about what output to assign, because there's only the one
choice. 

### Example

Suppose we have a function \\( f \\) that accepts real numbers as inputs, and
in each case outputs a real number. We write this as 

\\[ f \colon \mathbb{R} \to \mathbb{R} \\]

Let's suppose that rule is

\\[ y = f(x) = x^2 \\]

This notation means that the output, a real number we're calling \\( y \\) is
obtained via the rule \\( f \\) from the input \\( x \\) by squaring the input.

By supplying different inputs, we get different outputs, but the *rule* \\( f
\\) is always the same.

\\[ f(2) = 2^2 = 4 \\]
\\[ f(3) = 3^2 = 9 \\]
\\[ f(0) = 0^2 = 0 \\]

## A Static Family

This ordinary type of function could be called a "static" function (not a real
term) because while the ouput varies, the rule itself never changes. Now let's
consider the family of functions

\\[ f_c(x) = x^2 + c \\]

This is not one function, but rather a set of infinitely many functions with a
similar form. The value \\( c \\) that distinguishes one member of this family
from another is called a **parameter**. 

One member of this family is \\( f_3 \\) which is the rule

\\[ f_3(x) = x^2 + 3 \\]

and so for example we'd have:

\\[ f_3(7) = 7^2 + 3 = 52 \\]

but \\( f_5 \\) or \\( f_1 \\) are different functions and they produce
different outputs when given the same input:

\\[ f_5(7) = 7^2 + 5 = 54 \\] 

All of the members of this family are individually "static" functions. 

## Dynamic Functions

Now suppose we make a new kind of function, a "dynamic" function (also not a
real term) that works as follows:

1. **(Initialize)** Ranomdly pick a value of \\( c \\) to start.
2. **(Data)** Using that member of the family, feed it an input.
3. **(Calculate Loss)** After each the value of \\[ L(x,y) = y - x \\] where
   \\( y \\) is the output of our function.
4. **(Update Parameters)** Subract \\( (0.1)(2x-1) \\) from the current value
   of \\( c \\) to get a new value.  Using this new parameter, repeat steps
   2--4 as many times as desired. 

Leaving aside for now where this set of steps comes from, notice that what we've
created is a function that always uses a rule of the form

\\[ f_c(x) = x^2 + c \\]

but the exact rule that gets applied depends on the inputs that are fed into
the function. It even depends on the *ordering* in which the inputs are
suppplied, since this will cause updates to the parameter, which will change
the rule, which changes what is done with next input, and so on. 

### Example

Suppose we initialize \\( c=1 \\) and feed in the **training** data 

\\[ T = (10, 12, 9, 14, 11) \\]

Then at each step the output, loss, and new parameter value is given in the
table below:

| input \\(x\\) | parameter \\(c\\) | output \\(y\\) | loss \\(L\\) | new parameter \\(c\\) |
|:-------------:|:-----------------:|:--------------:|:------------:|:---------------------:|
| 10            | 1                 | 101            | 91           | -0.9                  |
| 12            | -0.9              | 144.81         | 131.1        | -3.2                  |
| 9             | -3.2              | 77.8           | 68.8         | 
