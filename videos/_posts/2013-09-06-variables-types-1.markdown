---
layout: post
title: "Video: Variables & types 1"
---

# Video: Variables & types 1

Notes for this video are found below.

<div style="text-align: center">
<iframe src="http://player.vimeo.com/video/58274935?title=0&amp;byline=0&amp;portrait=0&amp;color=ffffff" width="800" height="600" frameborder="0" webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe>
</div>

## Types

- `int` for integers (..., -2, -1, 0, 1, 2, ...)

- `float` for "floating point" values (i.e. decimal values like -0.5 or 1.23040E-23)

- `char` for single characters/symbols (e.g., `'x'`).

- `string` for "strings" (e.g., `"Hello, Bob!"`).

- `boolean` for true/false values

## Variable naming

Here are the rules for naming variables:

- 1 to 255 characters

- must begin with a letter or _

- after the first letter or _, can contain numbers

- uppercase and lowercase letters are considered different (e.g. xyz is not the same variable as Xyz)

- "reserved" words cannot be used (e.g. "void" "if" etc.)

## Arithmetic

- Here are the normal math operators that work on integers and floating point numbers:

- `+` (add)

- `-` (subtract; or a negative number, e.g. `int x = -5`)

- `*` (multiply)

Here are somewhat-unique math operators that work with integers:

- `/` (quotient: `13 / 5` is 2 because 5 goes into 13 two times)

- `%` (remainder: `13 % 5` is 3 because the remainder of 5/13 is 2)

Note that `/` works as you would expect with floating point numbers
(e.g. `1.2 / 5.6` is about 0.214).

Precedence works the same as you would expect: `* / %` happen before
`+ -` so `(5 + 6 % 4 - (3 + 4) / 2)` equals 4 as you would expect. You
can use parentheses to clarify the math.

## Arithmetic shorthand

You can use the following shorthand for changing the values of
variables. The shorthand form is shown, then the equivalent form is
described in comments.

{% highlight java %}
float a = 0.0;
int x = 0;
x++;            // same as: x = x + 1;
x--;            // same as: x = x - 1;
x += 2;         // same as: x = x + 2;
x -= 2;         // same as: x = x - 2;
x *= 2;         // same as: x = x * 2;
x /= 2;         // same as: x = x / 2;
    
a += 2.0;       // same as: a = a + 2.0;
// etc.
{% endhighlight %}

## Boolean operators

Variables of type `boolean` have the following special operators:

{% highlight java %}
boolean p = true;
boolean q = false;
boolean r;
r = !p;        // "!" means "not" or "opposite", so r == false
r = p || q;    // "||" means "or", so r == true
r = p && q;    // "&&" means "and", so r == false
r = q || (!p)  // r == false
{% endhighlight %}

## Math functions

- `pow(a, b)` --- raise `a` to the power `b`; `a` and `b` should have type `float`
- `exp(a)` --- raise Euler’s number e to the power `a` (a float)
- `log(a)` --- find the natural logarithm of `a` (a float)
- `sqrt(a)` --- find the square root of `a` (a float)
- `sin(a)` --- the result of sine(a) (a is a float, in radians)
- `cos(a)`, `tan(a)` --- obvious

